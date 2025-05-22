# https://qwik.dev/docs/integrations/turso/

[Original link](https://qwik.dev/docs/integrations/turso/)

# Turso

Turso is the edge database based on libSQL - the open-source
open-contribution fork of SQLite.

It enables you to place your data close to your users in over 35 locations
around the world.

## Usage

You can easily add Turso by using the following Qwik starter script:

```
pnpm run qwik add turso
```

```
npm run qwik add turso
```

```
yarn run qwik add turso
```

```
bun run qwik add turso
```

This command will add the necessary dependencies to use Turso.

It also adds new files inside your project folder:

and adds or modifies a .env.local file to include

```
PRIVATE_TURSO_DATABASE_URL=
PRIVATE_TURSO_AUTH_TOKEN=
```

## Using file databases

For local development and CI integration, it is ideal to use local database files.

First, check if SQLite is installed in your machine by running sqlite3 --version. If you get anything other than a version number (e.g 0-14 20:58:05 554764a6e721fab307c63a4f98cd958c8428a5d9d8edfde951858d6fd02daapl), visit this
link for installation instructions.

Proceed to create an SQLite file database by running the following command.

```
sqlite3 foo.db
```

Create your database schema.

```
sqlite> create table todo (id integer not null, task text, done int default 0);
```

Seed some data into your table.

```
sqlite> insert into todo(id, task) values(1, "Go to the gym");
sqlite> insert into todo(id, task) values(2, "Buy groceries");
```

Quit the shell .quit

Then, assign the database file path to the PRIVATE_TURSO_DATABASE_URL environment variable
inside .env.local.

```
PRIVATE_TURSO_DATABASE_URL=file:foo.db
```

Note: A database token is not needed when working with file databases and createClient must be imported from @libsql/client since importing from @libsql/client/web does not support local file URLs.

## Using a Turso database

When you want to deploy your project to production, you can then install the
Turso CLI to your machine and create a Turso database.

Use the Turso CLI's db shell command to issue queries to your database.

```
turso db shell <database-name>
```

Create your database schema.

```
→  create table todo (id integer not null, task text, done int default 0);
```

Seed some data into your table.

```
→  insert into todo(id, task) values(1, "Go to the gym");
→  insert into todo(id, task) values(2, "Buy groceries");
```

Quit the shell .quit

Use the following instructions to obtain your Turso database credentials and
assign them to the environment variables inside your deployment environment.

Starting with the database url, run the following command.

```
turso db show <database-name> --url
```

Copy the resulting URL and assign it to the PRIVATE_TURSO_DATABASE_URL environment variable.

And, for the database authentication token, run the command.

```
turso db tokens create <database-name>
```

Copy the resulting token and assign it to the PRIVATE_TURSO_AUTH_TOKEN environment
variable.

## How to use Turso inside Qwik

Import tursoClient inside your routes and initiate a database client instance
within Qwik's server-side APIs that expose the RequestEvent object, such as
routeLoader$(), routeAction$(), server$() and endpoint handlers such as
onGet, onPost, onRequest.

```
import { tursoClient } from "~/utils/turso";
 
export const useRouteLoader = routeLoader$(
  async (requestEvent: RequestEventBase) => {
    const client = tursoClient(requestEvent);
 
    const items = await client.execute("select * from table");
 
    return {
      items: items.rows,
    };
  }
);
```

For more information, please visit the Turso docs.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
