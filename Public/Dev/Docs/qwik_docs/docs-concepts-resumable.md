# https://qwik.dev/docs/concepts/resumable/

[Original link](https://qwik.dev/docs/concepts/resumable/)

# Resumable vs. Hydration

A key concept of Qwik applications is that they are resumable from a server-side-rendered state. The best way to explain resumability is to understand how the current generation of frameworks are replayable (hydration).

When an SSR/SSG application boots up on a client, it requires that the framework on the client restores three pieces of information:

Collectively, this is known as hydration. All current generations of frameworks require this step to make the application interactive.

Hydration is expensive for two reasons:

Qwik is different because it does not require hydration to resume an application on the client. Not requiring hydration is what makes the Qwik application startup instantaneous.

All other frameworks' hydration replays all the application logic on the client. Qwik instead pauses execution on the server, and resumes execution on the client.

## Introducing Resumability

Resumability is about pausing execution on the server and resuming execution on the client without having to replay and download all of the application logic.

A good mental model is that Qwik applications at any point of their lifecycle can be serialized and moved to a different VM instance (server to browser). There, the application simply resumes where the serialization stopped. No hydration is required. Hence, Qwik applications don't hydrate; they resume.

In order to achieve this, Qwik needs to solve the 3 problems (listeners, component tree, application state) in a way that is compatible with a no-code startup.

### Listeners

DOM without event listeners is just a static page; it is not an application. Today's standard for all sites is quite a high level of interactivity, so even the most static-looking sites are full of event listeners. These include menus, hovers, expanding details, or even full-on interactive apps.

Existing frameworks solve the event listener by downloading the components and executing their templates to collect event listeners that are then attached to the DOM. The current approach has these issues:

The above approach does not scale. As the application becomes more complicated, the amount of code needed to download eagerly and execute grows proportionally with the size of the application. This negatively impacts the application startup performance and hence the user experience.
In other frameworks, lazy-loading chunks of the application becomes a development task in itself that consumes time and effort. In Qwik, lazy-loading is a natural consequence of the resumable architecture.

Qwik solves the above issue by serializing the event listeners into DOM like so:

```
<button on:click="./chunk.js#handler_symbol">click me</button>
```

Qwik still needs to collect the listener information, but this step is done as part of the SSR/SSG. The results of SSR/SSG are then serialized into HTML so that the browser does not need to do anything to resume the execution. Notice that the on:click attribute contains all of the information to resume the application without doing anything eagerly.

### Component Trees

Frameworks work with component trees. To that end, frameworks need a complete understanding of the component trees to know which components need to be rerendered and when. If you look into the existing framework SSR/SSG output, the component boundary information has been destroyed. There is no way of knowing where component boundaries are by looking at the resulting HTML. To recreate this information, frameworks re-execute the component templates and memoize the component boundary location. Re-execution is what hydration is. Hydration is expensive as it requires both the download of component templates and their execution.

Qwik collects component boundary information as part of the SSR/SSG and then serializes that information into HTML. The result is that Qwik can:

### Application State

Existing frameworks usually have a way of serializing the application state into HTML so that the state can be restored as part of hydration. In this way, they are very similar to Qwik. However, Qwik has state management more tightly integrated into the lifecycle of the components. In practice, this means that component can be delay-loaded independently from the state of the component. This is not easily achievable in existing frameworks because component props are usually created by the parent component. This creates a chain reaction. In order to restore component X, its parents need to be restored as well. Qwik allows any component to be resumed without the parent component code being present.

#### Serialization

The simplest way to think about serialization is through JSON.stringify. However, JSON has several limitations. Qwik can overcome some limitations, but some can't be overcome, and they place limitations on what the developer can do. Understanding these limitations is important when building Qwik applications.

Limitations of JSON which Qwik solves:

Limitations of JSON that Qwik does not solve:

For cases where serialization is not possible, code should run on client only.

### Writing applications with serializability in mind

The resumability capability of the framework must extend to resumability of the application as well. This means that the framework must provide mechanisms for the developer to express components and entities of the application in a way which can be serialized and then resumed (without re-bootstrapping). This necessitates that the application is written with resumability constraints in mind. It is simply not possible for developers to continue to write applications in a heap-centric way and expect that a better framework can somehow make up for this sub-optimal approach.

Developers must write their applications in a DOM-centric way. This will require a change of behavior and retooling of web developers' skills. Frameworks need to provide guidance and APIs to make it easy for developers to write the applications in this way.

### Other benefits of resumability

The most obvious benefit of using resumability is for server-side-rendering. However, there are secondary benefits:

### Contributors

Thanks to all the contributors who have helped make this documentation better!
