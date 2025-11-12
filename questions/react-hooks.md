# React Hooks Interview Questions and Answers

| #   | Question                                                                                                               |
| --- | ---------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are Hooks in React?](#what-are-hooks-in-react)                                                                   |
| 2   | [What are the different types of hooks?](#what-are-the-different-types-of-hooks)                                       |
| 3   | [What is the difference between useState() and useReducer()?](#what-is-the-difference-between-usestate-and-usereducer) |
| 4   | [Explain useEffect() hook in react?](#explain-useeffect-hook-in-react)                                                 |
| 5   | [How does useLayoutEffect() differ from useEffect()?](#how-does-uselayouteffect-differ-from-useeffect)                 |
| 6   | [Explain difference between useCallback() and useMemo()?](#explain-difference-between-usecallback-and-usememo)         |
| 7   | [Explain Context API in React?](#explain-context-api-in-react)                                                         |
| 8   | [How useRef() is helpful in React? Explain with an example.](#how-useref-is-helpful-in-react-explain-with-an-example)  |
| 8   | [What makes useImperativeHandle() differ from useRef()?](#what-makes-useimperativehandle-differ-from-useref)           |
| 9   | [Explain working of useTransition()?](#explain-working-of-usetransition)                                               |

---

## What are Hooks in React?

In React, Hooks are special functions introduced in `React 16.8` that allow functional components to have state management, use lifecycle methods, and access other React features previously only available in class components. They were introduced to simplify code, improve performance, reusability, and provide a cleaner alternative to class components.

[⬆️Go to top](#react-hooks-interview-questions-and-answers)

---

## What are the different types of hooks?

**State Hooks**:

- `useState()` - Declares a state variable that can update directly with a setter function.
- `useReducer()` - Declares a state variable with the update logic inside a reducer function triggers it on dispatching actions.

**Context Hooks**:

- `useContext()` - Creates a global context that lets components receive information from distant parent without passing it as props.

**Reference Hook**:

- `useRef()` - Provides a mutable reference that persist across renders without causing re-rendering the component.
- `useImperativeHandle()` - Allows a child component to customize the instance value that is exposed to a parent component when using a ref.

**Effeact Hooks**:

- `useEffect()` - Allows components to have side effects or connect with external systems. Provide life cycle features.
- `useLayoutEffect()` - Similar to useEffect(), but it execute the callback before the browser repaints the screen.
- `useInsertionEffect()` - Execute the callback before React makes changes to the DOM. Libraries can insert dynamic CSS here.

**Performance Hooks**:

- `useCallback()` - Allows to cache the function definition (function instance) before passing it down to an optimized component.
- `useMemo()` - Allow to cache the result of expensive calculation.
- `useTransition()` - Mark a state transition as non-blocking and allow other updates to interrupt it.
- `useDeferredValue()` - Defer updating a non-critical part of the UI and let other parts update first.

**Other Hooks**:

- `useDebugValue()` - Customize the label React DevTools displays for your custom Hook.
- `useId()` - Lets a component associate a unique ID with itself. Typically used with accessibility APIs.
- `useSyncExternalStore()` - Lets a component subscribe to an external store.
- `useActionState()` - Allows you to manage state of actions.

[⬆️Go to top](#react-hooks-interview-questions-and-answers)

---

## What is the difference between useState() and useReducer()?

Both React Hooks used for managing state in functional components, but they are designed for different levels of complexity and offer distinct advantages.

**useState()**:

- Allows a component to have internal state and can directly update it.
- Returns an array with 2 values, a state variable and a direct setter function to update its value.
- Accepts an optional initialState as arguemnt.

  ```javascript
  const [state, setterFunction] = useState(initialValue);
  ```

**useReducer()**:

- An alternativve to `useState`, handles complex state logic especially when state involve multiple related values, or require a specific sequence of actions.
- It's often preferred when the next state depends on the previous state and an **action** that describes how the state should change.
- It takes a reducer function and an initial state, returning the current state and a dispatch function.

  ```javascript
  const [state, dispatch] = useReducer(reducer, initialState);
  ```

- **Reducer**: A function that takes current state and an action object and returns the new state.
- **Dispatch**: A function to sends actions to the reducer, which then calculates and returns the new state.
- **Action**: An object that describes what to perform in a reducer. It has an type prperty and an optional payload.
- **initialState**: The initial value for your state.

| Key difference               | `useState`                                | `useReducer`                                                         |
| ---------------------------- | ----------------------------------------- | -------------------------------------------------------------------- |
| Complexity                   | Best for simple, local state              | Suited for complex or related state logic                            |
| API                          | Returns [state, setState] (direct setter) | Returns [state, dispatch]; updates via actions and reducer           |
| State logic                  | Updates performed directly in component   | Centralized update logic inside a reducer function                   |
| Predictability & scalability | Less structured for large/complex flows   | More predictable, testable and scalable for complex state management |

[⬆️Go to top](#react-hooks-interview-questions-and-answers)

---

## Explain useEffect() hook in react?

- The `useEffect` Hook is used to perform side effects such as data fetching, directly manipulating the DOM, setting up subscriptions, or working with timers.
- It performs life-cycle features (`componentDidMount`, `componentDidUpdate` and `componentWillUnmount`) in functional components, which was before available only with in class components.

`useEffect()` takes 2 arguments:

1. **A callback function (the effect)**: This function contains the logic for your side effect.

2. **An optional array of dependencies**: This array controls when the effect should re-run.

   - **No dependency array**: The effect runs after every render.
   - **Empty dependency array ([])**: The effect runs only once after the initial render (like `componentDidMount`) and the cleanup function (if returned) runs when the component unmounts (like `componentWillUnmount`).
   - **Array with dependencies**: The effect runs after the initial render and whenever any of the values in the dependency array change between renders.

3. **Cleanup Functions**: performs cleaning up resources (e.g., clearing timers, unsubscribing from events), by return a function from effect's callback. This cleanup function will be executed before the component unmounts or before the effect runs again due to a dependency change.

```javascript
useEffect(() => {
  // Perform side effects here
  return () => {
    // Optional cleanup function
  };
}, [dependency1, dependency2]);
```

[⬆️Go to top](#react-hooks-interview-questions-and-answers)

---

## How does useLayoutEffect() differ from useEffect()?

The `useLayoutEffect` is similar to `useEffect` but the difference lies in the timing of execution and blocking nature.

1. **Timing of Execution**:
   - The useEffect hook runs aynchronously after the browser has painted the updates to the screen. Means, the user sees the initial render before useEffect's callback is executed.
   - useLayoutEffect runs synchronosly after all DOM mutations are applied but before the browser has painted the updates to the screen.
2. **Blocking Nature**:
   - useEfect is non-blocking since it executes asynchronously after painting. So it does not delay the rendering process.
   - useLayoutEffect is blocking by nature. Because it runs synchronously before painting, it can potentially block the browser's rendering if the operations inside are computationally intensive, leading to perceived performance issues or "jank".

In essence, use `useEffect` for most side effects, and reserve `useLayoutEffect` for situations where you need to perform DOM manipulations or measurements that must be applied and reflected in the layout before the user sees the painted content.

```javascript
useLayoutEffect(() => {
  // Perform side effects here
  return () => {
    // Optional cleanup function
  };
}, [dependency1, dependency2]);
```

- **Memoization**: The process of caching (memoizes) a function and its dependencies for future references and use.
- On subsequent render, React checks the current dependency values with the previous ones.

- **Referential Equality**: React's memoization mechanisms, such as `React.memo` for components and the dependency arrays in hooks like `useEffect`, `useMemo`, and `useCallback`, rely on referential equality. This means they compare the memory addresses of objects (including functions) to determine if they are "the same."

[⬆️Go to top](#react-hooks-interview-questions-and-answers)

---

## Explain difference between useCallback() and useMemo()?

`useCallback()` and `useMemo()` are both React Hooks that help optimize performance by memoizing values, but they serve different purposes.

| Hook                      | Returns                                | Purpose                                                                                                                                  | Syntax                                                                | Common use cases                                                                                                                           |
| ------------------------- | -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `useCallback(fn, [deps])` | A memoized function (stable reference) | Prevents creating a new function instance each render so child components receiving the function as a prop don't re-render unnecessarily | `const memoizedFn = useCallback(() => { /* ... */ }, [dep1, dep2]);`  | Passing callbacks to memoized children (with `React.memo`), using a function as a dependency in other hooks (`useEffect`, `useMemo`, etc.) |
| `useMemo(fn, [deps])`     | A memoized value (cached result)       | Caches the result of an expensive computation and recomputes only when dependencies change                                               | `const memoizedValue = useMemo(() => expensiveCalc(), [dep1, dep2]);` | Expensive calculations, deriving data for rendering, providing stable props/values to children                                             |

Notes:

- Key difference: `useCallback` memoizes the function reference; `useMemo` memoizes the value/result.
- Prefer not to use them prematurely—only apply when there's a measurable performance need.

[⬆️Go to top](#react-hooks-interview-questions-and-answers)

---

## Explain Context API in React?

Context API provides a way to pass data through the component tree without prop drilling. Use it for global concerns (theme, auth, locale) but avoid using it for very frequent updates (can cause many re-renders).

**Why use it**

- Eliminates passing props down many levels.
- Best for cross-cutting app state (theme, user, settings).

**Key Components of the Context API**

- **`createContext`**: This function is used to create a Context object. It can take an optional default value as an argument.
- **`Context.Provider`**: This component is used to provide the context value to its descendant components by wripping it.
- **`useContext`**: Hook used to consume the context value. It takes the Context object (created using `createContext()`) as an argument and returns the current context value.

**Minimal example (Theme)**

```javascript
import React, { createContext, useState, useContext, useMemo } from "react";

const ThemeContext = createContext({ theme: "light", setTheme: () => {} });

function App() {
  const [theme, setTheme] = useState("light");
  const value = useMemo(() => ({ theme, setTheme }), [theme]); // avoid unnecessary re-renders

  return (
    <ThemeContext.Provider value={value}>
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  return <ThemedButton />;
}

function ThemedButton() {
  const { theme, setTheme } = useContext(ThemeContext);
  return (
    <button
      onClick={() => setTheme((t) => (t === "light" ? "dark" : "light"))}
      style={{
        background: theme === "dark" ? "#333" : "#fff",
        color: theme === "dark" ? "#fff" : "#000",
      }}
    >
      Theme: {theme}
    </button>
  );
}
```

Tips

- Memoize provider value (useMemo) or handlers (useCallback) to reduce re-renders.
- Prefer local state when only a narrow subtree needs data.
- For complex state, combine Context with useReducer for predictable updates.

Short summary: Context = global-ish dependency injection for React components; use responsibly to avoid performance pitfalls.

[⬆️Go to top](#react-hooks-interview-questions-and-answers)

---

## How useRef() is helpful in React? Explain with an example.

- The `useRef()` hook in React is used to create a mutable reference that persists across component re-renders without causing the component to re-render.
- It returns a mutable object with a `current` property, which holds the referenced value.
- It is primarily used to access and interact with DOM elements directly, store mutable values, or keep a reference to a previous state without causing re-renders.

### Example:

```javascript
import React, { useRef } from "react";

function TextInputWithFocusButton() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus(); // Accessing the DOM node directly
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus the input</button>
    </div>
  );
}
```

In this example, `useRef()` is used to create a reference to the input element. When the button is clicked, the `focusInput` function is called, which uses the `current` property of the ref to focus the input field directly.

[⬆️Go to top](#react-hooks-interview-questions-and-answers)

---

## What makes useImperativeHandle() differ from useRef()?

`useImperativeHandle()` is a React Hook that customizes the instance value that is exposed to parent components when using `ref`. It is typically used in conjunction with `forwardRef` to allow a parent component to interact with a child component's methods or properties.

### How it works:

- When you use `useImperativeHandle`, you pass it a ref and a function that returns an object containing the values or methods you want to expose.
- This allows you to control what the parent component can access, providing a cleaner API for the child component.

### Common Use Cases:

1. **Exposing Methods**: When you want to expose specific methods of a child component to the parent, such as focusing an input or triggering animations.
2. **Encapsulating Logic**: To hide internal state or methods from the parent while still allowing controlled access to certain functionalities.
3. **Integrating with Third-Party Libraries**: When integrating with libraries that require direct manipulation of a component's instance.

### Example:

```javascript
import React, { useImperativeHandle, forwardRef, useRef } from "react";

const CustomInput = forwardRef((props, ref) => {
  const inputRef = useRef();

  useImperativeHandle(ref, () => ({
    focus: () => {
      inputRef.current.focus();
    },
    clear: () => {
      inputRef.current.value = "";
    },
  }));

  return <input ref={inputRef} type="text" />;
});

// Parent component
function Parent() {
  const inputRef = useRef();

  const handleFocus = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <CustomInput ref={inputRef} />
      <button onClick={handleFocus}>Focus Input</button>
    </div>
  );
}
```

In this example, `CustomInput` exposes `focus` and `clear` methods to the `Parent` component, allowing it to control the input field directly.

[⬆️Go to top](#react-hooks-interview-questions-and-answers)

---

## Explain working of useTransition()?

- The `useTransition` hook is used to manage state transitions in React applications, allowing you to mark certain updates as non-blocking.
- This means that while a transition is in progress, other updates can still occur, improving the user experience by keeping the interface responsive.

  **How it works:**

- `useTransition` returns an array containing a boolean indicating whether the transition is pending and a function to start the transition.
- You can wrap state updates that you want to be non-blocking in the transition function.

```javascript
import React, { useState, useTransition } from "react";

function App() {
  const [isPending, startTransition] = useTransition();
  const [inputValue, setInputValue] = useState("");
  const [list, setList] = useState([]);

  const handleChange = (e) => {
    const value = e.target.value;
    startTransition(() => {
      setInputValue(value);
      // Simulate a state update that might be expensive
      setList(Array.from({ length: 10000 }, (_, i) => `${value} ${i}`));
    });
  };

  return (
    <div>
      <input type="text" value={inputValue} onChange={handleChange} />
      {isPending && <span>Loading...</span>}
      <ul>
        {list.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
  );
}
```

### Use Case:

`useTransition` is particularly useful in scenarios where you have expensive state updates that could block the main thread, such as rendering large lists or performing complex calculations. By marking these updates as transitions, you can keep the UI responsive and provide feedback to users while the updates are being processed.

[⬆️Go to top](#react-hooks-interview-questions-and-answers)
