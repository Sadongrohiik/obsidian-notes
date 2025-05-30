# https://qwik.dev/docs/validator/

[Original link](https://qwik.dev/docs/validator/)

# Data Validators

Data validators in QwikCity are essential for validating request events and data for actions and loaders. These validations occur on the server-side before the execution of the associated action or loader. Similar to the zod$() function, Qwik provides a dedicated validator$() function for this purpose.

```
import {
  type RequestEvent,
  type RequestEventAction,
  routeAction$,
  validator$,
} from "@builder.io/qwik-city";
 
export const useAction = routeAction$(
  async (data, requestEvent: RequestEventAction) => {
    return { foo: "bar" };
  },
  validator$(async (ev: RequestEvent, data) => {
    if (ev.query.get("secret") === "123") {
      return { success: true };
    }
    return {
      success: false,
      error: {
        message: "secret is not correct",
      },
    };
  }),
);
```

When submitting a request to a routeAction(), the request event and data undergo validation against the defined validator. If the validation fails, the action will place the validation error in the routeAction.value property.

```
export default component$(() => {
  const action = useAction();
 
  // action value is undefined before submitting
  if (action.value) {
    if (action.value.failed) {
      // action failed if query string has no secret
      action.value satisfies { failed: true; message: string };
    } else {
      action.value satisfies { searchResult: string };
    }
  }
 
  return (
    <button onClick$={() => action.submit({ search: "foo" })}>Submit</button>
  );
});
```

## Multiple validators

Actions and loaders can have multiple validators, which are executed in reverse order. In the following example, validators execute in the order validator3 -> validator2 -> validator1.

```
const validator1 = validator$(/*...*/)
const validator2 = validator$(/*...*/)
const validator3 = validator$(/*...*/)
 
export const useAction = routeAction$(
  async (data, requestEvent: RequestEventAction) => {
    return { foo: "bar" };
  },
  validator1,
  validator2,
  validator3, // will be executed first
);
```

If validator3 has a data property in its success return object, this data will be passed to the next validator, validator2. If you don't want to override the original submitted data, avoid putting the data property in the success return object.

```
export const useAction = routeAction$(
  async (data, requestEvent: RequestEventAction) => {
    console.log(data); // { message: "hi, I am validator1" }
    return { foo: "bar" };
  },
  // validator1
  validator$((ev, data) => {
    console.log(data); // { message: "hi, I am validator2" }
    return {
      success: true,
      data: {
        message: "hi, I am validator1",
      },
    };
  }),
  // validator2
  validator$((ev, data) => {
    console.log(data); // { message: "hi, I am validator3" }
    return {
      success: true,
      data: {
        message: "hi, I am validator2",
      },
    };
  }),
  // validator3
  validator$((ev, data) => {
    console.log(data); // Your submitted data
    return {
      success: true,
      data: {
        message: "hi, I am validator3",
      },
    };
  }),
);
```

## Return object

Data validators expect specific properties in their return objects.

### Successful validation

The success property must be true for a successful validation.

```
interface Success {
  success: true;
  data?: any;
}
```

### Failed validation

```
interface Fail {
  success: false;
  error: Record<string, any>;
  status?: number;
}
```

Validator behaves like using the fail() method in the action or loader when it returns a failed object.

```
const status = 500;
const errorObject = { message: "123" };
 
export const useAction = routeAction$(
  async (_, { fail }) => {
    return fail(status, errorObject);
  },
  validator$(async () => {
    return {
      success: false,
      status,
      errorObject,
    };
  }),
);
```

## Use validator$() with zod$() together in actions

For actions, the typed data validator zod$() should be the second argument of routeAction$, followed by other data validators validator$()s.

```
export const useAction = routeAction$(
  async (data, requestEvent: RequestEventAction) => {
    return { foo: "bar" };
  },
  zod$(/*...*/),
  validator$(/*...*/),
  validator$(/*...*/),
);
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
