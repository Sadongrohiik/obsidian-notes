# https://qwik.dev/docs/action/

[Original link](https://qwik.dev/docs/action/)

# routeAction$()

routeAction$() is used to define functions called actions that execute exclusively on the server, and only when explicitly called. Actions can have side effects such as writing to a database or sending an email, that cannot happen during client-side rendering. This makes them ideal for handling form submissions, performing operations with side effects, and then returning data back to the client/browser where it can be used to update the UI.

Actions can be declared using routeAction$() or globalAction$() exported from @builder.io/qwik-city.

```
import { component$ } from '@builder.io/qwik';
import { routeAction$, Form } from '@builder.io/qwik-city';
 
export const useAddUser = routeAction$(async (data, requestEvent) => {
  // This will only run on the server when the user submits the form (or when the action is called programmatically)
  const userID = await db.users.add({
    firstName: data.firstName,
    lastName: data.lastName,
  });
  return {
    success: true,
    userID,
  };
});
 
export default component$(() => {
  const action = useAddUser();
 
  return (
    <>
      <Form action={action}>
        <input name="firstName" />
        <input name="lastName" />
        <button type="submit">Add user</button>
      </Form>
      {action.value?.success && (
        // When the action is done successfully, the `action.value` property will contain the return value of the action
        <p>User {action.value.userID} added successfully</p>
      )}
    </>
  );
});
```

Since actions are not executed during rendering, they can have side effects such as writing to a database, or sending an email. An action only runs when called explicitly.

## Using actions with <Form/>

The best way to call an action is using the <Form/> component exported in @builder.io/qwik-city.

```
import { component$ } from '@builder.io/qwik';
import { routeAction$, Form } from '@builder.io/qwik-city';
 
export const useAddUser = routeAction$(async (user) => {
  const userID = await db.users.add(user);
  return {
    success: true,
    userID,
  };
});
 
export default component$(() => {
  const action = useAddUser();
  return (
    <Form action={action}>
      <input name="name" />
      <button type="submit">Add user</button>
      {action.value?.success && <p>User added successfully</p>}
    </Form>
  );
});
```

Under the hood, the <Form/> component uses a native HTML <form> element, so it will work without JavaScript.

When JS is enabled, the <Form/> component will intercept the form submission and trigger the action in SPA mode. Allowing for a full SPA experience.

This is to clarify that the server re-renders the whole page and re-executes everything, so if you have any routeLoader$ they will be executed too.

Complex forms can be created using dot notation.

## Using actions programmatically

Actions can also be triggered programmatically using the action.submit() method (i.e. you don't need a <Form/> component). However, you can trigger the action from a button click or any other event, just like you would do with a function.

```
import { component$ } from '@builder.io/qwik';
import { routeAction$ } from '@builder.io/qwik-city';
 
export const useAddUser = routeAction$(async (user) => {
  const userID = await db.users.add(user);
  return {
    success: true,
    userID,
  };
});
 
export default component$(() => {
  const action = useAddUser();
  return (
    <section>
      <button
        onClick$={async () => {
          const { value } = await action.submit({ name: 'John' });
          console.log(value);
        }}
      >
        Add user
      </button>
      {action.value?.success && <p>User added successfully</p>}
    </section>
  );
});
```

In the example above, the addUser action is triggered when the user clicks the button. The action.submit() method returns a Promise that resolves when the action is done.

### Uploading files

When using <Form> with a file input, the submission will be sent as a multipart/form-data request.

But when using actions programmatically, you can still upload files by passing a File object to the action.submit() method by creating a FormData object and appending the file to it.

```
import { component$ } from '@builder.io/qwik';
import { routeAction$ } from '@builder.io/qwik-city';
 
export const useUploadFile = routeAction$(async ({file}) => {
  // save the file somewhere...
  return {
    success: true,
  };
});
 
export default component$(() => {
  const action = useUploadFile();
  const fileUploadRef = useSignal<HTMLInputElement | undefined>();
  return (
    <section>
      <input type="file" ref={fileUploadRef}/>
      <button
        onClick$={async () => {
          
          const file = fileUploadRef.value?.files?.[0];
 
          if (file){
            const formData = new FormData();
            formData.append('file', file);
            const { value } = await action.submit(formData);
            console.log(value);
          }
        }}
      >
        Upload file
      </button>
      
    </section>
  );
});
```

## Actions with Event Handlers

The onSubmitCompleted$ event handler can be used after an action is successfully executed and returns some data. This is useful for performing tasks, such as resetting UI elements or updating the application state, once an action has been completed.

Here's an example of the onSubmitCompleted$ handler used to edit an item in a EditForm component of a todo app.

```
import { component$, type Signal, useSignal } from '@builder.io/qwik';
import { Form } from '@builder.io/qwik-city';
import { type ListItem, useEditFromListAction } from '../../routes/index';
 
export interface EditFormProps {
  item: listItem;
  editingIdSignal: Signal<string>;
}
 
const EditForm = component$(
  ({ item, editingIdSignal }: EditFormProps) => {
    const editAction = useEditFromListAction();
 
    return (
      <div>
        <Form
          action={editAction}
          onSubmitCompleted$={() => {
            editingIdSignal.value = '';
          }}
          spaReset
        >
          <input
            type="text"
            value={item.text}
            name="text"
            id={`edit-${item.id}`}
          />
          {/* Sends item.id with form data on submission. */}
          <input type="hidden" name="id" value={item.id} />
          <button type="submit">
            Submit
          </button>
        </Form>
 
        <div>
          <button onClick$={() => (editingIdSignal.value = '')}>
            Cancel
          </button>
        </div>
      </div>
    );
  }
);
 
export default EditForm;
```

In this example, onSubmitCompleted$ is used to reset the editingIdSignal value to an empty string once the form submission is completed successfully. This allows the application to update its state and return to the default view.

## Validation and type safety

Qwik comes with built-in support for Zod, a TypeScript-first schema validation that can be used directly with actions, using the zod$() function.

Actions + Zod allows to create type safe forms, where the data is validated server side before the action is executed.

```
import { component$ } from '@builder.io/qwik';
import { routeAction$, zod$, z, Form } from '@builder.io/qwik-city';
 
export const useAddUser = routeAction$(
  async (user) => {
    // The "user" is strongly typed: { firstName: string, lastName: string }
    const userID = await db.users.add({
      firstName: user.firstName,
      lastName: user.lastName,
    });
    return {
      success: true,
      userID,
    };
  },
  // Zod schema is used to validate that the FormData includes "firstName" and "lastName"
  zod$({
    firstName: z.string(),
    lastName: z.string(),
  })
);
 
export default component$(() => {
  const action = useAddUser();
  return (
    <>
      <Form action={action}>
        <input name="firstName" />
        <input name="lastName" />
 
        {action.value?.failed && <p>{action.value.fieldErrors?.firstName}</p>}
        <button type="submit">Add user</button>
      </Form>
      {action.value?.success && (
        <p>User {action.value.userID} added successfully</p>
      )}
    </>
  );
});
```

When submitting data to a routeAction(), the data is validated against the Zod schema. If the data is invalid, the action will put the validation error in the routeAction.value property.

Please refer to the Zod documentation for more information on how to use Zod schemas.

### Advanced event based validation

The constructor of zod$ can also take a function, as the first argument is zod itself, so you can use this directly to build the schema.
The second parameter is the RequestEvent to construct an event-based zod schema.
Especially in combination with refine and superRefine in zod, the only limit is your imagination.

```
export const useAddUser = routeAction$(
  async (user) => {
    // The "user" is still strongly typed, but firstname
    // is now optional: { firstName?: string | undefined, lastName: string }
    const userID = await db.users.add({
      firstName: user.firstName,
      lastName: user.lastName,
    });
    return {
      success: true,
      userID,
    };
  },
  // Zod schema is used to validate that the FormData includes "firstName" and "lastName"
  zod$((z, ev) => {
    // The first name is optional if the url contains the query parameter "firstname=optional"
    const firstName =
      ev.url.searchParams.get("firstname") === "optional"
        ? z.string().optional()
        : z.string().nonempty();
 
    return z.object({
      firstName,
      lastName: z.string(),
    });
  })
);
```

## HTTP request and response

routeAction$ and globalAction$ have access to the RequestEvent object which includes information about the current HTTP request and response.

This allows actions to access the request headers, cookies, url and environment variables within the routeAction$ function.

```
import { routeAction$ } from '@builder.io/qwik-city';
 
// The second argument of the action is the `RequestEvent` object
export const useProductRecommendations = routeAction$(
  async (_data, requestEvent) => {
    console.log('Request headers:', requestEvent.request.headers);
    console.log('Request cookies:', requestEvent.cookie);
    console.log('Request url:', requestEvent.url);
    console.log('Request params:', requestEvent.params);
    console.log('MY_ENV_VAR:', requestEvent.env.get('MY_ENV_VAR'));
  }
);
```

## Action Failures

In order to return non-success values, the action must use the fail() method.

```
import { routeAction$, zod$, z } from '@builder.io/qwik-city';
 
export const useAddUser = routeAction$(
  async (user, { fail }) => {
    // `user` is typed { name: string }
    const userID = await db.users.add(user);
    if (!userID) {
      return fail(500, {
        message: 'User could not be added',
      });
    }
    return {
      userID,
    };
  },
  zod$({
    name: z.string(),
  })
);
```

Failures are stored in the action.value property, just like the success value. However, the action.value.failed property is set to true when the action fails. Futhermore, failure messages can be found in the fieldErrors object according to properties defined in your Zod schema.

The fieldErrors become a dot notation object. See Complex forms for more information.

```
import { component$ } from '@builder.io/qwik';
import { Form } from '@builder.io/qwik-city';
 
export default component$(() => {
  const action = useAddUser();
  return (
    <Form action={action}>
      <input name="name" />
      <button type="submit">Add user</button>
      {action.value?.failed && <p>{action.value.fieldErrors.name}</p>}
      {action.value?.userID && <p>User added successfully</p>}
    </Form>
  );
});
```

Thanks to Typescript type discrimination, you can use the action.value.failed property to discriminate between success and failure.

## Previous form state

When an action is triggered, the previous state is stored in the action.formData property. This is useful to display a loading state while the action is running.

```
import { component$ } from '@builder.io/qwik';
import { routeAction$, Form, zod$, z } from '@builder.io/qwik-city';
 
export const useAddUser = routeAction$(async (user) => {
  // handle action...
});
 
export default component$(() => {
  const action = useAddUser();
  return (
    <Form action={action}>
      <input name="name" value={action.formData?.get('name')} />
      <button type="submit">Add user</button>
    </Form>
  );
});
```

The action.formData is especially useful for retaining user-filled form data even after a page refresh. This enables a seamless SPA experience, even with JS disabled.

## Route vs Global actions

Actions can be declared using the routeAction$() or globalAction$() exported from @builder.io/qwik-city, the only difference between the two is that routeAction$() is scoped to a route, while globalAction$() is globally available across the whole app.

It's recommended to start with routeAction$(). Use globalAction$() only when sharing an action across multiple routes, or if you wish to use the action in a component that is not a route.

### routeAction$()

routeAction$() can only be declared inside the src/routes folder, in a layout.tsx or index.tsx file, and they MUST be exported, just like a routeLoader$(). Since routeAction$()s are only accessible within the route it's declared, they are recommended when the action needs to access some user data, or it's a protected route. Think about it like a "private" action.

If you want to manage common reusable routeAction$() it is essential that this function is re-exported from within 'layout.tsx' or 'index.tsx file of the existing route otherwise it will not run or throw exception. For more information check this section.

```
import { routeAction$ } from '@builder.io/qwik-city';
 
export const useChangePassword = routeAction$((data) => {
  // ...
});
```

### globalAction$()

globalAction$() can be declared anywhere in the src folder. Since globalAction$() are globally available, they are recommended when the action needs to be shared across multiple routes, or when the action doesn't need to access any user data. For example, a useLogin action that logs in a user. Think about it like a "public" action.

```
import { globalAction$ } from '@builder.io/qwik-city';
 
export const useLogin = globalAction$((data) => {
  // ...
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
