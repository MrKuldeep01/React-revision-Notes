# React js Notes with chatGPT [ Inermediate Level ]


[Basic level](/Readme.md)
[Advanced level](/Advanced.md)


#### Kuldeep : 

```
 Come on the Intermediate level & heading no. 9 : Hooks 
```
#### chatGPT : 

Got it! Let's dive into **Hooks** in React.

## 9. Hooks

Hooks are functions that let you use state and other React features in functional components. They were introduced in React 16.8 and allow you to use state and lifecycle methods without writing a class.

### Basic Hooks

1. **useState**
2. **useEffect**
3. **useContext**

### 1. useState

The `useState` hook lets you add state to functional components.

#### Example

```jsx
import React, { useState } from 'react';

function Counter() {
  // Declare a state variable named "count", and a function "setCount" to update it
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

export default Counter;
```

### 2. useEffect

The `useEffect` hook lets you perform side effects in function components. It's equivalent to `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` combined in class components.

#### Example

```jsx
import React, { useState, useEffect } from 'react';

function Timer() {
  const [count, setCount] = useState(0);

  // useEffect runs after the component renders
  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  }, [count]); // Only re-run the effect if count changes

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

export default Timer;
```

### 3. useContext

The `useContext` hook lets you subscribe to React context without introducing nesting.

#### Example

```jsx
import React, { useState, useContext, createContext } from 'react';

// Create a context
const CountContext = createContext();

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <CountContext.Provider value={{ count, setCount }}>
      <Child />
    </CountContext.Provider>
  );
}

function Child() {
  const { count, setCount } = useContext(CountContext);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}

export default Counter;
```

### Advanced Hooks

1. **useReducer**
2. **useCallback**
3. **useMemo**
4. **useRef**

### 1. useReducer

The `useReducer` hook is an alternative to `useState` for managing more complex state logic.

#### Example

```jsx
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>
        Increment
      </button>
      <button onClick={() => dispatch({ type: 'decrement' })}>
        Decrement
      </button>
    </div>
  );
}

export default Counter;
```

### 2. useCallback

The `useCallback` hook returns a memoized callback function that only changes if one of the dependencies has changed. It's useful for optimizing performance.

#### Example

```jsx
import React, { useState, useCallback } from 'react';

function ExpensiveComponent({ onClick }) {
  return <button onClick={onClick}>Click me</button>;
}

function Parent() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log('Button clicked');
  }, []);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <ExpensiveComponent onClick={handleClick} />
    </div>
  );
}

export default Parent;
```

### 3. useMemo

The `useMemo` hook returns a memoized value that only recomputes when one of the dependencies has changed. It's useful for optimizing performance.

#### Example

```jsx
import React, { useState, useMemo } from 'react';

function ExpensiveCalculation(count) {
  console.log('Calculating...');
  return count * 2;
}

function Counter() {
  const [count, setCount] = useState(0);

  const memoizedValue = useMemo(() => ExpensiveCalculation(count), [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <p>Calculation: {memoizedValue}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default Counter;
```

### 4. useRef

The `useRef` hook returns a mutable ref object whose `.current` property is initialized to the passed argument. It's useful for accessing and modifying DOM elements directly.

#### Example

```jsx
import React, { useRef } from 'react';

function FocusInput() {
  const inputRef = useRef(null);

  const handleClick = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={handleClick}>Focus the input</button>
    </div>
  );
}

export default FocusInput;
```

### Summary

- **useState**: Adds state to functional components.
- **useEffect**: Performs side effects in functional components.
- **useContext**: Subscribes to React context without nesting.
- **useReducer**: Manages complex state logic.
- **useCallback**: Returns a memoized callback function.
- **useMemo**: Returns a memoized value.
- **useRef**: Accesses and modifies DOM elements directly.

Feel free to ask if you have any questions or need further clarification on any of these hooks!









[Basic level](/Readme.md)

[Advanced level](/Advanced.md)
