# https://qwik.dev/api/qwik/

[Original link](https://qwik.dev/api/qwik/)

# API › @builder.io/qwik

## _qrlSync

This API is provided as an alpha preview for developers and may change based on feedback that we receive. Do not use this API in a production environment.

Extract function into a synchronously loadable QRL.

NOTE: Synchronous QRLs functions can't close over any variables, including exports.

```
_qrlSync: <TYPE extends Function>(fn: TYPE, serializedFn?: string) =>
  SyncQRL<TYPE>;
```

Parameter

Type

Description

fn

TYPE

Extracted function

serializedFn

string

(Optional) Serialized function in string form.

Returns:

SyncQRL<TYPE>

Edit this section

## "q:slot"

```
'q:slot'?: string;
```

## "xlink:actuate"

```
'xlink:actuate'?: string | undefined;
```

## "xlink:arcrole"

```
'xlink:arcrole'?: string | undefined;
```

## "xlink:href"

```
'xlink:href'?: string | undefined;
```

## "xlink:role"

```
'xlink:role'?: string | undefined;
```

## "xlink:show"

```
'xlink:show'?: string | undefined;
```

## "xlink:title"

```
'xlink:title'?: string | undefined;
```

## "xlink:type"

```
'xlink:type'?: string | undefined;
```

## "xml:base"

```
'xml:base'?: string | undefined;
```

## "xml:lang"

```
'xml:lang'?: string | undefined;
```

## "xml:space"

```
'xml:space'?: string | undefined;
```

## "xmlns:xlink"

```
'xmlns:xlink'?: string | undefined;
```

## $

Qwik Optimizer marker function.

Use $(...) to tell Qwik Optimizer to extract the expression in $(...) into a lazy-loadable resource referenced by QRL.

```
$: <T>(expression: T) => QRL<T>;
```

Parameter

Type

Description

expression

T

Expression which should be lazy loaded

Returns:

QRL<T>

Edit this section

## AnchorHTMLAttributes

```
export interface AnchorHTMLAttributes<T extends Element> extends Attrs<'a', T>
```

Extends: Attrs<'a', T>

Edit this section

## AreaHTMLAttributes

```
export interface AreaHTMLAttributes<T extends Element> extends Attrs<'area', T>
```

Extends: Attrs<'area', T>

Edit this section

## AriaAttributes

TS defines these with the React syntax which is not compatible with Qwik. E.g. ariaAtomic instead of aria-atomic.

```
export interface AriaAttributes
```

Property

Modifiers

Type

Description

"aria-activedescendant"?

string | undefined

(Optional) Identifies the currently active element when DOM focus is on a composite widget, textbox, group, or application.

"aria-atomic"?

Booleanish | undefined

(Optional) Indicates whether assistive technologies will present all, or only parts of, the changed region based on the change notifications defined by the aria-relevant attribute.

"aria-autocomplete"?

'none' | 'inline' | 'list' | 'both' | undefined

(Optional) Indicates whether inputting text could trigger display of one or more predictions of the user's intended value for an input and specifies how predictions would be presented if they are made.

"aria-busy"?

Booleanish | undefined

(Optional) Indicates an element is being modified and that assistive technologies MAY want to wait until the modifications are complete before exposing them to the user.

"aria-checked"?

boolean | 'false' | 'mixed' | 'true' | undefined

(Optional) Indicates the current "checked" state of checkboxes, radio buttons, and other widgets.

"aria-colcount"?

number | undefined

(Optional) Defines the total number of columns in a table, grid, or treegrid.

"aria-colindex"?

number | undefined

(Optional) Defines an element's column index or position with respect to the total number of columns within a table, grid, or treegrid.

"aria-colspan"?

number | undefined

(Optional) Defines the number of columns spanned by a cell or gridcell within a table, grid, or treegrid.

"aria-controls"?

string | undefined

(Optional) Identifies the element (or elements) whose contents or presence are controlled by the current element.

"aria-current"?

boolean | 'false' | 'true' | 'page' | 'step' | 'location' | 'date' | 'time' | undefined

(Optional) Indicates the element that represents the current item within a container or set of related elements.

"aria-describedby"?

string | undefined

(Optional) Identifies the element (or elements) that describes the object.

"aria-details"?

string | undefined

(Optional) Identifies the element that provides a detailed, extended description for the object.

"aria-disabled"?

Booleanish | undefined

(Optional) Indicates that the element is perceivable but disabled, so it is not editable or otherwise operable.

"aria-dropeffect"?

'none' | 'copy' | 'execute' | 'link' | 'move' | 'popup' | undefined

(Optional) Indicates what functions can be performed when a dragged object is released on the drop target.

"aria-errormessage"?

string | undefined

(Optional) Identifies the element that provides an error message for the object.

"aria-expanded"?

Booleanish | undefined

(Optional) Indicates whether the element, or another grouping element it controls, is currently expanded or collapsed.

"aria-flowto"?

string | undefined

(Optional) Identifies the next element (or elements) in an alternate reading order of content which, at the user's discretion, allows assistive technology to override the general default of reading in document source order.

"aria-grabbed"?

Booleanish | undefined

(Optional) Indicates an element's "grabbed" state in a drag-and-drop operation.

"aria-haspopup"?

boolean | 'false' | 'true' | 'menu' | 'listbox' | 'tree' | 'grid' | 'dialog' | undefined

(Optional) Indicates the availability and type of interactive popup element, such as menu or dialog, that can be triggered by an element.

"aria-hidden"?

Booleanish | undefined

(Optional) Indicates whether the element is exposed to an accessibility API.

"aria-invalid"?

boolean | 'false' | 'true' | 'grammar' | 'spelling' | undefined

(Optional) Indicates the entered value does not conform to the format expected by the application.

"aria-keyshortcuts"?

string | undefined

(Optional) Indicates keyboard shortcuts that an author has implemented to activate or give focus to an element.

"aria-label"?

string | undefined

(Optional) Defines a string value that labels the current element.

"aria-labelledby"?

string | undefined

(Optional) Identifies the element (or elements) that labels the current element.

"aria-level"?

number | undefined

(Optional) Defines the hierarchical level of an element within a structure.

"aria-live"?

'off' | 'assertive' | 'polite' | undefined

(Optional) Indicates that an element will be updated, and describes the types of updates the user agents, assistive technologies, and user can expect from the live region.

"aria-modal"?

Booleanish | undefined

(Optional) Indicates whether an element is modal when displayed.

"aria-multiline"?

Booleanish | undefined

(Optional) Indicates whether a text box accepts multiple lines of input or only a single line.

"aria-multiselectable"?

Booleanish | undefined

(Optional) Indicates that the user may select more than one item from the current selectable descendants.

"aria-orientation"?

'horizontal' | 'vertical' | undefined

(Optional) Indicates whether the element's orientation is horizontal, vertical, or unknown/ambiguous.

"aria-owns"?

string | undefined

(Optional) Identifies an element (or elements) in order to define a visual, functional, or contextual parent/child relationship between DOM elements where the DOM hierarchy cannot be used to represent the relationship.

"aria-placeholder"?

string | undefined

(Optional) Defines a short hint (a word or short phrase) intended to aid the user with data entry when the control has no value. A hint could be a sample value or a brief description of the expected format.

"aria-posinset"?

number | undefined

(Optional) Defines an element's number or position in the current set of listitems or treeitems. Not required if all elements in the set are present in the DOM.

"aria-pressed"?

boolean | 'false' | 'mixed' | 'true' | undefined

(Optional) Indicates the current "pressed" state of toggle buttons.

"aria-readonly"?

Booleanish | undefined

(Optional) Indicates that the element is not editable, but is otherwise operable.

"aria-relevant"?

'additions' | 'additions removals' | 'additions text' | 'all' | 'removals' | 'removals additions' | 'removals text' | 'text' | 'text additions' | 'text removals' | undefined

(Optional) Indicates what notifications the user agent will trigger when the accessibility tree within a live region is modified.

"aria-required"?

Booleanish | undefined

(Optional) Indicates that user input is required on the element before a form may be submitted.

"aria-roledescription"?

string | undefined

(Optional) Defines a human-readable, author-localized description for the role of an element.

"aria-rowcount"?

number | undefined

(Optional) Defines the total number of rows in a table, grid, or treegrid.

"aria-rowindex"?

number | undefined

(Optional) Defines an element's row index or position with respect to the total number of rows within a table, grid, or treegrid.

"aria-rowspan"?

number | undefined

(Optional) Defines the number of rows spanned by a cell or gridcell within a table, grid, or treegrid.

"aria-selected"?

Booleanish | undefined

(Optional) Indicates the current "selected" state of various widgets.

"aria-setsize"?

number | undefined

(Optional) Defines the number of items in the current set of listitems or treeitems. Not required if all elements in the set are present in the DOM.

"aria-sort"?

'none' | 'ascending' | 'descending' | 'other' | undefined

(Optional) Indicates if items in a table or grid are sorted in ascending or descending order.

"aria-valuemax"?

number | undefined

(Optional) Defines the maximum allowed value for a range widget.

"aria-valuemin"?

number | undefined

(Optional) Defines the minimum allowed value for a range widget.

"aria-valuenow"?

number | undefined

(Optional) Defines the current value for a range widget.

"aria-valuetext"?

string | undefined

(Optional) Defines the human readable text alternative of aria-valuenow for a range widget.

Edit this section

## AriaRole

```
export type AriaRole =
  | "alert"
  | "alertdialog"
  | "application"
  | "article"
  | "banner"
  | "button"
  | "cell"
  | "checkbox"
  | "columnheader"
  | "combobox"
  | "complementary"
  | "contentinfo"
  | "definition"
  | "dialog"
  | "directory"
  | "document"
  | "feed"
  | "figure"
  | "form"
  | "grid"
  | "gridcell"
  | "group"
  | "heading"
  | "img"
  | "link"
  | "list"
  | "listbox"
  | "listitem"
  | "log"
  | "main"
  | "marquee"
  | "math"
  | "menu"
  | "menubar"
  | "menuitem"
  | "menuitemcheckbox"
  | "menuitemradio"
  | "navigation"
  | "none"
  | "note"
  | "option"
  | "presentation"
  | "progressbar"
  | "radio"
  | "radiogroup"
  | "region"
  | "row"
  | "rowgroup"
  | "rowheader"
  | "scrollbar"
  | "search"
  | "searchbox"
  | "separator"
  | "slider"
  | "spinbutton"
  | "status"
  | "switch"
  | "tab"
  | "table"
  | "tablist"
  | "tabpanel"
  | "term"
  | "textbox"
  | "timer"
  | "toolbar"
  | "tooltip"
  | "tree"
  | "treegrid"
  | "treeitem"
  | (string & {});
```

Edit this section

## AudioHTMLAttributes

```
export interface AudioHTMLAttributes<T extends Element> extends Attrs<'audio', T>
```

Extends: Attrs<'audio', T>

Edit this section

## BaseHTMLAttributes

```
export interface BaseHTMLAttributes<T extends Element> extends Attrs<'base', T>
```

Extends: Attrs<'base', T>

Edit this section

## BlockquoteHTMLAttributes

```
export interface BlockquoteHTMLAttributes<T extends Element> extends Attrs<'blockquote', T>
```

Extends: Attrs<'blockquote', T>

Edit this section

## Booleanish

```
export type Booleanish = boolean | `${boolean}`;
```

Edit this section

## ButtonHTMLAttributes

```
export interface ButtonHTMLAttributes<T extends Element> extends Attrs<'button', T>
```

Extends: Attrs<'button', T>

Edit this section

## cache

```
cache(policyOrMilliseconds: number | 'immutable'): void;
```

Parameter

Type

Description

policyOrMilliseconds

number | 'immutable'

Returns:

void

## CanvasHTMLAttributes

```
export interface CanvasHTMLAttributes<T extends Element> extends Attrs<'canvas', T>
```

Extends: Attrs<'canvas', T>

Edit this section

## ClassList

A class list can be a string, a boolean, an array, or an object.

If it's an array, each item is a class list and they are all added.

If it's an object, then the keys are class name strings, and the values are booleans that determine if the class name string should be added or not.

```
export type ClassList =
  | string
  | undefined
  | null
  | false
  | Record<string, boolean | string | number | null | undefined>
  | ClassList[];
```

References: ClassList

Edit this section

## cleanup

```
cleanup(): void;
```

Returns:

void

## ColgroupHTMLAttributes

```
export interface ColgroupHTMLAttributes<T extends Element> extends Attrs<'colgroup', T>
```

Extends: Attrs<'colgroup', T>

Edit this section

## ColHTMLAttributes

```
export interface ColHTMLAttributes<T extends Element> extends Attrs<'col', T>
```

Extends: Attrs<'col', T>

Edit this section

## Component

Type representing the Qwik component.

Component is the type returned by invoking component$.

```
interface MyComponentProps {
  someProp: string;
}
const MyComponent: Component<MyComponentProps> = component$(
  (props: MyComponentProps) => {
    return <span>{props.someProp}</span>;
  },
);
```

```
export type Component<PROPS = unknown> = FunctionComponent<PublicProps<PROPS>>;
```

References: FunctionComponent, PublicProps

Edit this section

## component$

Declare a Qwik component that can be used to create UI.

Use component$ to declare a Qwik component. A Qwik component is a special kind of component that allows the Qwik framework to lazy load and execute the component independently of other Qwik components as well as lazy load the component's life-cycle hooks and event handlers.

Side note: You can also declare regular (standard JSX) components that will have standard synchronous behavior.

Qwik component is a facade that describes how the component should be used without forcing the implementation of the component to be eagerly loaded. A minimum Qwik definition consists of:

### Example

An example showing how to create a counter component:

```
export interface CounterProps {
  initialValue?: number;
  step?: number;
}
export const Counter = component$((props: CounterProps) => {
  const state = useStore({ count: props.initialValue || 0 });
  return (
    <div>
      <span>{state.count}</span>
      <button onClick$={() => (state.count += props.step || 1)}>+</button>
    </div>
  );
});
```

The above can then be used like so:

```
export const OtherComponent = component$(() => {
  return <Counter initialValue={100} />;
});
```

See also: component, useCleanup, onResume, onPause, useOn, useOnDocument, useOnWindow, useStyles

```
component$: <PROPS = unknown>(onMount: OnRenderFn<PROPS>) => Component<PROPS>;
```

Parameter

Type

Description

onMount

OnRenderFn<PROPS>

Returns:

Component<PROPS>

Edit this section

## ComponentBaseProps

```
export interface ComponentBaseProps
```

Property

Modifiers

Type

Description

"q:slot"?

string

(Optional)

key?

string | number | null | undefined

(Optional)

Edit this section

## componentQrl

Declare a Qwik component that can be used to create UI.

Use component$ to declare a Qwik component. A Qwik component is a special kind of component that allows the Qwik framework to lazy load and execute the component independently of other Qwik components as well as lazy load the component's life-cycle hooks and event handlers.

Side note: You can also declare regular (standard JSX) components that will have standard synchronous behavior.

Qwik component is a facade that describes how the component should be used without forcing the implementation of the component to be eagerly loaded. A minimum Qwik definition consists of:

### Example

An example showing how to create a counter component:

```
export interface CounterProps {
  initialValue?: number;
  step?: number;
}
export const Counter = component$((props: CounterProps) => {
  const state = useStore({ count: props.initialValue || 0 });
  return (
    <div>
      <span>{state.count}</span>
      <button onClick$={() => (state.count += props.step || 1)}>+</button>
    </div>
  );
});
```

The above can then be used like so:

```
export const OtherComponent = component$(() => {
  return <Counter initialValue={100} />;
});
```

See also: component, useCleanup, onResume, onPause, useOn, useOnDocument, useOnWindow, useStyles

```
componentQrl: <PROPS extends Record<any, any>>(
  componentQrl: QRL<OnRenderFn<PROPS>>,
) => Component<PROPS>;
```

Parameter

Type

Description

componentQrl

QRL<OnRenderFn<PROPS>>

Returns:

Component<PROPS>

Edit this section

## ComputedFn

```
export type ComputedFn<T> = () => T;
```

Edit this section

## ContextId

ContextId is a typesafe ID for your context.

Context is a way to pass stores to the child components without prop-drilling.

Use createContextId() to create a ContextId. A ContextId is just a serializable identifier for the context. It is not the context value itself. See useContextProvider() and useContext() for the values. Qwik needs a serializable ID for the context so that the it can track context providers and consumers in a way that survives resumability.

### Example

```
// Declare the Context type.
interface TodosStore {
  items: string[];
}
// Create a Context ID (no data is saved here.)
// You will use this ID to both create and retrieve the Context.
export const TodosContext = createContextId<TodosStore>("Todos");
 
// Example of providing context to child components.
export const App = component$(() => {
  useContextProvider(
    TodosContext,
    useStore<TodosStore>({
      items: ["Learn Qwik", "Build Qwik app", "Profit"],
    }),
  );
 
  return <Items />;
});
 
// Example of retrieving the context provided by a parent component.
export const Items = component$(() => {
  const todos = useContext(TodosContext);
  return (
    <ul>
      {todos.items.map((item) => (
        <li>{item}</li>
      ))}
    </ul>
  );
});
```

```
export interface ContextId<STATE>
```

Property

Modifiers

Type

Description

__brand_context_type__

readonly

STATE

Design-time property to store type information for the context.

id

readonly

string

A unique ID for the context.

Edit this section

## CorePlatform

Low-level API for platform abstraction.

Different platforms (browser, node, service workers) may have different ways of handling things such as requestAnimationFrame and imports. To make Qwik platform-independent Qwik uses the CorePlatform API to access the platform API.

CorePlatform also is responsible for importing symbols. The import map is different on the client (browser) then on the server. For this reason, the server has a manifest that is used to map symbols to javascript chunks. The manifest is encapsulated in CorePlatform, for this reason, the CorePlatform can't be global as there may be multiple applications running at server concurrently.

This is a low-level API and there should not be a need for you to access this.

```
export interface CorePlatform
```

Property

Modifiers

Type

Description

chunkForSymbol

(symbolName: string, chunk: string | null, parent?: string) => readonly [symbol: string, chunk: string] | undefined

Retrieve chunk name for the symbol.

When the application is running on the server the symbols may be imported from different files (as server build is typically a single javascript chunk.) For this reason, it is necessary to convert the chunks from server format to client (browser) format. This is done by looking up symbols (which are globally unique) in the manifest. (Manifest is the mapping of symbols to the client chunk names.)

importSymbol

(containerEl: Element | undefined, url: string | URL | undefined | null, symbol: string) => ValueOrPromise<any>

Retrieve a symbol value from QRL.

Qwik needs to lazy load data and closures. For this Qwik uses QRLs that are serializable references of resources that are needed. The QRLs contain all the information necessary to retrieve the reference using importSymbol.

Why not use import()? Because import() is relative to the current file, and the current file is always the Qwik framework. So QRLs have additional information that allows them to serialize imports relative to application base rather than the Qwik framework file.

isServer

boolean

True of running on the server platform.

nextTick

(fn: () => any) => Promise<any>

Perform operation on next tick.

raf

(fn: () => any) => Promise<any>

Perform operation on next request-animation-frame.

Edit this section

## CorrectedToggleEvent

This corrects the TS definition for ToggleEvent

```
export interface CorrectedToggleEvent extends Event
```

Extends: Event

Property

Modifiers

Type

Description

newState

readonly

'open' | 'closed'

prevState

readonly

'open' | 'closed'

Edit this section

## createComputed$

Warning: This API is now obsolete.

This is a technology preview

Returns read-only signal that updates when signals used in the ComputedFn change. Unlike useComputed$, this is not a hook and it always creates a new signal.

```
createComputed$: <T>(qrl: ComputedFn<T>) => Signal<Awaited<T>>;
```

Parameter

Type

Description

qrl

ComputedFn<T>

Returns:

Signal<Awaited<T>>

Edit this section

## createComputedQrl

```
createComputedQrl: <T>(qrl: QRL<ComputedFn<T>>) => Signal<Awaited<T>>;
```

Parameter

Type

Description

qrl

QRL<ComputedFn<T>>

Returns:

Signal<Awaited<T>>

Edit this section

## createContextId

Create a context ID to be used in your application. The name should be written with no spaces.

Context is a way to pass stores to the child components without prop-drilling.

Use createContextId() to create a ContextId. A ContextId is just a serializable identifier for the context. It is not the context value itself. See useContextProvider() and useContext() for the values. Qwik needs a serializable ID for the context so that the it can track context providers and consumers in a way that survives resumability.

### Example

```
// Declare the Context type.
interface TodosStore {
  items: string[];
}
// Create a Context ID (no data is saved here.)
// You will use this ID to both create and retrieve the Context.
export const TodosContext = createContextId<TodosStore>("Todos");
 
// Example of providing context to child components.
export const App = component$(() => {
  useContextProvider(
    TodosContext,
    useStore<TodosStore>({
      items: ["Learn Qwik", "Build Qwik app", "Profit"],
    }),
  );
 
  return <Items />;
});
 
// Example of retrieving the context provided by a parent component.
export const Items = component$(() => {
  const todos = useContext(TodosContext);
  return (
    <ul>
      {todos.items.map((item) => (
        <li>{item}</li>
      ))}
    </ul>
  );
});
```

```
createContextId: <STATE = unknown>(name: string) => ContextId<STATE>;
```

Parameter

Type

Description

name

string

The name of the context.

Returns:

ContextId<STATE>

Edit this section

## createSignal

Warning: This API is now obsolete.

This is a technology preview

Creates a signal.

If the initial state is a function, the function is invoked to calculate the actual initial state.

```
createSignal: UseSignal;
```

Edit this section

## CSSProperties

```
export interface CSSProperties extends CSS.Properties<string | number>, CSS.PropertiesHyphen<string | number>
```

Extends: CSS.Properties<string | number>, CSS.PropertiesHyphen<string | number>

Edit this section

## DataHTMLAttributes

```
export interface DataHTMLAttributes<T extends Element> extends Attrs<'data', T>
```

Extends: Attrs<'data', T>

Edit this section

## DelHTMLAttributes

```
export interface DelHTMLAttributes<T extends Element> extends Attrs<'del', T>
```

Extends: Attrs<'del', T>

Edit this section

## DetailsHTMLAttributes

```
export interface DetailsHTMLAttributes<T extends Element> extends Attrs<'details', T>
```

Extends: Attrs<'details', T>

Edit this section

## DevJSX

```
export interface DevJSX
```

Property

Modifiers

Type

Description

columnNumber

number

fileName

string

lineNumber

number

stack?

string

(Optional)

Edit this section

## DialogHTMLAttributes

```
export interface DialogHTMLAttributes<T extends Element> extends Attrs<'dialog', T>
```

Extends: Attrs<'dialog', T>

Edit this section

## DOMAttributes

The Qwik-specific attributes that DOM elements accept

```
export interface DOMAttributes<EL extends Element> extends DOMAttributesBase<EL>, QwikEvents<EL>
```

Extends: DOMAttributesBase<EL>, QwikEvents<EL>

Property

Modifiers

Type

Description

class?

ClassList | Signal<ClassList> | undefined

(Optional)

Edit this section

## EagernessOptions

Warning: This API is now obsolete.

use useVisibleTask$ or useResource$, useTask$ is for running tasks as part of the initial SSR render

```
export type EagernessOptions = "visible" | "load" | "idle";
```

Edit this section

## Element

```
type Element = JSXOutput;
```

References: JSXOutput

## ElementChildrenAttribute

```
interface ElementChildrenAttribute
```

Property

Modifiers

Type

Description

children

JSXChildren

## ElementType

```
type ElementType = string | FunctionComponent<Record<any, any>>;
```

References: FunctionComponent

## EmbedHTMLAttributes

```
export interface EmbedHTMLAttributes<T extends Element> extends Attrs<'embed', T>
```

Extends: Attrs<'embed', T>

Edit this section

## ErrorBoundaryStore

```
export interface ErrorBoundaryStore
```

Property

Modifiers

Type

Description

error

any | undefined

Edit this section

## event$

```
event$: <T>(qrl: T) => QRL<T>;
```

Parameter

Type

Description

qrl

T

Returns:

QRL<T>

Edit this section

## EventHandler

A DOM event handler

```
export type EventHandler<EV = Event, EL = Element> = {
  bivarianceHack(event: EV, element: EL): any;
}["bivarianceHack"];
```

Edit this section

## eventQrl

```
eventQrl: <T>(qrl: QRL<T>) => QRL<T>;
```

Parameter

Type

Description

qrl

QRL<T>

Returns:

QRL<T>

Edit this section

## FieldsetHTMLAttributes

```
export interface FieldsetHTMLAttributes<T extends Element> extends Attrs<'fieldset', T>
```

Extends: Attrs<'fieldset', T>

Edit this section

## FormHTMLAttributes

```
export interface FormHTMLAttributes<T extends Element> extends Attrs<'form', T>
```

Extends: Attrs<'form', T>

Edit this section

## Fragment

```
Fragment: FunctionComponent<{
  children?: any;
  key?: string | number | null;
}>;
```

Edit this section

## FunctionComponent

Any function taking a props object that returns JSXOutput.

The key, flags and dev parameters are for internal use.

```
export type FunctionComponent<P = unknown> = {
  renderFn(
    props: P,
    key: string | null,
    flags: number,
    dev?: DevJSX,
  ): JSXOutput;
}["renderFn"];
```

References: DevJSX, JSXOutput

Edit this section

## getPlatform

Retrieve the CorePlatform.

The CorePlatform is also responsible for retrieving the Manifest, that contains mappings from symbols to javascript import chunks. For this reason, CorePlatform can't be global, but is specific to the application currently running. On server it is possible that many different applications are running in a single server instance, and for this reason the CorePlatform is associated with the application document.

```
getPlatform: () => CorePlatform;
```

Returns:

CorePlatform

Edit this section

## h

```
export declare namespace h
```

Function

Description

h(type)

h(type, data)

h(type, text)

h(type, children)

h(type, data, text)

h(type, data, children)

h(sel, data, children)

Edit this section

## h

```
export declare namespace h
```

Function

Description

h(type)

h(type, data)

h(type, text)

h(type, children)

h(type, data, text)

h(type, data, children)

h(sel, data, children)

Edit this section

## HrHTMLAttributes

```
export interface HrHTMLAttributes<T extends Element> extends Attrs<'hr', T>
```

Extends: Attrs<'hr', T>

Edit this section

## HTMLAttributeAnchorTarget

```
export type HTMLAttributeAnchorTarget =
  | "_self"
  | "_blank"
  | "_parent"
  | "_top"
  | (string & {});
```

Edit this section

## HTMLAttributeReferrerPolicy

```
export type HTMLAttributeReferrerPolicy = ReferrerPolicy;
```

Edit this section

## HTMLAttributes

```
export interface HTMLAttributes<E extends Element> extends HTMLElementAttrs, DOMAttributes<E>
```

Extends: HTMLElementAttrs, DOMAttributes<E>

Edit this section

## HTMLCrossOriginAttribute

```
export type HTMLCrossOriginAttribute =
  | "anonymous"
  | "use-credentials"
  | ""
  | undefined;
```

Edit this section

## HTMLElementAttrs

```
export interface HTMLElementAttrs extends HTMLAttributesBase, FilterBase<HTMLElement>
```

Extends: HTMLAttributesBase, FilterBase<HTMLElement>

Edit this section

## HTMLFragment

```
HTMLFragment: FunctionComponent<{
  dangerouslySetInnerHTML: string;
}>;
```

Edit this section

## HtmlHTMLAttributes

```
export interface HtmlHTMLAttributes<T extends Element> extends Attrs<'html', T>
```

Extends: Attrs<'html', T>

Edit this section

## HTMLInputAutocompleteAttribute

```
export type HTMLInputAutocompleteAttribute =
  | "on"
  | "off"
  | "billing"
  | "shipping"
  | "name"
  | "honorific-prefix"
  | "given-name"
  | "additional-name"
  | "family-name"
  | "honorific-suffix"
  | "nickname"
  | "username"
  | "new-password"
  | "current-password"
  | "one-time-code"
  | "organization-title"
  | "organization"
  | "street-address"
  | "address-line1"
  | "address-line2"
  | "address-line3"
  | "address-level4"
  | "address-level3"
  | "address-level2"
  | "address-level1"
  | "country"
  | "country-name"
  | "postal-code"
  | "cc-name"
  | "cc-given-name"
  | "cc-additional-name"
  | "cc-family-name"
  | "cc-number"
  | "cc-exp"
  | "cc-exp-month"
  | "cc-exp-year"
  | "cc-csc"
  | "cc-type"
  | "transaction-currency"
  | "transaction-amount"
  | "language"
  | "bday"
  | "bday-day"
  | "bday-month"
  | "bday-year"
  | "sex"
  | "url"
  | "photo";
```

Edit this section

## HTMLInputTypeAttribute

```
export type HTMLInputTypeAttribute =
  | "button"
  | "checkbox"
  | "color"
  | "date"
  | "datetime-local"
  | "email"
  | "file"
  | "hidden"
  | "image"
  | "month"
  | "number"
  | "password"
  | "radio"
  | "range"
  | "reset"
  | "search"
  | "submit"
  | "tel"
  | "text"
  | "time"
  | "url"
  | "week"
  | (string & {});
```

Edit this section

## IframeHTMLAttributes

```
export interface IframeHTMLAttributes<T extends Element> extends Attrs<'iframe', T>
```

Extends: Attrs<'iframe', T>

Edit this section

## ImgHTMLAttributes

```
export interface ImgHTMLAttributes<T extends Element> extends Attrs<'img', T>
```

Extends: Attrs<'img', T>

Edit this section

## implicit$FirstArg

Create a ____$(...) convenience method from ___(...).

It is very common for functions to take a lazy-loadable resource as a first argument. For this reason, the Qwik Optimizer automatically extracts the first argument from any function which ends in $.

This means that foo$(arg0) and foo($(arg0)) are equivalent with respect to Qwik Optimizer. The former is just a shorthand for the latter.

For example, these function calls are equivalent:

```
export function myApi(callback: QRL<() => void>): void {
  // ...
}
 
export const myApi$ = implicit$FirstArg(myApi);
// type of myApi$: (callback: () => void): void
 
// can be used as:
myApi$(() => console.log("callback"));
 
// will be transpiled to:
// FILE: <current file>
myApi(qrl("./chunk-abc.js", "callback"));
 
// FILE: chunk-abc.js
export const callback = () => console.log("callback");
```

```
implicit$FirstArg: <FIRST, REST extends any[], RET>(
    fn: (qrl: QRL<FIRST>, ...rest: REST) => RET,
  ) =>
  (qrl: FIRST, ...rest: REST) =>
    RET;
```

Parameter

Type

Description

fn

(qrl: QRL<FIRST>, ...rest: REST) => RET

A function that should have its first argument automatically $.

Returns:

((qrl: FIRST, ...rest: REST) => RET)

Edit this section

## InputHTMLAttributes

```
export type InputHTMLAttributes<T extends Element> = Attrs<
  "input",
  T,
  HTMLInputElement
>;
```

Edit this section

## InsHTMLAttributes

```
export interface InsHTMLAttributes<T extends Element> extends Attrs<'ins', T>
```

Extends: Attrs<'ins', T>

Edit this section

## IntrinsicAttributes

```
interface IntrinsicAttributes extends QwikIntrinsicAttributes
```

Extends: QwikIntrinsicAttributes

## IntrinsicElements

```
export interface IntrinsicElements extends IntrinsicHTMLElements, IntrinsicSVGElements
```

Extends: IntrinsicHTMLElements, IntrinsicSVGElements

Edit this section

## isSignal

Checks if a given object is a Signal.

```
isSignal: <T = unknown>(obj: any) => obj is Signal<T>
```

Parameter

Type

Description

obj

any

The object to check if Signal.

Returns:

obj is Signal<T>

Boolean - True if the object is a Signal.

Edit this section

## jsx

Used by the JSX transpilers to create a JSXNode. Note that the optimizer will not use this, instead using _jsxQ, _jsxS, and _jsxC directly.

```
jsx: <T extends string | FunctionComponent<any>>(
  type: T,
  props: T extends FunctionComponent<infer PROPS>
    ? PROPS
    : Record<any, unknown>,
  key?: string | number | null,
) => JSXNode<T>;
```

Parameter

Type

Description

type

T

props

T extends FunctionComponent<infer PROPS> ? PROPS : Record<any, unknown>

key

string | number | null

(Optional)

Returns:

JSXNode<T>

Edit this section

## JSXChildren

```
export type JSXChildren =
  | string
  | number
  | boolean
  | null
  | undefined
  | Function
  | RegExp
  | JSXChildren[]
  | Promise<JSXChildren>
  | Signal<JSXChildren>
  | JSXNode;
```

References: JSXChildren, Signal, JSXNode

Edit this section

## jsxDEV

```
jsxDEV: <T extends string | FunctionComponent<Record<any, unknown>>>(
  type: T,
  props: T extends FunctionComponent<infer PROPS>
    ? PROPS
    : Record<any, unknown>,
  key: string | number | null | undefined,
  _isStatic: boolean,
  opts: JsxDevOpts,
  _ctx: unknown,
) => JSXNode<T>;
```

Parameter

Type

Description

type

T

props

T extends FunctionComponent<infer PROPS> ? PROPS : Record<any, unknown>

key

string | number | null | undefined

_isStatic

boolean

opts

JsxDevOpts

_ctx

unknown

Returns:

JSXNode<T>

Edit this section

## JSXNode

A JSX Node, an internal structure. You probably want to use JSXOutput instead.

```
export interface JSXNode<T extends string | FunctionComponent | unknown = unknown>
```

Property

Modifiers

Type

Description

children

JSXChildren | null

dev?

DevJSX

(Optional)

key

string | null

props

T extends FunctionComponent<infer P> ? P : Record<any, unknown>

type

T

Edit this section

## JSXOutput

Any valid output for a component

```
export type JSXOutput =
  | JSXNode
  | string
  | number
  | boolean
  | null
  | undefined
  | JSXOutput[];
```

References: JSXNode, JSXOutput

Edit this section

## JSXTagName

```
export type JSXTagName =
  | keyof HTMLElementTagNameMap
  | Omit<string, keyof HTMLElementTagNameMap>;
```

Edit this section

## KeygenHTMLAttributes

Warning: This API is now obsolete.

in html5

```
export interface KeygenHTMLAttributes<T extends Element> extends Attrs<'base', T>
```

Extends: Attrs<'base', T>

Edit this section

## KnownEventNames

The names of events that Qwik knows about. They are all lowercase, but on the JSX side, they are PascalCase for nicer DX. (onAuxClick$ vs onauxclick$)

```
export type KnownEventNames = LiteralUnion<AllEventKeys, string>;
```

Edit this section

## LabelHTMLAttributes

```
export interface LabelHTMLAttributes<T extends Element> extends Attrs<'label', T>
```

Extends: Attrs<'label', T>

Edit this section

## LiHTMLAttributes

```
export interface LiHTMLAttributes<T extends Element> extends Attrs<'li', T>
```

Extends: Attrs<'li', T>

Edit this section

## LinkHTMLAttributes

```
export interface LinkHTMLAttributes<T extends Element> extends Attrs<'link', T>
```

Extends: Attrs<'link', T>

Edit this section

## MapHTMLAttributes

```
export interface MapHTMLAttributes<T extends Element> extends Attrs<'map', T>
```

Extends: Attrs<'map', T>

Edit this section

## MediaHTMLAttributes

```
export interface MediaHTMLAttributes<T extends Element> extends HTMLAttributes<T>, Augmented<HTMLMediaElement, {
    crossOrigin?: HTMLCrossOriginAttribute;
}>
```

Extends: HTMLAttributes<T>, Augmented<HTMLMediaElement, { crossOrigin?: HTMLCrossOriginAttribute; }>

Property

Modifiers

Type

Description

crossOrigin?

HTMLCrossOriginAttribute

(Optional)

Edit this section

## MenuHTMLAttributes

```
export interface MenuHTMLAttributes<T extends Element> extends Attrs<'menu', T>
```

Extends: Attrs<'menu', T>

Edit this section

## MetaHTMLAttributes

```
export interface MetaHTMLAttributes<T extends Element> extends Attrs<'meta', T>
```

Extends: Attrs<'meta', T>

Edit this section

## MeterHTMLAttributes

```
export interface MeterHTMLAttributes<T extends Element> extends Attrs<'meter', T>
```

Extends: Attrs<'meter', T>

Edit this section

## NativeAnimationEvent

Warning: This API is now obsolete.

Use AnimationEvent and use the second argument to the handler function for the current event target

```
export type NativeAnimationEvent = AnimationEvent;
```

Edit this section

## NativeClipboardEvent

Warning: This API is now obsolete.

Use ClipboardEvent and use the second argument to the handler function for the current event target

```
export type NativeClipboardEvent = ClipboardEvent;
```

Edit this section

## NativeCompositionEvent

Warning: This API is now obsolete.

Use CompositionEvent and use the second argument to the handler function for the current event target

```
export type NativeCompositionEvent = CompositionEvent;
```

Edit this section

## NativeDragEvent

Warning: This API is now obsolete.

Use DragEvent and use the second argument to the handler function for the current event target

```
export type NativeDragEvent = DragEvent;
```

Edit this section

## NativeFocusEvent

Warning: This API is now obsolete.

Use FocusEvent and use the second argument to the handler function for the current event target

```
export type NativeFocusEvent = FocusEvent;
```

Edit this section

## NativeKeyboardEvent

Warning: This API is now obsolete.

Use KeyboardEvent and use the second argument to the handler function for the current event target

```
export type NativeKeyboardEvent = KeyboardEvent;
```

Edit this section

## NativeMouseEvent

Warning: This API is now obsolete.

Use MouseEvent and use the second argument to the handler function for the current event target

```
export type NativeMouseEvent = MouseEvent;
```

Edit this section

## NativePointerEvent

Warning: This API is now obsolete.

Use PointerEvent and use the second argument to the handler function for the current event target

```
export type NativePointerEvent = PointerEvent;
```

Edit this section

## NativeTouchEvent

Warning: This API is now obsolete.

Use TouchEvent and use the second argument to the handler function for the current event target

```
export type NativeTouchEvent = TouchEvent;
```

Edit this section

## NativeTransitionEvent

Warning: This API is now obsolete.

Use TransitionEvent and use the second argument to the handler function for the current event target

```
export type NativeTransitionEvent = TransitionEvent;
```

Edit this section

## NativeUIEvent

Warning: This API is now obsolete.

Use UIEvent and use the second argument to the handler function for the current event target

```
export type NativeUIEvent = UIEvent;
```

Edit this section

## NativeWheelEvent

Warning: This API is now obsolete.

Use WheelEvent and use the second argument to the handler function for the current event target

```
export type NativeWheelEvent = WheelEvent;
```

Edit this section

## noSerialize

Returned type of the noSerialize() function. It will be TYPE or undefined.

```
export type NoSerialize<T> =
  | (T & {
      __no_serialize__: true;
    })
  | undefined;
```

Edit this section

## NoSerialize

Returned type of the noSerialize() function. It will be TYPE or undefined.

```
export type NoSerialize<T> =
  | (T & {
      __no_serialize__: true;
    })
  | undefined;
```

Edit this section

## Numberish

```
export type Numberish = number | `${number}`;
```

Edit this section

## ObjectHTMLAttributes

```
export interface ObjectHTMLAttributes<T extends Element> extends Attrs<'object', T>
```

Extends: Attrs<'object', T>

Edit this section

## OlHTMLAttributes

```
export interface OlHTMLAttributes<T extends Element> extends Attrs<'ol', T>
```

Extends: Attrs<'ol', T>

Edit this section

## OnRenderFn

```
export type OnRenderFn<PROPS> = (props: PROPS) => JSXOutput;
```

References: JSXOutput

Edit this section

## OnVisibleTaskOptions

```
export interface OnVisibleTaskOptions
```

Property

Modifiers

Type

Description

strategy?

VisibleTaskStrategy

(Optional) The strategy to use to determine when the "VisibleTask" should first execute.

Edit this section

## OptgroupHTMLAttributes

```
export interface OptgroupHTMLAttributes<T extends Element> extends Attrs<'optgroup', T>
```

Extends: Attrs<'optgroup', T>

Edit this section

## OptionHTMLAttributes

```
export interface OptionHTMLAttributes<T extends Element> extends Attrs<'option', T>
```

Extends: Attrs<'option', T>

Edit this section

## OutputHTMLAttributes

```
export interface OutputHTMLAttributes<T extends Element> extends Attrs<'output', T>
```

Extends: Attrs<'output', T>

Edit this section

## ParamHTMLAttributes

Warning: This API is now obsolete.

Old DOM API

```
export interface ParamHTMLAttributes<T extends Element> extends Attrs<'base', T, HTMLParamElement>
```

Extends: Attrs<'base', T, HTMLParamElement>

Edit this section

## PrefetchGraph

This API is provided as an alpha preview for developers and may change based on feedback that we receive. Do not use this API in a production environment.

Warning: This API is now obsolete.

This is no longer needed as the preloading happens automatically in qrl-class. You can remove this component from your app.

```
PrefetchGraph: (opts?: {
  base?: string;
  manifestHash?: string;
  manifestURL?: string;
  nonce?: string;
}) => JSXOutput;
```

Parameter

Type

Description

opts

{ base?: string; manifestHash?: string; manifestURL?: string; nonce?: string; }

(Optional)

Returns:

JSXOutput

Edit this section

## PrefetchServiceWorker

This API is provided as an alpha preview for developers and may change based on feedback that we receive. Do not use this API in a production environment.

Warning: This API is now obsolete.

This is no longer needed as the preloading happens automatically in qrl-class.ts. Leave this in your app for a while so it uninstalls existing service workers, but don't use it for new projects.

```
PrefetchServiceWorker: (opts: {
  base?: string;
  scope?: string;
  path?: string;
  verbose?: boolean;
  fetchBundleGraph?: boolean;
  nonce?: string;
}) => JSXNode<"script">;
```

Parameter

Type

Description

opts

{ base?: string; scope?: string; path?: string; verbose?: boolean; fetchBundleGraph?: boolean; nonce?: string; }

Returns:

JSXNode<'script'>

Edit this section

## ProgressHTMLAttributes

```
export interface ProgressHTMLAttributes<T extends Element> extends Attrs<'progress', T>
```

Extends: Attrs<'progress', T>

Edit this section

## PropFnInterface

Warning: This API is now obsolete.

Use QRL<> instead

```
export type PropFnInterface<ARGS extends any[], RET> = {
  __qwik_serializable__?: any;
  (...args: ARGS): Promise<RET>;
};
```

Edit this section

## PropFunction

Alias for QRL<T>. Of historic relevance only.

```
export type PropFunction<T> = QRL<T>;
```

References: QRL

Edit this section

## PropFunctionProps

Warning: This API is now obsolete.

Use QRL<> on your function props instead

```
export type PropFunctionProps<PROPS extends Record<any, any>> = {
  [K in keyof PROPS]: PROPS[K] extends undefined
    ? PROPS[K]
    : PROPS[K] extends ((...args: infer ARGS) => infer RET) | undefined
      ? PropFnInterface<ARGS, Awaited<RET>>
      : PROPS[K];
};
```

References: PropFnInterface

Edit this section

## PropsOf

Infers Props from the component or tag.

```
export type PropsOf<COMP> = COMP extends string
  ? COMP extends keyof QwikIntrinsicElements
    ? QwikIntrinsicElements[COMP]
    : QwikIntrinsicElements["span"]
  : NonNullable<COMP> extends never
    ? never
    : COMP extends FunctionComponent<infer PROPS>
      ? PROPS extends Record<any, infer V>
        ? IsAny<V> extends true
          ? never
          : ObjectProps<PROPS>
        : COMP extends Component<infer OrigProps>
          ? ObjectProps<OrigProps>
          : PROPS
      : never;
```

References: QwikIntrinsicElements, FunctionComponent, Component

```
const Desc = component$(
  ({ desc, ...props }: { desc: string } & PropsOf<"div">) => {
    return <div {...props}>{desc}</div>;
  },
);
 
const TitleBox = component$(
  ({ title, ...props }: { title: string } & PropsOf<Box>) => {
    return (
      <Box {...props}>
        <h1>{title}</h1>
      </Box>
    );
  },
);
```

Edit this section

## PublicProps

Extends the defined component PROPS, adding the default ones (children and q:slot) and allowing plain functions to QRL arguments.

```
export type PublicProps<PROPS> = (PROPS extends Record<any, any>
  ? Omit<PROPS, `${string}$`> & _Only$<PROPS>
  : unknown extends PROPS
    ? {}
    : PROPS) &
  ComponentBaseProps &
  ComponentChildren<PROPS>;
```

References: ComponentBaseProps

Edit this section

## qrl

The QRL type represents a lazy-loadable AND serializable resource.

QRL stands for Qwik URL.

Use QRL when you want to refer to a lazy-loaded resource. QRLs are most often used for code (functions) but can also be used for other resources such as strings in the case of styles.

QRL is an opaque token that is generated by the Qwik Optimizer. (Do not rely on any properties in QRL as it may change between versions.)

## Creating QRL references

Creating QRL is done using $(...) function. $(...) is a special marker for the Qwik Optimizer that marks that the code should be extracted into a lazy-loaded symbol.

```
useOnDocument(
  "mousemove",
  $((event) => console.log("mousemove", event)),
);
```

In the above code, the Qwik Optimizer detects $(...) and transforms the code as shown below:

```
// FILE: <current file>
useOnDocument("mousemove", qrl("./chunk-abc.js", "onMousemove"));
 
// FILE: chunk-abc.js
export const onMousemove = () => console.log("mousemove");
```

NOTE: qrl(...) is a result of Qwik Optimizer transformation. You should never have to invoke this function directly in your application. The qrl(...) function should be invoked only after the Qwik Optimizer transformation.

## Using QRLs

Use QRL type in your application when you want to get a lazy-loadable reference to a resource (most likely a function).

```
// Example of declaring a custom functions which takes callback as QRL.
export function useMyFunction(callback: QRL<() => void>) {
  doExtraStuff();
  // The callback passed to `onDocument` requires `QRL`.
  useOnDocument("mousemove", callback);
}
```

In the above example, the way to think about the code is that you are not asking for a callback function but rather a reference to a lazy-loadable callback function. Specifically, the function loading should be delayed until it is actually needed. In the above example, the function would not load until after a mousemove event on document fires.

## Resolving QRL references

At times it may be necessary to resolve a QRL reference to the actual value. This can be performed using QRL.resolve(..) function.

```
// Assume you have QRL reference to a greet function
const lazyGreet: QRL<() => void> = $(() => console.log("Hello World!"));
 
// Use `qrlImport` to load / resolve the reference.
const greet: () => void = await lazyGreet.resolve();
 
//  Invoke it
greet();
```

NOTE: element is needed because QRLs are relative and need a base location to resolve against. The base location is encoded in the HTML in the form of <div q:base="/url">.

## QRL.resolved

Once QRL.resolve() returns, the value is stored under QRL.resolved. This allows the value to be used without having to await QRL.resolve() again.

## Question: Why not just use import()?

At first glance, QRL serves the same purpose as import(). However, there are three subtle differences that need to be taken into account.

Let's assume that you intend to write code such as this:

```
return <button onClick={() => (await import('./chunk-abc.js')).onClick}>
```

The above code needs to be serialized into DOM such as:

```
<div q:base="/build/">
  <button on:click="./chunk-abc.js#onClick">...</button>
</div>
```

These are the main reasons why Qwik introduces its own concept of QRL.

```
export type QRL<TYPE = unknown> = {
  __qwik_serializable__?: any;
  __brand__QRL__: TYPE;
  resolve(): Promise<TYPE>;
  resolved: undefined | TYPE;
  getCaptured(): unknown[] | null;
  getSymbol(): string;
  getHash(): string;
  dev: QRLDev | null;
} & BivariantQrlFn<QrlArgs<TYPE>, QrlReturn<TYPE>>;
```

Edit this section

## QRL

The QRL type represents a lazy-loadable AND serializable resource.

QRL stands for Qwik URL.

Use QRL when you want to refer to a lazy-loaded resource. QRLs are most often used for code (functions) but can also be used for other resources such as strings in the case of styles.

QRL is an opaque token that is generated by the Qwik Optimizer. (Do not rely on any properties in QRL as it may change between versions.)

## Creating QRL references

Creating QRL is done using $(...) function. $(...) is a special marker for the Qwik Optimizer that marks that the code should be extracted into a lazy-loaded symbol.

```
useOnDocument(
  "mousemove",
  $((event) => console.log("mousemove", event)),
);
```

In the above code, the Qwik Optimizer detects $(...) and transforms the code as shown below:

```
// FILE: <current file>
useOnDocument("mousemove", qrl("./chunk-abc.js", "onMousemove"));
 
// FILE: chunk-abc.js
export const onMousemove = () => console.log("mousemove");
```

NOTE: qrl(...) is a result of Qwik Optimizer transformation. You should never have to invoke this function directly in your application. The qrl(...) function should be invoked only after the Qwik Optimizer transformation.

## Using QRLs

Use QRL type in your application when you want to get a lazy-loadable reference to a resource (most likely a function).

```
// Example of declaring a custom functions which takes callback as QRL.
export function useMyFunction(callback: QRL<() => void>) {
  doExtraStuff();
  // The callback passed to `onDocument` requires `QRL`.
  useOnDocument("mousemove", callback);
}
```

In the above example, the way to think about the code is that you are not asking for a callback function but rather a reference to a lazy-loadable callback function. Specifically, the function loading should be delayed until it is actually needed. In the above example, the function would not load until after a mousemove event on document fires.

## Resolving QRL references

At times it may be necessary to resolve a QRL reference to the actual value. This can be performed using QRL.resolve(..) function.

```
// Assume you have QRL reference to a greet function
const lazyGreet: QRL<() => void> = $(() => console.log("Hello World!"));
 
// Use `qrlImport` to load / resolve the reference.
const greet: () => void = await lazyGreet.resolve();
 
//  Invoke it
greet();
```

NOTE: element is needed because QRLs are relative and need a base location to resolve against. The base location is encoded in the HTML in the form of <div q:base="/url">.

## QRL.resolved

Once QRL.resolve() returns, the value is stored under QRL.resolved. This allows the value to be used without having to await QRL.resolve() again.

## Question: Why not just use import()?

At first glance, QRL serves the same purpose as import(). However, there are three subtle differences that need to be taken into account.

Let's assume that you intend to write code such as this:

```
return <button onClick={() => (await import('./chunk-abc.js')).onClick}>
```

The above code needs to be serialized into DOM such as:

```
<div q:base="/build/">
  <button on:click="./chunk-abc.js#onClick">...</button>
</div>
```

These are the main reasons why Qwik introduces its own concept of QRL.

```
export type QRL<TYPE = unknown> = {
  __qwik_serializable__?: any;
  __brand__QRL__: TYPE;
  resolve(): Promise<TYPE>;
  resolved: undefined | TYPE;
  getCaptured(): unknown[] | null;
  getSymbol(): string;
  getHash(): string;
  dev: QRLDev | null;
} & BivariantQrlFn<QrlArgs<TYPE>, QrlReturn<TYPE>>;
```

Edit this section

## QRLEventHandlerMulti

This API is provided as a beta preview for developers and may change based on feedback that we receive. Do not use this API in a production environment.

An event handler for Qwik events, can be a handler QRL or an array of handler QRLs.

```
export type QRLEventHandlerMulti<EV extends Event, EL> =
  | QRL<EventHandler<EV, EL>>
  | undefined
  | null
  | QRLEventHandlerMulti<EV, EL>[]
  | EventHandler<EV, EL>;
```

References: QRL, EventHandler, QRLEventHandlerMulti

Edit this section

## QuoteHTMLAttributes

```
export interface QuoteHTMLAttributes<T extends Element> extends Attrs<'q', T>
```

Extends: Attrs<'q', T>

Edit this section

## QwikAnimationEvent

Warning: This API is now obsolete.

Use AnimationEvent and use the second argument to the handler function for the current event target

```
export type QwikAnimationEvent<T = Element> = NativeAnimationEvent;
```

References: NativeAnimationEvent

Edit this section

## QwikAttributes

The Qwik DOM attributes without plain handlers, for use as function parameters

```
export interface QwikAttributes<EL extends Element> extends DOMAttributesBase<EL>, QwikEvents<EL, false>
```

Extends: DOMAttributesBase<EL>, QwikEvents<EL, false>

Property

Modifiers

Type

Description

class?

ClassList | undefined

(Optional)

Edit this section

## QwikChangeEvent

Warning: This API is now obsolete.

Use Event and use the second argument to the handler function for the current event target. Also note that in Qwik, onInput$ with the InputEvent is the event that behaves like onChange in React.

```
export type QwikChangeEvent<T = Element> = Event;
```

Edit this section

## QwikClipboardEvent

Warning: This API is now obsolete.

Use ClipboardEvent and use the second argument to the handler function for the current event target

```
export type QwikClipboardEvent<T = Element> = NativeClipboardEvent;
```

References: NativeClipboardEvent

Edit this section

## QwikCompositionEvent

Warning: This API is now obsolete.

Use CompositionEvent and use the second argument to the handler function for the current event target

```
export type QwikCompositionEvent<T = Element> = NativeCompositionEvent;
```

References: NativeCompositionEvent

Edit this section

## QwikDOMAttributes

```
export interface QwikDOMAttributes extends DOMAttributes<Element>
```

Extends: DOMAttributes<Element>

Edit this section

## QwikDragEvent

Warning: This API is now obsolete.

Use DragEvent and use the second argument to the handler function for the current event target

```
export type QwikDragEvent<T = Element> = NativeDragEvent;
```

References: NativeDragEvent

Edit this section

## QwikFocusEvent

Warning: This API is now obsolete.

Use FocusEvent and use the second argument to the handler function for the current event target

```
export type QwikFocusEvent<T = Element> = NativeFocusEvent;
```

References: NativeFocusEvent

Edit this section

## QwikHTMLElements

The DOM props without plain handlers, for use inside functions

```
export type QwikHTMLElements = {
  [tag in keyof HTMLElementTagNameMap]: Augmented<
    HTMLElementTagNameMap[tag],
    SpecialAttrs[tag]
  > &
    HTMLElementAttrs &
    QwikAttributes<HTMLElementTagNameMap[tag]>;
};
```

References: HTMLElementAttrs, QwikAttributes

Edit this section

## QwikIdleEvent

Emitted by qwik-loader on document when the document first becomes idle

```
export type QwikIdleEvent = CustomEvent<{}>;
```

Edit this section

## QwikInitEvent

Emitted by qwik-loader on document when the document first becomes interactive

```
export type QwikInitEvent = CustomEvent<{}>;
```

Edit this section

## QwikIntrinsicElements

The interface holds available attributes of both native DOM elements and custom Qwik elements. An example showing how to define a customizable wrapper component:

```
import { component$, Slot, type QwikIntrinsicElements } from "@builder.io/qwik";
 
type WrapperProps = {
  attributes?: QwikIntrinsicElements["div"];
};
 
export default component$<WrapperProps>(({ attributes }) => {
  return (
    <div {...attributes} class="p-2">
      <Slot />
    </div>
  );
});
```

Note: It is shorter to use PropsOf<'div'>

```
export interface QwikIntrinsicElements extends QwikHTMLElements, QwikSVGElements
```

Extends: QwikHTMLElements, QwikSVGElements

Edit this section

## QwikInvalidEvent

Warning: This API is now obsolete.

Use Event and use the second argument to the handler function for the current event target

```
export type QwikInvalidEvent<T = Element> = Event;
```

Edit this section

## QwikJSX

```
export declare namespace QwikJSX
```

Interface

Description

ElementChildrenAttribute

IntrinsicAttributes

IntrinsicElements

Type Alias

Description

Element

ElementType

Edit this section

## QwikKeyboardEvent

Warning: This API is now obsolete.

Use KeyboardEvent and use the second argument to the handler function for the current event target

```
export type QwikKeyboardEvent<T = Element> = NativeKeyboardEvent;
```

References: NativeKeyboardEvent

Edit this section

## QwikMouseEvent

Warning: This API is now obsolete.

Use MouseEvent and use the second argument to the handler function for the current event target

```
export type QwikMouseEvent<T = Element, E = NativeMouseEvent> = E;
```

References: NativeMouseEvent

Edit this section

## QwikPointerEvent

Warning: This API is now obsolete.

Use PointerEvent and use the second argument to the handler function for the current event target

```
export type QwikPointerEvent<T = Element> = NativePointerEvent;
```

References: NativePointerEvent

Edit this section

## QwikSubmitEvent

Warning: This API is now obsolete.

Use SubmitEvent and use the second argument to the handler function for the current event target

```
export type QwikSubmitEvent<T = Element> = SubmitEvent;
```

Edit this section

## QwikSVGElements

The SVG props without plain handlers, for use inside functions

```
export type QwikSVGElements = {
  [K in keyof Omit<
    SVGElementTagNameMap,
    keyof HTMLElementTagNameMap
  >]: SVGProps<SVGElementTagNameMap[K]>;
};
```

References: SVGProps

Edit this section

## QwikSymbolEvent

Emitted by qwik-loader when a module was lazily loaded

```
export type QwikSymbolEvent = CustomEvent<{
  symbol: string;
  element: Element;
  reqTime: number;
  qBase?: string;
  qManifest?: string;
  qVersion?: string;
  href?: string;
}>;
```

Edit this section

## QwikTouchEvent

Warning: This API is now obsolete.

Use TouchEvent and use the second argument to the handler function for the current event target

```
export type QwikTouchEvent<T = Element> = NativeTouchEvent;
```

References: NativeTouchEvent

Edit this section

## QwikTransitionEvent

Warning: This API is now obsolete.

Use TransitionEvent and use the second argument to the handler function for the current event target

```
export type QwikTransitionEvent<T = Element> = NativeTransitionEvent;
```

References: NativeTransitionEvent

Edit this section

## QwikUIEvent

Warning: This API is now obsolete.

Use UIEvent and use the second argument to the handler function for the current event target

```
export type QwikUIEvent<T = Element> = NativeUIEvent;
```

References: NativeUIEvent

Edit this section

## QwikVisibleEvent

Emitted by qwik-loader when an element becomes visible. Used by useVisibleTask$

```
export type QwikVisibleEvent = CustomEvent<IntersectionObserverEntry>;
```

Edit this section

## QwikWheelEvent

Warning: This API is now obsolete.

Use WheelEvent and use the second argument to the handler function for the current event target

```
export type QwikWheelEvent<T = Element> = NativeWheelEvent;
```

References: NativeWheelEvent

Edit this section

## ReadonlySignal

```
export type ReadonlySignal<T = unknown> = Readonly<Signal<T>>;
```

References: Signal

Edit this section

## render

Render JSX.

Use this method to render JSX. This function does reconciling which means it always tries to reuse what is already in the DOM (rather then destroy and recreate content.) It returns a cleanup function you could use for cleaning up subscriptions.

```
render: (
  parent: Element | Document,
  jsxOutput: JSXOutput | FunctionComponent<any>,
  opts?: RenderOptions,
) => Promise<RenderResult>;
```

Parameter

Type

Description

parent

Element | Document

Element which will act as a parent to jsxNode. When possible the rendering will try to reuse existing nodes.

jsxOutput

JSXOutput | FunctionComponent<any>

JSX to render

opts

RenderOptions

(Optional)

Returns:

Promise<RenderResult>

An object containing a cleanup function.

Edit this section

## RenderOnce

```
RenderOnce: FunctionComponent<{
  children?: unknown;
  key?: string | number | null | undefined;
}>;
```

Edit this section

## RenderOptions

```
export interface RenderOptions
```

Property

Modifiers

Type

Description

serverData?

Record<string, any>

(Optional)

Edit this section

## RenderResult

```
export interface RenderResult
```

Method

Description

cleanup()

Edit this section

## RenderSSROptions

```
export interface RenderSSROptions
```

Property

Modifiers

Type

Description

base?

string

(Optional)

beforeClose?

(contexts: QContext[], containerState: ContainerState, containsDynamic: boolean, textNodes: Map<string, string>) => Promise<JSXNode>

(Optional)

beforeContent?

JSXNode<string>[]

(Optional)

containerAttributes

Record<string, string>

containerTagName

string

manifestHash

string

serverData?

Record<string, any>

(Optional)

stream

StreamWriter

Edit this section

## Resource

This method works like an async memoized function that runs whenever some tracked value changes and returns some data.

useResource however returns immediate a ResourceReturn object that contains the data and a state that indicates if the data is available or not.

The status can be one of the following:

### Example

Example showing how useResource to perform a fetch to request the weather, whenever the input city name changes.

```
const Cmp = component$(() => {
  const cityS = useSignal("");
 
  const weatherResource = useResource$(async ({ track, cleanup }) => {
    const cityName = track(cityS);
    const abortController = new AbortController();
    cleanup(() => abortController.abort("cleanup"));
    const res = await fetch(`http://weatherdata.com?city=${cityName}`, {
      signal: abortController.signal,
    });
    const data = await res.json();
    return data as { temp: number };
  });
 
  return (
    <div>
      <input name="city" bind:value={cityS} />
      <Resource
        value={weatherResource}
        onResolved={(weather) => {
          return <div>Temperature: {weather.temp}</div>;
        }}
      />
    </div>
  );
});
```

```
Resource: <T>(props: ResourceProps<T>) => JSXOutput;
```

Parameter

Type

Description

props

ResourceProps<T>

Returns:

JSXOutput

Edit this section

## ResourceCtx

```
export interface ResourceCtx<T>
```

Property

Modifiers

Type

Description

previous

readonly

T | undefined

track

readonly

Tracker

Method

Description

cache(policyOrMilliseconds)

cleanup(callback)

Edit this section

## ResourceFn

```
export type ResourceFn<T> = (ctx: ResourceCtx<unknown>) => ValueOrPromise<T>;
```

References: ResourceCtx, ValueOrPromise

Edit this section

## ResourceOptions

Options to pass to useResource$()

```
export interface ResourceOptions
```

Property

Modifiers

Type

Description

timeout?

number

(Optional) Timeout in milliseconds. If the resource takes more than the specified millisecond, it will timeout. Resulting on a rejected resource.

Edit this section

## ResourcePending

```
export interface ResourcePending<T>
```

Property

Modifiers

Type

Description

loading

readonly

boolean

value

readonly

Promise<T>

Edit this section

## ResourceProps

```
export interface ResourceProps<T>
```

Property

Modifiers

Type

Description

onPending?

() => JSXOutput

(Optional)

onRejected?

(reason: Error) => JSXOutput

(Optional)

onResolved

(value: T) => JSXOutput

value

readonly

ResourceReturn<T> | Signal<Promise<T> | T> | Promise<T>

Edit this section

## ResourceRejected

```
export interface ResourceRejected<T>
```

Property

Modifiers

Type

Description

loading

readonly

boolean

value

readonly

Promise<T>

Edit this section

## ResourceResolved

```
export interface ResourceResolved<T>
```

Property

Modifiers

Type

Description

loading

readonly

boolean

value

readonly

Promise<T>

Edit this section

## ResourceReturn

```
export type ResourceReturn<T> =
  | ResourcePending<T>
  | ResourceResolved<T>
  | ResourceRejected<T>;
```

References: ResourcePending, ResourceResolved, ResourceRejected

Edit this section

## ScriptHTMLAttributes

```
export interface ScriptHTMLAttributes<T extends Element> extends Attrs<'script', T>
```

Extends: Attrs<'script', T>

Edit this section

## SelectHTMLAttributes

```
export interface SelectHTMLAttributes<T extends Element> extends Attrs<'select', T>
```

Extends: Attrs<'select', T>

Edit this section

## setPlatform

Sets the CorePlatform.

This is useful to override the platform in tests to change the behavior of, requestAnimationFrame, and import resolution.

```
setPlatform: (plt: CorePlatform) => CorePlatform;
```

Parameter

Type

Description

plt

CorePlatform

Returns:

CorePlatform

Edit this section

## Signal

A signal is a reactive value which can be read and written. When the signal is written, all tasks which are tracking the signal will be re-run and all components that read the signal will be re-rendered.

Furthermore, when a signal value is passed as a prop to a component, the optimizer will automatically forward the signal. This means that return <div title={signal.value}>hi</div> will update the title attribute when the signal changes without having to re-render the component.

```
export interface Signal<T = any>
```

Property

Modifiers

Type

Description

value

T

Edit this section

## Size

```
export type Size = number | string;
```

Edit this section

## SkipRender

```
SkipRender: JSXNode;
```

Edit this section

## Slot

Allows to project the children of the current component. <Slot/> can only be used within the context of a component defined with component$.

```
Slot: FunctionComponent<{
  name?: string;
}>;
```

Edit this section

## SlotHTMLAttributes

```
export interface SlotHTMLAttributes<T extends Element> extends Attrs<'slot', T>
```

Extends: Attrs<'slot', T>

Edit this section

## SnapshotListener

```
export interface SnapshotListener
```

Property

Modifiers

Type

Description

el

Element

key

string

qrl

QRL<any>

Edit this section

## SnapshotMeta

```
export type SnapshotMeta = Record<string, SnapshotMetaValue>;
```

References: SnapshotMetaValue

Edit this section

## SnapshotMetaValue

```
export interface SnapshotMetaValue
```

Property

Modifiers

Type

Description

c?

string

(Optional)

h?

string

(Optional)

s?

string

(Optional)

w?

string

(Optional)

Edit this section

## SnapshotResult

```
export interface SnapshotResult
```

Property

Modifiers

Type

Description

funcs

string[]

mode

'render' | 'listeners' | 'static'

objs

any[]

qrls

QRL[]

resources

ResourceReturnInternal<any>[]

state

SnapshotState

Edit this section

## SnapshotState

```
export interface SnapshotState
```

Property

Modifiers

Type

Description

ctx

SnapshotMeta

objs

any[]

refs

Record<string, string>

subs

any[]

Edit this section

## SourceHTMLAttributes

```
export interface SourceHTMLAttributes<T extends Element> extends Attrs<'source', T>
```

Extends: Attrs<'source', T>

Edit this section

## SSRComment

```
SSRComment: FunctionComponent<{
  data: string;
}>;
```

Edit this section

## SSRHint

Warning: This API is now obsolete.

```
SSRHint: FunctionComponent<SSRHintProps>;
```

Edit this section

## SSRHintProps

```
export type SSRHintProps = {
  dynamic?: boolean;
};
```

Edit this section

## SSRRaw

```
SSRRaw: FunctionComponent<{
  data: string;
}>;
```

Edit this section

## SSRStream

```
SSRStream: FunctionComponent<SSRStreamProps>;
```

Edit this section

## SSRStreamBlock

```
SSRStreamBlock: FunctionComponent<{
  children?: any;
}>;
```

Edit this section

## SSRStreamProps

```
export type SSRStreamProps = {
  children:
    | AsyncGenerator<JSXChildren, void, any>
    | ((stream: StreamWriter) => Promise<void>)
    | (() => AsyncGenerator<JSXChildren, void, any>);
};
```

References: JSXChildren, StreamWriter

Edit this section

## StreamWriter

```
export type StreamWriter = {
  write: (chunk: string) => void;
};
```

Edit this section

## StyleHTMLAttributes

```
export interface StyleHTMLAttributes<T extends Element> extends Attrs<'style', T>
```

Extends: Attrs<'style', T>

Edit this section

## SVGAttributes

The TS types don't include the SVG attributes so we have to define them ourselves

NOTE: These props are probably not complete

```
export interface SVGAttributes<T extends Element = Element> extends AriaAttributes
```

Extends: AriaAttributes

Property

Modifiers

Type

Description

"accent-height"?

number | string | undefined

(Optional)

"alignment-baseline"?

'auto' | 'baseline' | 'before-edge' | 'text-before-edge' | 'middle' | 'central' | 'after-edge' | 'text-after-edge' | 'ideographic' | 'alphabetic' | 'hanging' | 'mathematical' | 'inherit' | undefined

(Optional)

"arabic-form"?

'initial' | 'medial' | 'terminal' | 'isolated' | undefined

(Optional)

"baseline-shift"?

number | string | undefined

(Optional)

"cap-height"?

number | string | undefined

(Optional)

"clip-path"?

string | undefined

(Optional)

"clip-rule"?

number | string | undefined

(Optional)

"color-interpolation-filters"?

'auto' | 's-rGB' | 'linear-rGB' | 'inherit' | undefined

(Optional)

"color-interpolation"?

number | string | undefined

(Optional)

"color-profile"?

number | string | undefined

(Optional)

"color-rendering"?

number | string | undefined

(Optional)

"dominant-baseline"?

number | string | undefined

(Optional)

"edge-mode"?

number | string | undefined

(Optional)

"enable-background"?

number | string | undefined

(Optional)

"fill-opacity"?

number | string | undefined

(Optional)

"fill-rule"?

'nonzero' | 'evenodd' | 'inherit' | undefined

(Optional)

"flood-color"?

number | string | undefined

(Optional)

"flood-opacity"?

number | string | undefined

(Optional)

"font-family"?

string | undefined

(Optional)

"font-size-adjust"?

number | string | undefined

(Optional)

"font-size"?

number | string | undefined

(Optional)

"font-stretch"?

number | string | undefined

(Optional)

"font-style"?

number | string | undefined

(Optional)

"font-variant"?

number | string | undefined

(Optional)

"font-weight"?

number | string | undefined

(Optional)

"glyph-name"?

number | string | undefined

(Optional)

"glyph-orientation-horizontal"?

number | string | undefined

(Optional)

"glyph-orientation-vertical"?

number | string | undefined

(Optional)

"horiz-adv-x"?

number | string | undefined

(Optional)

"horiz-origin-x"?

number | string | undefined

(Optional)

"image-rendering"?

number | string | undefined

(Optional)

"letter-spacing"?

number | string | undefined

(Optional)

"lighting-color"?

number | string | undefined

(Optional)

"marker-end"?

string | undefined

(Optional)

"marker-mid"?

string | undefined

(Optional)

"marker-start"?

string | undefined

(Optional)

"overline-position"?

number | string | undefined

(Optional)

"overline-thickness"?

number | string | undefined

(Optional)

"paint-order"?

number | string | undefined

(Optional)

"pointer-events"?

number | string | undefined

(Optional)

"rendering-intent"?

number | string | undefined

(Optional)

"shape-rendering"?

number | string | undefined

(Optional)

"stop-color"?

string | undefined

(Optional)

"stop-opacity"?

number | string | undefined

(Optional)

"strikethrough-position"?

number | string | undefined

(Optional)

"strikethrough-thickness"?

number | string | undefined

(Optional)

"stroke-dasharray"?

string | number | undefined

(Optional)

"stroke-dashoffset"?

string | number | undefined

(Optional)

"stroke-linecap"?

'butt' | 'round' | 'square' | 'inherit' | undefined

(Optional)

"stroke-linejoin"?

'miter' | 'round' | 'bevel' | 'inherit' | undefined

(Optional)

"stroke-miterlimit"?

string | undefined

(Optional)

"stroke-opacity"?

number | string | undefined

(Optional)

"stroke-width"?

number | string | undefined

(Optional)

"text-anchor"?

string | undefined

(Optional)

"text-decoration"?

number | string | undefined

(Optional)

"text-rendering"?

number | string | undefined

(Optional)

"underline-position"?

number | string | undefined

(Optional)

"underline-thickness"?

number | string | undefined

(Optional)

"unicode-bidi"?

number | string | undefined

(Optional)

"unicode-range"?

number | string | undefined

(Optional)

"units-per-em"?

number | string | undefined

(Optional)

"v-alphabetic"?

number | string | undefined

(Optional)

"v-hanging"?

number | string | undefined

(Optional)

"v-ideographic"?

number | string | undefined

(Optional)

"v-mathematical"?

number | string | undefined

(Optional)

"vector-effect"?

number | string | undefined

(Optional)

"vert-adv-y"?

number | string | undefined

(Optional)

"vert-origin-x"?

number | string | undefined

(Optional)

"vert-origin-y"?

number | string | undefined

(Optional)

"word-spacing"?

number | string | undefined

(Optional)

"writing-mode"?

number | string | undefined

(Optional)

"x-channel-selector"?

string | undefined

(Optional)

"x-height"?

number | string | undefined

(Optional)

"xlink:actuate"?

string | undefined

(Optional)

"xlink:arcrole"?

string | undefined

(Optional)

"xlink:href"?

string | undefined

(Optional)

"xlink:role"?

string | undefined

(Optional)

"xlink:show"?

string | undefined

(Optional)

"xlink:title"?

string | undefined

(Optional)

"xlink:type"?

string | undefined

(Optional)

"xml:base"?

string | undefined

(Optional)

"xml:lang"?

string | undefined

(Optional)

"xml:space"?

string | undefined

(Optional)

"xmlns:xlink"?

string | undefined

(Optional)

accumulate?

'none' | 'sum' | undefined

(Optional)

additive?

'replace' | 'sum' | undefined

(Optional)

allowReorder?

'no' | 'yes' | undefined

(Optional)

alphabetic?

number | string | undefined

(Optional)

amplitude?

number | string | undefined

(Optional)

ascent?

number | string | undefined

(Optional)

attributeName?

string | undefined

(Optional)

attributeType?

string | undefined

(Optional)

autoReverse?

Booleanish | undefined

(Optional)

azimuth?

number | string | undefined

(Optional)

baseFrequency?

number | string | undefined

(Optional)

baseProfile?

number | string | undefined

(Optional)

bbox?

number | string | undefined

(Optional)

begin?

number | string | undefined

(Optional)

bias?

number | string | undefined

(Optional)

by?

number | string | undefined

(Optional)

calcMode?

number | string | undefined

(Optional)

clip?

number | string | undefined

(Optional)

clipPathUnits?

number | string | undefined

(Optional)

color?

string | undefined

(Optional)

contentScriptType?

number | string | undefined

(Optional)

contentStyleType?

number | string | undefined

(Optional)

crossOrigin?

HTMLCrossOriginAttribute

(Optional)

cursor?

number | string

(Optional)

cx?

number | string | undefined

(Optional)

cy?

number | string | undefined

(Optional)

d?

string | undefined

(Optional)

decelerate?

number | string | undefined

(Optional)

descent?

number | string | undefined

(Optional)

diffuseConstant?

number | string | undefined

(Optional)

direction?

number | string | undefined

(Optional)

display?

number | string | undefined

(Optional)

divisor?

number | string | undefined

(Optional)

dur?

number | string | undefined

(Optional)

dx?

number | string | undefined

(Optional)

dy?

number | string | undefined

(Optional)

elevation?

number | string | undefined

(Optional)

end?

number | string | undefined

(Optional)

exponent?

number | string | undefined

(Optional)

externalResourcesRequired?

number | string | undefined

(Optional)

fill?

string | undefined

(Optional)

filter?

string | undefined

(Optional)

filterRes?

number | string | undefined

(Optional)

filterUnits?

number | string | undefined

(Optional)

focusable?

number | string | undefined

(Optional)

format?

number | string | undefined

(Optional)

fr?

number | string | undefined

(Optional)

from?

number | string | undefined

(Optional)

fx?

number | string | undefined

(Optional)

fy?

number | string | undefined

(Optional)

g1?

number | string | undefined

(Optional)

g2?

number | string | undefined

(Optional)

glyphRef?

number | string | undefined

(Optional)

gradientTransform?

string | undefined

(Optional)

gradientUnits?

string | undefined

(Optional)

hanging?

number | string | undefined

(Optional)

height?

Size | undefined

(Optional)

href?

string | undefined

(Optional)

id?

string | undefined

(Optional)

ideographic?

number | string | undefined

(Optional)

in?

string | undefined

(Optional)

in2?

number | string | undefined

(Optional)

intercept?

number | string | undefined

(Optional)

k?

number | string | undefined

(Optional)

k1?

number | string | undefined

(Optional)

k2?

number | string | undefined

(Optional)

k3?

number | string | undefined

(Optional)

k4?

number | string | undefined

(Optional)

kernelMatrix?

number | string | undefined

(Optional)

kernelUnitLength?

number | string | undefined

(Optional)

kerning?

number | string | undefined

(Optional)

keyPoints?

number | string | undefined

(Optional)

keySplines?

number | string | undefined

(Optional)

keyTimes?

number | string | undefined

(Optional)

lang?

string | undefined

(Optional)

lengthAdjust?

number | string | undefined

(Optional)

limitingConeAngle?

number | string | undefined

(Optional)

local?

number | string | undefined

(Optional)

markerHeight?

number | string | undefined

(Optional)

markerUnits?

number | string | undefined

(Optional)

markerWidth?

number | string | undefined

(Optional)

mask?

string | undefined

(Optional)

maskContentUnits?

number | string | undefined

(Optional)

maskUnits?

number | string | undefined

(Optional)

mathematical?

number | string | undefined

(Optional)

max?

number | string | undefined

(Optional)

media?

string | undefined

(Optional)

method?

string | undefined

(Optional)

min?

number | string | undefined

(Optional)

mode?

number | string | undefined

(Optional)

name?

string | undefined

(Optional)

numOctaves?

number | string | undefined

(Optional)

offset?

number | string | undefined

(Optional)

opacity?

number | string | undefined

(Optional)

operator?

number | string | undefined

(Optional)

order?

number | string | undefined

(Optional)

orient?

number | string | undefined

(Optional)

orientation?

number | string | undefined

(Optional)

origin?

number | string | undefined

(Optional)

overflow?

number | string | undefined

(Optional)

panose1?

number | string | undefined

(Optional)

path?

string | undefined

(Optional)

pathLength?

number | string | undefined

(Optional)

patternContentUnits?

string | undefined

(Optional)

patternTransform?

number | string | undefined

(Optional)

patternUnits?

string | undefined

(Optional)

points?

string | undefined

(Optional)

pointsAtX?

number | string | undefined

(Optional)

pointsAtY?

number | string | undefined

(Optional)

pointsAtZ?

number | string | undefined

(Optional)

preserveAlpha?

number | string | undefined

(Optional)

preserveAspectRatio?

string | undefined

(Optional)

primitiveUnits?

number | string | undefined

(Optional)

r?

number | string | undefined

(Optional)

radius?

number | string | undefined

(Optional)

refX?

number | string | undefined

(Optional)

refY?

number | string | undefined

(Optional)

repeatCount?

number | string | undefined

(Optional)

repeatDur?

number | string | undefined

(Optional)

requiredextensions?

number | string | undefined

(Optional)

requiredFeatures?

number | string | undefined

(Optional)

restart?

number | string | undefined

(Optional)

result?

string | undefined

(Optional)

role?

string | undefined

(Optional)

rotate?

number | string | undefined

(Optional)

rx?

number | string | undefined

(Optional)

ry?

number | string | undefined

(Optional)

scale?

number | string | undefined

(Optional)

seed?

number | string | undefined

(Optional)

slope?

number | string | undefined

(Optional)

spacing?

number | string | undefined

(Optional)

specularConstant?

number | string | undefined

(Optional)

specularExponent?

number | string | undefined

(Optional)

speed?

number | string | undefined

(Optional)

spreadMethod?

string | undefined

(Optional)

startOffset?

number | string | undefined

(Optional)

stdDeviation?

number | string | undefined

(Optional)

stemh?

number | string | undefined

(Optional)

stemv?

number | string | undefined

(Optional)

stitchTiles?

number | string | undefined

(Optional)

string?

number | string | undefined

(Optional)

stroke?

string | undefined

(Optional)

style?

CSSProperties | string | undefined

(Optional)

surfaceScale?

number | string | undefined

(Optional)

systemLanguage?

number | string | undefined

(Optional)

tabindex?

number | undefined

(Optional)

tableValues?

number | string | undefined

(Optional)

target?

string | undefined

(Optional)

targetX?

number | string | undefined

(Optional)

targetY?

number | string | undefined

(Optional)

textLength?

number | string | undefined

(Optional)

to?

number | string | undefined

(Optional)

transform?

string | undefined

(Optional)

type?

string | undefined

(Optional)

u1?

number | string | undefined

(Optional)

u2?

number | string | undefined

(Optional)

unicode?

number | string | undefined

(Optional)

values?

string | undefined

(Optional)

version?

string | undefined

(Optional)

viewBox?

string | undefined

(Optional)

viewTarget?

number | string | undefined

(Optional)

visibility?

number | string | undefined

(Optional)

width?

Size | undefined

(Optional)

widths?

number | string | undefined

(Optional)

x?

number | string | undefined

(Optional)

x1?

number | string | undefined

(Optional)

x2?

number | string | undefined

(Optional)

xmlns?

string | undefined

(Optional)

y?

number | string | undefined

(Optional)

y1?

number | string | undefined

(Optional)

y2?

number | string | undefined

(Optional)

yChannelSelector?

string | undefined

(Optional)

z?

number | string | undefined

(Optional)

zoomAndPan?

string | undefined

(Optional)

Edit this section

## SVGProps

```
export interface SVGProps<T extends Element> extends SVGAttributes, QwikAttributes<T>
```

Extends: SVGAttributes, QwikAttributes<T>

Edit this section

## sync$

This API is provided as an alpha preview for developers and may change based on feedback that we receive. Do not use this API in a production environment.

Extract function into a synchronously loadable QRL.

NOTE: Synchronous QRLs functions can't close over any variables, including exports.

```
sync$: <T extends Function>(fn: T) => SyncQRL<T>;
```

Parameter

Type

Description

fn

T

Function to extract.

Returns:

SyncQRL<T>

Edit this section

## SyncQRL

This API is provided as an alpha preview for developers and may change based on feedback that we receive. Do not use this API in a production environment.

```
export interface SyncQRL<TYPE extends Function = any> extends QRL<TYPE>
```

Extends: QRL<TYPE>

Property

Modifiers

Type

Description

__brand__SyncQRL__

TYPE

(ALPHA)

dev

QRLDev | null

(ALPHA)

resolved

TYPE

(ALPHA)

Edit this section

## TableHTMLAttributes

```
export interface TableHTMLAttributes<T extends Element> extends Attrs<'table', T>
```

Extends: Attrs<'table', T>

Edit this section

## TaskCtx

```
export interface TaskCtx
```

Property

Modifiers

Type

Description

track

Tracker

Method

Description

cleanup(callback)

Edit this section

## TaskFn

```
export type TaskFn = (ctx: TaskCtx) => ValueOrPromise<void | (() => void)>;
```

References: TaskCtx, ValueOrPromise

Edit this section

## TdHTMLAttributes

```
export interface TdHTMLAttributes<T extends Element> extends Attrs<'td', T>
```

Extends: Attrs<'td', T>

Edit this section

## TextareaHTMLAttributes

```
export interface TextareaHTMLAttributes<T extends Element> extends Attrs<'textarea', T>
```

Extends: Attrs<'textarea', T>

Edit this section

## ThHTMLAttributes

```
export interface ThHTMLAttributes<T extends Element> extends Attrs<'tr', T>
```

Extends: Attrs<'tr', T>

Edit this section

## TimeHTMLAttributes

```
export interface TimeHTMLAttributes<T extends Element> extends Attrs<'time', T>
```

Extends: Attrs<'time', T>

Edit this section

## TitleHTMLAttributes

```
export interface TitleHTMLAttributes<T extends Element> extends Attrs<'title', T>
```

Extends: Attrs<'title', T>

Edit this section

## Tracker

Used to signal to Qwik which state should be watched for changes.

The Tracker is passed into the taskFn of useTask. It is intended to be used to wrap state objects in a read proxy which signals to Qwik which properties should be watched for changes. A change to any of the properties causes the taskFn to rerun.

### Example

The obs passed into the taskFn is used to mark state.count as a property of interest. Any changes to the state.count property will cause the taskFn to rerun.

```
const Cmp = component$(() => {
  const store = useStore({ count: 0, doubleCount: 0 });
  const signal = useSignal(0);
  useTask$(({ track }) => {
    // Any signals or stores accessed inside the task will be tracked
    const count = track(() => store.count);
    // You can also pass a signal to track() directly
    const signalCount = track(signal);
    store.doubleCount = count + signalCount;
  });
  return (
    <div>
      <span>
        {store.count} / {store.doubleCount}
      </span>
      <button
        onClick$={() => {
          store.count++;
          signal.value++;
        }}
      >
        +
      </button>
    </div>
  );
});
```

```
export interface Tracker
```

Edit this section

## TrackHTMLAttributes

```
export interface TrackHTMLAttributes<T extends Element> extends Attrs<'track', T>
```

Extends: Attrs<'track', T>

Edit this section

## untrack

Don't track listeners for this callback

```
untrack: <T>(fn: () => T) => T;
```

Parameter

Type

Description

fn

() => T

Returns:

T

Edit this section

## unwrapStore

Get the target value of the Proxy. Useful if you want to clone a store (structureClone, IndexedDB,...)

```
unwrapProxy: <T>(proxy: T) => T;
```

Parameter

Type

Description

proxy

T

Returns:

T

Edit this section

## useComputed$

Returns a computed signal which is calculated from the given function. A computed signal is a signal which is calculated from other signals. When the signals change, the computed signal is recalculated, and if the result changed, all tasks which are tracking the signal will be re-run and all components that read the signal will be re-rendered.

The function must be synchronous and must not have any side effects.

Async functions are deprecated because:

In v2, async functions won't work.

```
useComputed$: <T>(qrl: ComputedFn<T>) => Signal<Awaited<T>>;
```

Parameter

Type

Description

qrl

ComputedFn<T>

Returns:

Signal<Awaited<T>>

Edit this section

## useComputedQrl

```
useComputedQrl: <T>(qrl: QRL<ComputedFn<T>>) => Signal<Awaited<T>>;
```

Parameter

Type

Description

qrl

QRL<ComputedFn<T>>

Returns:

Signal<Awaited<T>>

Edit this section

## useConstant

Warning: This API is now obsolete.

This is a technology preview

Stores a value which is retained for the lifetime of the component.

If the value is a function, the function is invoked to calculate the actual value.

```
useConstant: <T>(value: (() => T) | T) => T;
```

Parameter

Type

Description

value

(() => T) | T

Returns:

T

Edit this section

## useContext

Retrieve Context value.

Use useContext() to retrieve the value of context in a component. To retrieve a value a parent component needs to invoke useContextProvider() to assign a value.

### Example

```
// Declare the Context type.
interface TodosStore {
  items: string[];
}
// Create a Context ID (no data is saved here.)
// You will use this ID to both create and retrieve the Context.
export const TodosContext = createContextId<TodosStore>("Todos");
 
// Example of providing context to child components.
export const App = component$(() => {
  useContextProvider(
    TodosContext,
    useStore<TodosStore>({
      items: ["Learn Qwik", "Build Qwik app", "Profit"],
    }),
  );
 
  return <Items />;
});
 
// Example of retrieving the context provided by a parent component.
export const Items = component$(() => {
  const todos = useContext(TodosContext);
  return (
    <ul>
      {todos.items.map((item) => (
        <li>{item}</li>
      ))}
    </ul>
  );
});
```

```
useContext: UseContext;
```

Edit this section

## useContextProvider

Assign a value to a Context.

Use useContextProvider() to assign a value to a context. The assignment happens in the component's function. Once assigned, use useContext() in any child component to retrieve the value.

Context is a way to pass stores to the child components without prop-drilling. Note that scalar values are allowed, but for reactivity you need signals or stores.

### Example

```
// Declare the Context type.
interface TodosStore {
  items: string[];
}
// Create a Context ID (no data is saved here.)
// You will use this ID to both create and retrieve the Context.
export const TodosContext = createContextId<TodosStore>("Todos");
 
// Example of providing context to child components.
export const App = component$(() => {
  useContextProvider(
    TodosContext,
    useStore<TodosStore>({
      items: ["Learn Qwik", "Build Qwik app", "Profit"],
    }),
  );
 
  return <Items />;
});
 
// Example of retrieving the context provided by a parent component.
export const Items = component$(() => {
  const todos = useContext(TodosContext);
  return (
    <ul>
      {todos.items.map((item) => (
        <li>{item}</li>
      ))}
    </ul>
  );
});
```

```
useContextProvider: <STATE>(context: ContextId<STATE>, newValue: STATE) => void
```

Parameter

Type

Description

context

ContextId<STATE>

The context to assign a value to.

newValue

STATE

Returns:

void

Edit this section

## useErrorBoundary

```
useErrorBoundary: () => ErrorBoundaryStore;
```

Returns:

ErrorBoundaryStore

Edit this section

## useId

```
useId: () => string;
```

Returns:

string

Edit this section

## useOn

Register a listener on the current component's host element.

Used to programmatically add event listeners. Useful from custom use* methods, which do not have access to the JSX. Otherwise, it's adding a JSX listener in the <div> is a better idea.

```
useOn: <T extends KnownEventNames>(event: T | T[], eventQrl: EventQRL<T>) => void
```

Parameter

Type

Description

event

T | T[]

eventQrl

EventQRL<T>

Returns:

void

Edit this section

## useOnDocument

Register a listener on document.

Used to programmatically add event listeners. Useful from custom use* methods, which do not have access to the JSX.

```
useOnDocument: <T extends KnownEventNames>(event: T | T[], eventQrl: EventQRL<T>) => void
```

Parameter

Type

Description

event

T | T[]

eventQrl

EventQRL<T>

Returns:

void

Edit this section

## useOnWindow

Register a listener on window.

Used to programmatically add event listeners. Useful from custom use* methods, which do not have access to the JSX.

```
useOnWindow: <T extends KnownEventNames>(event: T | T[], eventQrl: EventQRL<T>) => void
```

Parameter

Type

Description

event

T | T[]

eventQrl

EventQRL<T>

Returns:

void

Edit this section

## useResource$

This method works like an async memoized function that runs whenever some tracked value changes and returns some data.

useResource however returns immediate a ResourceReturn object that contains the data and a state that indicates if the data is available or not.

The status can be one of the following:

### Example

Example showing how useResource to perform a fetch to request the weather, whenever the input city name changes.

```
const Cmp = component$(() => {
  const cityS = useSignal("");
 
  const weatherResource = useResource$(async ({ track, cleanup }) => {
    const cityName = track(cityS);
    const abortController = new AbortController();
    cleanup(() => abortController.abort("cleanup"));
    const res = await fetch(`http://weatherdata.com?city=${cityName}`, {
      signal: abortController.signal,
    });
    const data = await res.json();
    return data as { temp: number };
  });
 
  return (
    <div>
      <input name="city" bind:value={cityS} />
      <Resource
        value={weatherResource}
        onResolved={(weather) => {
          return <div>Temperature: {weather.temp}</div>;
        }}
      />
    </div>
  );
});
```

```
useResource$: <T>(generatorFn: ResourceFn<T>, opts?: ResourceOptions) =>
  ResourceReturn<T>;
```

Parameter

Type

Description

generatorFn

ResourceFn<T>

opts

ResourceOptions

(Optional)

Returns:

ResourceReturn<T>

Edit this section

## useResourceQrl

This method works like an async memoized function that runs whenever some tracked value changes and returns some data.

useResource however returns immediate a ResourceReturn object that contains the data and a state that indicates if the data is available or not.

The status can be one of the following:

Avoid using a try/catch statement in useResource$. If you catch the error instead of passing it, the resource status will never be rejected.

### Example

Example showing how useResource to perform a fetch to request the weather, whenever the input city name changes.

```
const Cmp = component$(() => {
  const cityS = useSignal("");
 
  const weatherResource = useResource$(async ({ track, cleanup }) => {
    const cityName = track(cityS);
    const abortController = new AbortController();
    cleanup(() => abortController.abort("cleanup"));
    const res = await fetch(`http://weatherdata.com?city=${cityName}`, {
      signal: abortController.signal,
    });
    const data = await res.json();
    return data as { temp: number };
  });
 
  return (
    <div>
      <input name="city" bind:value={cityS} />
      <Resource
        value={weatherResource}
        onResolved={(weather) => {
          return <div>Temperature: {weather.temp}</div>;
        }}
      />
    </div>
  );
});
```

```
useResourceQrl: <T>(qrl: QRL<ResourceFn<T>>, opts?: ResourceOptions) =>
  ResourceReturn<T>;
```

Parameter

Type

Description

qrl

QRL<ResourceFn<T>>

opts

ResourceOptions

(Optional)

Returns:

ResourceReturn<T>

Edit this section

## useServerData

```
export declare function useServerData<T>(key: string): T | undefined;
```

Parameter

Type

Description

key

string

Returns:

T | undefined

Edit this section

## useSignal

Hook that creates a signal that is retained for the lifetime of the component.

```
useSignal: UseSignal;
```

Edit this section

## UseSignal

Hook that creates a signal that is retained for the lifetime of the component.

```
useSignal: UseSignal;
```

Edit this section

## useStore

Creates an object that Qwik can track across serializations.

Use useStore to create a state for your application. The returned object is a proxy that has a unique ID. The ID of the object is used in the QRLs to refer to the store.

### Example

Example showing how useStore is used in Counter example to keep track of the count.

```
const Stores = component$(() => {
  const counter = useCounter(1);
 
  // Reactivity happens even for nested objects and arrays
  const userData = useStore({
    name: "Manu",
    address: {
      address: "",
      city: "",
    },
    orgs: [],
  });
 
  // useStore() can also accept a function to calculate the initial value
  const state = useStore(() => {
    return {
      value: expensiveInitialValue(),
    };
  });
 
  return (
    <div>
      <div>Counter: {counter.value}</div>
      <Child userData={userData} state={state} />
    </div>
  );
});
 
function useCounter(step: number) {
  // Multiple stores can be created in custom hooks for convenience and composability
  const counterStore = useStore({
    value: 0,
  });
  useVisibleTask$(() => {
    // Only runs in the client
    const timer = setInterval(() => {
      counterStore.value += step;
    }, 500);
    return () => {
      clearInterval(timer);
    };
  });
  return counterStore;
}
```

```
useStore: <STATE extends object>(
  initialState: STATE | (() => STATE),
  opts?: UseStoreOptions,
) => STATE;
```

Parameter

Type

Description

initialState

STATE | (() => STATE)

opts

UseStoreOptions

(Optional)

Returns:

STATE

Edit this section

## UseStoreOptions

```
export interface UseStoreOptions
```

Property

Modifiers

Type

Description

deep?

boolean

(Optional) If true then all nested objects and arrays will be tracked as well. Default is true.

reactive?

boolean

(Optional) If false then the object will not be tracked for changes. Default is true.

Edit this section

## useStyles$

A lazy-loadable reference to a component's styles.

Component styles allow Qwik to lazy load the style information for the component only when needed. (And avoid double loading it in case of SSR hydration.)

```
import styles from "./code-block.css?inline";
 
export const CmpStyles = component$(() => {
  useStyles$(styles);
 
  return <div>Some text</div>;
});
```

```
useStyles$: (qrl: string) => void
```

Parameter

Type

Description

qrl

string

Returns:

void

Edit this section

## useStylesQrl

A lazy-loadable reference to a component's styles.

Component styles allow Qwik to lazy load the style information for the component only when needed. (And avoid double loading it in case of SSR hydration.)

```
import styles from "./code-block.css?inline";
 
export const CmpStyles = component$(() => {
  useStyles$(styles);
 
  return <div>Some text</div>;
});
```

```
useStylesQrl: (styles: QRL<string>) => void
```

Parameter

Type

Description

styles

QRL<string>

Returns:

void

Edit this section

## UseStylesScoped

```
export interface UseStylesScoped
```

Property

Modifiers

Type

Description

scopeId

string

Edit this section

## useStylesScoped$

A lazy-loadable reference to a component's styles, that is scoped to the component.

Component styles allow Qwik to lazy load the style information for the component only when needed. (And avoid double loading it in case of SSR hydration.)

```
import scoped from "./code-block.css?inline";
 
export const CmpScopedStyles = component$(() => {
  useStylesScoped$(scoped);
 
  return <div>Some text</div>;
});
```

```
useStylesScoped$: (qrl: string) => UseStylesScoped;
```

Parameter

Type

Description

qrl

string

Returns:

UseStylesScoped

Edit this section

## useStylesScopedQrl

A lazy-loadable reference to a component's styles, that is scoped to the component.

Component styles allow Qwik to lazy load the style information for the component only when needed. (And avoid double loading it in case of SSR hydration.)

```
import scoped from "./code-block.css?inline";
 
export const CmpScopedStyles = component$(() => {
  useStylesScoped$(scoped);
 
  return <div>Some text</div>;
});
```

```
useStylesScopedQrl: (styles: QRL<string>) => UseStylesScoped;
```

Parameter

Type

Description

styles

QRL<string>

Returns:

UseStylesScoped

Edit this section

## useTask$

Reruns the taskFn when the observed inputs change.

Use useTask to observe changes on a set of inputs, and then re-execute the taskFn when those inputs change.

The taskFn only executes if the observed inputs change. To observe the inputs, use the obs function to wrap property reads. This creates subscriptions that will trigger the taskFn to rerun.

```
useTask$: (qrl: TaskFn, opts?: UseTaskOptions | undefined) => void
```

Parameter

Type

Description

qrl

TaskFn

opts

UseTaskOptions | undefined

(Optional)

Returns:

void

Edit this section

## UseTaskOptions

Warning: This API is now obsolete.

use useVisibleTask$ or useResource$, useTask$ is for running tasks as part of the initial SSR render

```
export interface UseTaskOptions
```

Property

Modifiers

Type

Description

eagerness?

EagernessOptions

(Optional) - visible: run the effect when the element is visible. - load: eagerly run the effect when the application resumes.

Edit this section

## useTaskQrl

Reruns the taskFn when the observed inputs change.

Use useTask to observe changes on a set of inputs, and then re-execute the taskFn when those inputs change.

The taskFn only executes if the observed inputs change. To observe the inputs, use the obs function to wrap property reads. This creates subscriptions that will trigger the taskFn to rerun.

```
useTaskQrl: (qrl: QRL<TaskFn>, opts?: UseTaskOptions) => void
```

Parameter

Type

Description

qrl

QRL<TaskFn>

opts

UseTaskOptions

(Optional)

Returns:

void

Edit this section

## useVisibleTask$

```
const Timer = component$(() => {
  const store = useStore({
    count: 0,
  });
 
  useVisibleTask$(() => {
    // Only runs in the client
    const timer = setInterval(() => {
      store.count++;
    }, 500);
    return () => {
      clearInterval(timer);
    };
  });
 
  return <div>{store.count}</div>;
});
```

```
useVisibleTask$: (qrl: TaskFn, opts?: OnVisibleTaskOptions | undefined) => void
```

Parameter

Type

Description

qrl

TaskFn

opts

OnVisibleTaskOptions | undefined

(Optional)

Returns:

void

Edit this section

## useVisibleTaskQrl

```
const Timer = component$(() => {
  const store = useStore({
    count: 0,
  });
 
  useVisibleTask$(() => {
    // Only runs in the client
    const timer = setInterval(() => {
      store.count++;
    }, 500);
    return () => {
      clearInterval(timer);
    };
  });
 
  return <div>{store.count}</div>;
});
```

```
useVisibleTaskQrl: (qrl: QRL<TaskFn>, opts?: OnVisibleTaskOptions) => void
```

Parameter

Type

Description

qrl

QRL<TaskFn>

opts

OnVisibleTaskOptions

(Optional)

Returns:

void

Edit this section

## ValueOrPromise

Type representing a value which is either resolve or a promise.

```
export type ValueOrPromise<T> = T | Promise<T>;
```

Edit this section

## version

QWIK_VERSION

```
version: string;
```

Edit this section

## VideoHTMLAttributes

```
export interface VideoHTMLAttributes<T extends Element> extends Attrs<'video', T>
```

Extends: Attrs<'video', T>

Edit this section

## VisibleTaskStrategy

```
export type VisibleTaskStrategy =
  | "intersection-observer"
  | "document-ready"
  | "document-idle";
```

Edit this section

## WebViewHTMLAttributes

Warning: This API is now obsolete.

This is the type for a React Native WebView. It doesn't belong in Qwik (yet?) but we're keeping it for backwards compatibility.

```
export interface WebViewHTMLAttributes<T extends Element> extends HTMLAttributes<T>
```

Extends: HTMLAttributes<T>

Property

Modifiers

Type

Description

allowFullScreen?

boolean | undefined

(Optional)

allowpopups?

boolean | undefined

(Optional)

autoFocus?

boolean | undefined

(Optional)

autosize?

boolean | undefined

(Optional)

blinkfeatures?

string | undefined

(Optional)

disableblinkfeatures?

string | undefined

(Optional)

disableguestresize?

boolean | undefined

(Optional)

disablewebsecurity?

boolean | undefined

(Optional)

guestinstance?

string | undefined

(Optional)

httpreferrer?

string | undefined

(Optional)

nodeintegration?

boolean | undefined

(Optional)

partition?

string | undefined

(Optional)

plugins?

boolean | undefined

(Optional)

preload?

string | undefined

(Optional)

src?

string | undefined

(Optional)

useragent?

string | undefined

(Optional)

webpreferences?

string | undefined

(Optional)

Edit this section
