---
title: "Optimizing performance in React apps"
datePublished: Thu Mar 30 2023 15:59:08 GMT+0000 (Coordinated Universal Time)
cuid: clfvawklb00040ajx681a42a0
slug: optimizing-performance-in-react-apps
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/UYsBCu9RP3Y/upload/06eed6cdaada9ea0d821b76cbc93be3e.jpeg
tags: reactjs, clean-code, react-hooks, optimize

---

Here I want to share how can we make a more **optimize React js** web app. Here are some methods to make your code clean and make it faster.

Improving the code is a very important process you need good knowledge about that technology to improve that code. **Optimization** makes code faster and easy to read. A coder should always remember is their mind the code that he is writing it will be read and used by many other people so be careful when writing the code.

**React** is a **frontend library** it gives a lot of freedom in code. It makes a very high risk to make code Dirty. React gives many tools to optimize web apps.

In React library components rerender many times in their [lifecycle](https://www.w3schools.com/react/react_lifecycle.asp#:~:text=Each%20component%20in%20React%20has,Mounting%2C%20Updating%2C%20and%20Unmounting.). A programmer needs to control this unnecessary re-rendering. It makes it very costly not to take control of it.

**Tools to optimize the React code are Like :**

1. [useEffect Hook](https://react.dev/reference/react/useEffect#reference): useEffect is a hook provided by the React library to control the unusual rerendering of components. useEffect is also used to run some code in mounting, unmounting or after a change in data. Here is an example given below in this code snippet there is a **useEffect** Hook with empty dependency. This useEffect will run only after mounting the component and before unmounting the component.
    
    ```typescript
    useEffect(() => {
        console.log("This line will execute after the Mounting the Component");
        return () => {
          console.log("This line will execute Befor the Unmounteing the Component");
        };
      }, []);
    ```
    
2. **MEMO HOC:** Memo is a HOC to control unnecessary rerendering of a [pure component](https://react.dev/reference/react/PureComponent). It is capable to rerender a component when props get changed for that component. It gets memoized the output of the component and returns the same output until the props got changed.
    
    ```typescript
    import React, { memo } from 'react';
    
    // A simple functional component that displays a greeting
    function Greeting(props) {
      console.log('Rendering Greeting');
      return (
        <div>
          <h1>Hello, {props.name}!</h1>
        </div>
      );
    }
    
    // Wrap the component with memo
    const MemoizedGreeting = memo(Greeting);
    
    // Example usage:
    function App() {
      const [name, setName] = useState('John');
    
      return (
        <div>
          <input value={name} onChange={e => setName(e.target.value)} />
          <MemoizedGreeting name={name} />
        </div>
      );
    }
    
    export default App;
    ```
    
    <details data-node-type="hn-details-summary"><summary>Warning: Do not use memo in impure components it will affect your component's usual rendering.</summary><div data-type="detailsContent"></div></details>
3. **useMemo hook**: It is a hook used to save some calculations in the code. Sometimes we have some large calculations which can make our code slow that are recalculating again and again during every rerender to solve this type of problem we use the useMemo hook which can memoize the output of that large calculation and return it after every rerender.
    
    we can also set dependencies for the useMemo so that when these **dependencies** get changed the code will rerun and will return the latest output.
    
    ```typescript
    import React, { useMemo, useState } from 'react';
    
    // A simple functional component that sums two numbers
    function Calculator(props) {
      const [num1, setNum1] = useState(0);
      const [num2, setNum2] = useState(0);
    
      // Memoize the sum calculation based on the input props and num1 state
      const sum = useMemo(() => {
        console.log('Calculating sum...');
        return num1 + props.inputNum;
      }, [props.inputNum, num1]);
    
      return (
        <div>
          <input value={num1} onChange={e => setNum1(Number(e.target.value))} />
          <input value={num2} onChange={e => setNum2(Number(e.target.value))} />
    
          <p>The sum is: {sum}</p>
        </div>
      );
    }
    
    // Example usage:
    function App() {
      const [inputNum, setInputNum] = useState(0);
    
      return (
        <div>
          <input value={inputNum} onChange={e => setInputNum(Number(e.target.value))} />
          <Calculator inputNum={inputNum} />
        </div>
      );
    }
    
    export default App;
    ```
    
    In the above example, we have a simple functional component called `Calculator`, which takes an input prop `inputNum` and two state variables `num1` and `num2`. It renders the sum of `num1` and `inputNum`.
    
    We use the `useMemo` hook to memoize the sum calculation based on changes in `num1` or `inputNum`. This ensures that the sum calculation is only re-performed when necessary.
    
4. **useCallback hook**: It is used to solve a problem if we want to pass a function in props and we are using memo in the child component then every rerender will recreate that function and the child component will act like it is getting new props and it will get rerender.+
    
    ```typescript
    import React, { useState, useCallback } from 'react';
    
    function ExampleComponent() {
      const [count, setCount] = useState(0);
    
      // Define a memoized increment function using useCallback and the count dependency
      const increment = useCallback(() => {
        setCount(count + 1);
      }, [count]);
    
      return (
        <div>
          <p>Count: {count}</p>
          <button onClick={increment}>Increment</button>
        </div>
      );
    }
    ```
    
    In the above example, the `increment` function is memoized using `useCallback`. It only takes in one dependency, which is `count`. This means that `increment` will only be re-created if `count` changes, which can improve performance.
    

I hope these things will help you a lot.

Thank you😃