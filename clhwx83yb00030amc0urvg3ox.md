---
title: "Understanding core Redux with React JS"
seoTitle: "Understanding core Redux with React JS"
seoDescription: "This is the first blog about the Redux. In this article we will deep dive into this topic after reading this you will have a basic understanding redux."
datePublished: Sun May 21 2023 04:31:09 GMT+0000 (Coordinated Universal Time)
cuid: clhwx83yb00030amc0urvg3ox
slug: understanding-core-redux-with-react-js
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684459847554/a3840619-0a30-477f-93c7-93c4e2bfe402.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684643413846/cb9769b4-97fa-4c66-8881-b4999119e344.png
tags: reactjs, redux, tailwind-css

---

This is the first blog about the Redux. In this article we will deep dive into this topic after reading this you will have a basic understanding of how redux works and why we need to use this library.

Redux is used to centralize the data. It is not a ReactJS-specific thing it can also use with another framework like Angular or Vue. There are also other tools for state management in React but Redux is the most popular tool for this. It separates the state code from reactJS logic.

### **Setup a ReactJS project with Redux**

here are some steps for creating the react project with redux.

### 1\. Create a react app with Vite builder

```javascript
npm init vite@latest React-Redux-Setup -- --template react-ts
```

### **2\. Go to the newly created folder**

here is the command for navigating to the folder

```javascript
cd React-Redux-Setup
```

### 3\. Install the redux and react-redux library

```javascript
npm install redux react-redux
```

### 4\. Now run the web App

```javascript
npm run dev
```

### Creating a simple Increment Decrement App

First, we have to set up a Redux store in our app. so we need to create an initial state that contains the number as a key initially it is zero.

store.ts

```javascript
import { Action, createStore } from "redux";

type initialState = {
  number: number;
};

const initialState: initialState = {
  number: 0,
};

function reducer(state = initialState, action: Action) {
  switch (action.type) {
    case INCREMENT:
      return { ...state, number: state.number + 1 };
    case DECREMENT:
      return { ...state, number: state.number - 1 };
    default:
      return state;
  }
}

export const store = createStore(reducer);
```

here I have created a redux store. the initial state of the number is 0. and a reducer that takes action and according to their type makes some changes in state. the store is exported from this file and we will use this on main.ts to provide the store to the whole web app.

main.ts

In the main file, we have to provide the store access to the whole ReactJS app.

```javascript
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.tsx";
import "./index.css";
import { Provider } from "react-redux";
import { store } from './../Redux/store.ts'

ReactDOM.createRoot(document.getElementById("root") as HTMLElement).render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
  </React.StrictMode>
);
```

now our react app has access to the redux store.

now we need some action to make changes in the redux store. action is the function that takes the payload in a parameter and returns an object of two key-like types and payload.

```javascript
export const INCREMENT = "INCREMENT";
export const DECREMENT = "DECREMENT";

export const incrementAction = ()=>({ type : INCREMENT })
export const decrementAction = ()=>({ type : DECREMENT })
```

here are our two actions like incrementAction and decrementAction. For anything to change something in a redux store, we have to create a redux action.

**UI Part**

```javascript
import { useDispatch } from "react-redux";
import "./App.css";
import {
  decrementAction,
  incrementAction,
} from "../Redux/Actions/IncrementDecrement";

function App() {
  const dispatch = useDispatch();

  return (
    <div className="h-screen flex flex-col justify-center items-center ">
      <div className="text-3xl mb-4">0</div>
      <div className="flex gap-2">
        <button
          onClick={() => dispatch(incrementAction())}
          className="px-4 py-1 rounded-md text-white bg-indigo-800 hover:bg-indigo-500 "
        >
          Increment
        </button>
        <button
          onClick={() => dispatch(decrementAction())}
          className="px-4 py-1 rounded-md text-white bg-red-800 hover:bg-red-500 "
        >
          Decrement
        </button>
      </div>
    </div>
  );
}

export default App;
```

In this react component there are two buttons Increment and Decrement and a number. Initially, the number is zero but we will change it by dispatching the action.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684635343849/61373509-60d5-4bf7-b79b-98ae50c2b432.png align="center")

Now on clicking the button state is changing for getting the state value we need to create selectors.

for selecting the value of a number we have a selector stateSelector.ts.

```javascript
import { State } from "./../store";

export function numberValueSelector(state: State) {
  return state.number;
}
```

Now we can get the value of this number state in our UI component.

```javascript
import { useDispatch, useSelector } from "react-redux";
import "./App.css";
import {
  decrementAction,
  incrementAction,
} from "../Redux/Actions/IncrementDecrement";
import { numberValueSelector } from './../Redux/selector/stateSelector'

function App() {
  const dispatch = useDispatch();
  const value = useSelector(numberValueSelector);

  return (
    <div className="h-screen flex flex-col justify-center items-center ">
      <div className="text-3xl mb-4">{value}</div>
      <div className="flex gap-2">
        <button
          onClick={() => dispatch(incrementAction())}
          className="px-4 py-1 rounded-md text-white bg-indigo-800 hover:bg-indigo-500 "
        >
          Increment
        </button>
        <button
          onClick={() => dispatch(decrementAction())}
          className="px-4 py-1 rounded-md text-white bg-red-800 hover:bg-red-500 "
        >
          Decrement
        </button>
      </div>
    </div>
  );
}

export default App;
```

Here is the final form of this app. You can track the state changes and sequence of action dispatch in redux-dev tools just install the redux-dev tool extension.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684643323384/8b08b439-84fc-4813-a6d9-f5b375b0f08e.png align="center")

I hope if you are following this article now you have got a good idea of **Redux** with **ReactJS. 💕💕**Thank you for reading this article and please share your valuable comment in the comments.