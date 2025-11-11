# React Hooks Interview Questions and Answers

| #   | Question                                                                                                                   |
| --- | -------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are Hooks in React?](#what-are-hooks-in-react)                                                                       |
| 2   | [What are the different types of hooks?](#what-are-the-different-types-of-hooks)                                           |
| 3   | [What is the difference between `useState()` and `useReducer()`?](#what-is-the-difference-between-usestate-and-usereducer) |
| 4   | [Explain `useEffect()` hook in react?](#explain-useeffect-hook-in-react)                                                   |
| 5   | [How does `useLayoutEffect()` differ from `useEffect()`?](#how-does-uselayouteffect-differ-from-useeffect)                 |
|     | []()                                                                                                                       |

---

## What are Hooks in React?

In React, Hooks are special functions introduced in `React 16.8` that allow functional components to have state management, use lifecycle methods, and access other React features previously only available in class components. They were introduced to simplify code, improve performance, reusability, and provide a cleaner alternative to class components.

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

---

## What is the difference between `useState()` and `useReducer()`?

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

---

## Explain `useEffect()` hook in react?

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

---

## How does `useLayoutEffect()` differ from `useEffect()`?

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

---
