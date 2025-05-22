# https://qwik.dev/docs/labs/devtools/

[Original link](https://qwik.dev/docs/labs/devtools/)

# 🧪 Devtools

Stage: prototyping

This will eventually become Devtools for your browser to better debug application. For now it is a collection of utilities to better understand the state of your application.

## qwik/json

Qwik serializes the state of the application into <script type="qwik/json"> tag. This allows you to inspect the state of the application by looking at the DOM. Unfortunately the format is not very human readable. These steps describe how to parse the JSON into a more readable format.

```
import("https://qwik.dev/devtools/json/");
```

Most of the resulting output should be self explanatory. But we provide few high level points here to get you oriented. (This is not meant to be a complete documentation of the output.)

The way to think about Qwik serialization is that Qwik wants to serialize minimal amount of information. For this reason it only serializes objects which are reachable from either QContext or from QRef. This means that if you have an object which is not reachable from either of these two, then it will not be serialized. This is a good thing, because it means that Qwik will not serialize the entire application state, but only the state which is reachable from the component which is being rendered.

The flip side is that if you see an object being serialized and you think it should not be you can trace it backwards to see why it is being serialized. For this purpose all objects include a __backRef property which points to the object which is causing any object to be retained. By tracing the objects references back to their roots (which should be QContext or QRef) we can determine because of which one a particular object is being serialized. Similarly we can see if we can refactor our code to prevent serialization of said object.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
