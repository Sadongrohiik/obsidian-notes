# https://qwik.dev/docs/integrations/prisma/

[Original link](https://qwik.dev/docs/integrations/prisma/)

# Prisma

Prisma allows interaction with MongoDB or SQL databases in a fully type-safe manner.

With Prisma you define your DB schema in .prisma files, and their CLI automatically generates the DB migrations as well as the Typescript types.

Prisma can be used in Qwik with routeLoader$, routeAction$ and server$ functions. These are Qwik APIs to allow code to execute only on the server-side.

The easiest way to add Prisma to Qwik is using the Qwik CLI command. This will install the required dependencies and create a prisma folder with the Prisma schema and the migrations.

```
pnpm run qwik add prisma
```

```
npm run qwik add prisma
```

```
yarn run qwik add prisma
```

```
bun run qwik add prisma
```

Prisma makes it easy to use different databases such as Postgres, MySQL, SQLite and MongoDB.

## Listing all the users

We will use routeLoader$ to query all users in the DB, using prisma.user.findMany(), and returning the result.

```
import { component$ } from '@builder.io/qwik';
import { routeLoader$ } from '@builder.io/qwik-city';
import { PrismaClient } from '@prisma/client'
 
export const useGetUsers = routeLoader$(async () => {
  const prisma = new PrismaClient();
  // example read from SQLite
  const users = await prisma.user.findMany()
  return users;
});
 
export default component$(() => {
  const users = useGetUsers();
  return (
    <section>
      <h1>User's directory</h1>
      <ul>
        {users.value.map(user => (
          <li key={user.id}>
            <a href={`/users/${user.id}`}>{user.name} ({user.email})</a>
          </li>
        ))}
      </ul>
    </section>
  )
});
```

## Show user detail

We will use routeLoader$ to query specific users based on the userId URL param, using prisma.user.findUnique(), and returning the result.

```
import { component$ } from '@builder.io/qwik';
import { routeLoader$ } from '@builder.io/qwik-city';
import { PrismaClient } from '@prisma/client'
 
export const useGetUser = routeLoader$(async ({params, status}) => {
  const userId = parseInt(params['userId'], 10);
  const prisma = new PrismaClient();
  const user = await prisma.user.findUnique({where: {id: userId}});
  if (!user) {
    // Set the status to 404 if the user is not found
    status(404);
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
  )
});
```

## Adding a user

We will use routeAction$ and Form to create a progressive form to add a new user to the DB. We will use prisma.user.create() to create the user.

```
import { component$ } from '@builder.io/qwik';
import { routeAction$, zod$, z, Form } from '@builder.io/qwik-city';
import { PrismaClient } from '@prisma/client'
 
export const useCreateUser = routeAction$(async (data) => {
  const prisma = new PrismaClient();
  const user = await prisma.user.create({
    data,
  });
  return user;
}, zod$({
  name: z.string(),
  email: z.string().email(),
}));
 
export default component$(() => {
  const createUserAction = useCreateUser();
  return (
    <section>
      <h1>Create User</h1>
      <Form action={createUserAction}>
        <label>Name
          <input name="name" value={createUserAction.formData?.get('name')} />
        </label>
        <label>Email
          <input name="email" value={createUserAction.formData?.get('email')} />
        </label>
        <button type="submit">Create</button>
      </Form>
      {createUserAction.value && (
        <div>
          <h2>User created successfully!</h2>
        </div>
      )}
    </section>
  )
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
