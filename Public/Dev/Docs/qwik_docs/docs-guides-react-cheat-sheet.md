# https://qwik.dev/docs/guides/react-cheat-sheet/

[Original link](https://qwik.dev/docs/guides/react-cheat-sheet/)

# React Vs Qwik

Several examples comparing React and Qwik.

## Hello world component

### ⚛️ From React

```
export const HelloWorld = () => {
  return <div>Hello world</div>;
}
```

### ⚡️ To Qwik

```
export const HelloWorld = component$(() => {
  return <div>Hello world</div>;
});
```

component$ is used to declare a Qwik component.

The dollar sign $ is used to signal both the optimizer and the developer when Qwik splits up your application into many small pieces we call symbols.

## Button with a click handler

### ⚛️ From React

```
export const Button = () => {
  return <button onClick={() => console.log('click')}>Click me</button>;
}
```

### ⚡️ To Qwik

```
export const Button = component$(() => {
  return <button onClick$={() => console.log('click')}>Click me</button>;
});
```

Event handlers in qwik behave in the same way as in other frameworks, you just have to keep in mind that their content will be loaded in a lazy way thanks to the dollar suffix.

Attention ⚠️: JSX handlers such as onClick$ and onInput$ are only executed on the client. This is because they are DOM events, since there is no DOM on the server, they will not be executed on the server.

## Declare local state

### ⚛️ From React

```
export function UseStateExample() {
  const [value, setValue] = useState(0);
  return <div>Value is: {value}</div>;
}
```

### ⚡️ To Qwik

```
export const LocalStateExample = component$(() => {
  const count = useSignal(0);
  return <div>Value is: {count.value}</div>;
});
```

useStore() Works very similarly to useSignal(), but it takes an object as its initial value and the reactivity extends to nested objects and arrays by default. One can think of a store as a multiple-value signal or an object made of several signals.

## Create a counter component

### ⚛️ From React

```
export function Counter() {
  const [count, setCount] = useState(0);
  return (
    <>
      <p>Value is: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </>
  );
}
```

### ⚡️ To Qwik

```
export const Counter = component$(() => {
  const count = useSignal(0);
  return (
    <>
      <p>Value is: {count.value}</p>
      <button onClick$={() => count.value++}>Increment</button>
    </>
  );
});
```

## Using Props

### ⚛️ From React

```
export const Parent = (() => {
  const [ count, setCount ] = useState<number>(0);
 
  const increment = (() => {
    setCount((prev) => prev + 1)
  })
  return <Child count={count} increment={increment} />;
})
 
interface ChildProps {
  count: number;
  increment: () => void;
}
 
export const Child = ((props: ChildProps) => {
  return (
    <>
      <button onClick={props.increment}>Increment</button>
      <p>Count: {props.count}</p>
    </>
  );
})
```

### ⚡️ To Qwik

```
export const Parent = component$(() => {
  const userData = useStore({ count: 0 });
  return <Child userData={userData} />;
});
 
interface ChildProps {
  userData: { count: number };
}
 
export const Child = component$<ChildProps>(({ userData }) => {
  return (
    <>
      <button onClick$={() => userData.count++}>Increment</button>
      <p>Count: {userData.count}</p>
    </>
  );
});
```

The reactive signal returned by useSignal() consists of an object with a single property .value. If you change the value property of the signal, any component that depends on it will be updated automatically.

## Create a clock that increments every second

### ⚛️ From React

```
export function Clock() {
  const [seconds, setSeconds] = useState(0);
  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds(seconds + 1);
    }, 1000);
    return () => clearInterval(interval);
  });
  return <p>Seconds: {seconds}</p>;
}
```

### ⚡️ To Qwik

```
export const Clock = component$(() => {
  const seconds = useSignal(0);
  useVisibleTask$(({ cleanup }) => {
    const interval = setInterval(() => {
      seconds.value++;
    }, 1000);
    cleanup(() => clearInterval(interval));
  });
 
  return <p>Seconds: {seconds.value}</p>;
});
```

## Perform a fetch request every time the state changes

### ⚛️ From React

```
export function Fetch() {
  const [url, setUrl] = useState('https://api.github.com/repos/QwikDev/qwik');
  const [responseJson, setResponseJson] = useState(undefined);
 
  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then((json) => setResponseJson(json));
  }, [url]);
 
  return (
    <>
      <p>{responseJson?.name} has {responseJson?.stargazers_count} ✨'s</p>
      <input name="url" value={url} onChange={(e) => setUrl(e.target.value)} />
    </>
  );
}
```

### ⚡️ To Qwik

```
export const Fetch = component$(() => {
  const url = useSignal('https://api.github.com/repos/QwikDev/qwik');
  const responseJson = useSignal(undefined);
 
  useTask$(async ({ track }) => {
    track(() => url.value);
    const res = await fetch(url.value);
    const json = await res.json();
    responseJson.value = json;
  });
 
  return (
    <>
      <p>{responseJson.value?.name} has {responseJson.value?.stargazers_count} ✨'s</p>
      <input name="url" bind:value={url} />
    </>
  );
});
```

useTask$() registers a hook to be executed upon component creation, it will run at least once either in the server or in the browser, depending on where the component is initially rendered.

bind attribute is a convenient API to two-way data bind the value of an input to a Signal.

## Declare some context and consume it

### ⚛️ From React

```
export const MyContext = createContext({ message: 'some example value' });
 
export default function Parent() {
  return (
    <MyContext.Provider value={{ message: 'updated example value' }}>
      <Child />
    </MyContext.Provider>
  );
}
 
export const Child = () => {
  const value = useContext(MyContext);
  return <p>{value.message}</p>;
};
```

### ⚡️ To Qwik

```
export const MyContext = createContextId('my-context');
 
export const Parent = component$(() => {
  const message = useSignal('some example value');
  useContextProvider(MyContext, message);
  return (
    <>
      <Child />
    </>
  );
});
 
export const Child = component$(() => {
  const message = useContext(MyContext);
  return <p>{message.value}</p>;
});
```

You simply need to create a context.

Just create the context in the component where you need to store the information and then, in its descendants, get the information through the corresponding ContextId.

## Create a debounced input

### ⚛️ From React

```
export const DebouncedInput = () => {
  const [value, setValue] = useState('');
  const [debouncedValue, setDebouncedValue] = useState(value);
 
  useEffect(() => {
    const debounced = setTimeout(() => setDebouncedValue(value), 1000);
    return () => clearTimeout(debounced);
  }, [value]);
 
  return (
    <>
      <input
        value={value}
        onChange={(ev) => setValue((ev.target as HTMLInputElement).value)}
      />
      <p>{debouncedValue}</p>
    </>
  );
};
```

### ⚡️ To Qwik

```
export const DebouncedInput = component$(() => {
  const inputText = useSignal('');
  const debouncedValue = useSignal('');
 
  useTask$(({ track, cleanup }) => {
    track(() => inputText.value);
 
    const debounced = setTimeout(() => {
      debouncedValue.value = inputText.value;
    }, 1000);
    cleanup(() => clearTimeout(debounced));
  });
 
  return (
    <>
      <input bind:value={inputText} />
      <p>{debouncedValue.value}</p>
    </>
  );
});
```

## Change background color randomly every button click

### ⚛️ From React

```
export function DynamicBackground() {
  const [red, setRed] = useState(0);
  const [green, setGreen] = useState(0);
  const [blue, setBlue] = useState(0);
  return (
    <div
      style={{
        background: `rgb(${red}, ${green}, ${blue})`,
      }}
    >
      <button
        onClick={() => {
          setRed(Math.random() * 256);
          setGreen(Math.random() * 256);
          setBlue(Math.random() * 256);
        }}
      >
        Change background
      </button>
    </div>
  );
}
```

### ⚡️ To Qwik

```
export const DynamicBackground = component$(() => {
  const red = useSignal(0);
  const green = useSignal(0);
  const blue = useSignal(0);
 
  return (
    <div
      style={{
        background: `rgb(${red.value}, ${green.value}, ${blue.value})`,
      }}
    >
      <button
        onClick$={() => {
          red.value = Math.random() * 256;
          green.value = Math.random() * 256;
          blue.value = Math.random() * 256;
        }}
      >
        Change background
      </button>
    </div>
  );
});
```

## Create a component that renders a list of the presidents

### ⚛️ From React

```
export function Presidents() {
  const presidents = [
    { name: 'George Washington', years: '1789-1797' },
    { name: 'John Adams', years: '1797-1801' },
    { name: 'Thomas Jefferson', years: '1801-1809' },
    { name: 'James Madison', years: '1809-1817' },
    { name: 'James Monroe', years: '1817-1825' },
    { name: 'John Quincy Adams', years: '1825-1829' },
    { name: 'Andrew Jackson', years: '1829-1837' },
    { name: 'Martin Van Buren', years: '1837-1841' },
    { name: 'William Henry Harrison', years: '1841-1841' },
    { name: 'John Tyler', years: '1841-1845' },
    { name: 'James K. Polk', years: '1845-1849' },
    { name: 'Zachary Taylor', years: '1849-1850' },
    { name: 'Millard Fillmore', years: '1850-1853' },
    { name: 'Franklin Pierce', years: '1853-1857' },
    { name: 'James Buchanan', years: '1857-1861' },
    { name: 'Abraham Lincoln', years: '1861-1865' },
    { name: 'Andrew Johnson', years: '1865-1869' },
    { name: 'Ulysses S. Grant', years: '1869-1877' },
    { name: 'Rutherford B. Hayes', years: '1877-1881' },
    { name: 'James A. Garfield', years: '1881-1881' },
    { name: 'Chester A. Arthur', years: '1881-1885' },
    { name: 'Grover Cleveland', years: '1885-1889' },
  ];
  return (
    <ul>
      {presidents.map((president) => (
        <li key={president.name + president.years}>
          {president.name} ({president.years})
        </li>
      ))}
    </ul>
  );
}
```

### ⚡️ To Qwik

```
export const Presidents = component$(() => {
  const presidents = [
    { name: 'George Washington', years: '1789-1797' },
    { name: 'John Adams', years: '1797-1801' },
    { name: 'Thomas Jefferson', years: '1801-1809' },
    { name: 'James Madison', years: '1809-1817' },
    { name: 'James Monroe', years: '1817-1825' },
    { name: 'John Quincy Adams', years: '1825-1829' },
    { name: 'Andrew Jackson', years: '1829-1837' },
    { name: 'Martin Van Buren', years: '1837-1841' },
    { name: 'William Henry Harrison', years: '1841-1841' },
    { name: 'John Tyler', years: '1841-1845' },
    { name: 'James K. Polk', years: '1845-1849' },
    { name: 'Zachary Taylor', years: '1849-1850' },
    { name: 'Millard Fillmore', years: '1850-1853' },
    { name: 'Franklin Pierce', years: '1853-1857' },
    { name: 'James Buchanan', years: '1857-1861' },
    { name: 'Abraham Lincoln', years: '1861-1865' },
    { name: 'Andrew Johnson', years: '1865-1869' },
    { name: 'Ulysses S. Grant', years: '1869-1877' },
    { name: 'Rutherford B. Hayes', years: '1877-1881' },
    { name: 'James A. Garfield', years: '1881-1881' },
    { name: 'Chester A. Arthur', years: '1881-1885' },
    { name: 'Grover Cleveland', years: '1885-1889' },
  ];
  return (
    <ul>
      {presidents.map((president) => (
        <li key={president.name + president.years}>
          {president.name} ({president.years})
        </li>
      ))}
    </ul>
  );
});
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
