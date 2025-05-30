# https://qwik.dev/docs/integrations/drizzle/

[Original link](https://qwik.dev/docs/integrations/drizzle/)

# Drizzle

Drizzle ORM is a headless TypeScript ORM with a head 🐲

Using Drizzle you can define & manage database schemas in TypeScript, access your data in a SQL-like or relational way, and take advantage of opt in tools to push your developer experience through the roof 🤯

While also being usable in serverless environments

Drizzle can be used in Qwik with routeLoader$, routeAction$ and server$ functions. These are Qwik APIs to allow code to execute only on the server-side.

The easiest way to add Drizzle to Qwik is using the Qwik CLI command. This will install the required dependencies and create a db folder with the drizzle schema.

```
pnpm run qwik add drizzle
```

```
npm run qwik add drizzle
```

```
yarn run qwik add drizzle
```

```
bun run qwik add drizzle
```

Drizzle is an ORM that embraces SQL. Unlike other ORMs, it doesn't deviate from SQL, eliminating the double learning curve of SQL and the framework's API. If you know SQL, you can easily use Drizzle to its full potential.

## Listing all the users

We will use routeLoader$ to query all users in the DB, using db.query.users.findMany(), and returning the result.

```
import { component$ } from "@builder.io/qwik";
import { routeLoader$ } from "@builder.io/qwik-city";
import { drizzle } from "drizzle-orm/better-sqlite3";
import Database from "better-sqlite3";
import { schema } from "../../../drizzle/schema";
 
export const useGetUsers = routeLoader$(async () => {
  const sqlite = new Database("./drizzle/db/db.sqlite");
  const db = drizzle(sqlite, { schema });
  const users = await db.query.users.findMany();
  return users;
});
 
export default component$(() => {
  const users = useGetUsers();
  return (
    <section>
      <h1>User's directory</h1>
      <ul>
        {users.value.map((user) => (
          <li key={user.id}>
            <a href={`/users/${user.id}`}>
              {user.name} ({user.email})
            </a>
          </li>
        ))}
      </ul>
    </section>
  );
});
```

## Show user detail

We will use routeLoader$ to query specific users based on the userId URL param, using db.query.users.findFirst({ where: (users, { eq }) => eq(users.id, userId), }), and returning the result.

```
import { component$ } from "@builder.io/qwik";
import { routeLoader$ } from "@builder.io/qwik-city";
import { drizzle } from "drizzle-orm/better-sqlite3";
import Database from "better-sqlite3";
import { schema } from "../../../../drizzle/schema";
 
export const useGetUser = routeLoader$(async (requestEvent) => {
  const userId = parseInt(requestEvent.params["userId"], 10);
  const sqlite = new Database("./drizzle/db/db.sqlite");
  const db = drizzle(sqlite, { schema });
  const user = await db.query.users.findFirst({
    where: (users, { eq }) => eq(users.id, userId),
  });
  if (!user) {
    // Set the status to 404 if the user is not found
    requestEvent.status(404);
  }
  return user;
});
 
export default component$(() => {
  const user = useGetUser();
  return (
    <section>
      <h1>User detail</h1>
      {user.value ? (
        <>
          <p>Name: {user.value.name}</p>
          <p>Email: {user.value.email}</p>
        </>
      ) : (
        <p>User not found</p>
      )}
    </section>
  );
});
```

## Adding a user

We will use routeAction$ and Form to create a progressive form to add a new user to the DB. We will use db.insert(schema.users).values(data) to create the user.

```
import { component$ } from "@builder.io/qwik";
import { routeAction$, zod$, z, Form } from "@builder.io/qwik-city";
import { drizzle } from "drizzle-orm/better-sqlite3";
import Database from "better-sqlite3";
import { schema } from "../../../drizzle/schema";
export const useCreateUser = routeAction$(
  async (data) => {
    const sqlite = new Database("./drizzle/db/db.sqlite");
    const db = drizzle(sqlite, { schema });
    const user = await db.insert(schema.users).values(data);
    return user;
  },
  zod$({
    name: z.string(),
    email: z.string().email(),
  }),
);
 
export default component$(() => {
  const createUserAction = useCreateUser();
  return (
    <section>
      <h1>Create User</h1>
      <Form action={createUserAction}>
        <label>
          Name
          <input name="name" value={createUserAction.formData?.get("name")} />
        </label>
        <label>
          Email
          <input name="email" value={createUserAction.formData?.get("email")} />
        </label>
        <button type="submit">Create</button>
      </Form>
      {createUserAction.value && (
        <div>
          <h2>User created successfully!</h2>
        </div>
      )}
    </section>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
