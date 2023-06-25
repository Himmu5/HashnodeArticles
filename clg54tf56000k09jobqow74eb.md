---
title: "Managing State in React Js: Where to Start as a Beginner?"
datePublished: Thu Apr 06 2023 13:06:25 GMT+0000 (Coordinated Universal Time)
cuid: clg54tf56000k09jobqow74eb
slug: managing-state-in-react-js-where-to-start-as-a-beginner
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/XJXWbfSo2f0/upload/629690c13f9a8ffe76f6b333d1c473b1.jpeg
tags: reactjs, frontend-development, state-management, replay

---

Managing the state in React is quite different from a normal Javascript project. In React every variable can not take effect on UI only the state variable can take effect. In React here is a concept of [Virtual Dom](https://legacy.reactjs.org/docs/faq-internals.html#:~:text=What%20is%20the%20Virtual%20DOM,This%20process%20is%20called%20reconciliation.) It compares an old state and a new state and then makes changes to the UI.

In the functional component, there are hooks to manage the state without hooks functional component is just a normal function. There are two main state hooks like **useState** and **useEffect** hook. Both two hooks are always present in a React web app.

React only supports unidirectional data flow so the state can't be passed from child to parent. Only we can pass a function to a child that can provide some data to the parent.

### State management tools

State management is very important when working on a big project. Always we should try to make a state structure that can be accessed from anywhere. The state should be centralized to make it easily accessible.

There are some good state management tools in javascript.

* **Context API**: Context is provided by React library to make the state centralized. It takes data in form of objects and provides the data in the whole web app.
    
    ```javascript
    import React, { createContext, useState } from 'react';
    
    // Create a context
    export const ThemeContext = createContext();
    
    // Create a provider component
    const ThemeProvider = ({ children }) => {
      const [darkTheme, setDarkTheme] = useState(false);
    
      const toggleTheme = () => {
        setDarkTheme(!darkTheme);
      }
    
      return (
        <ThemeContext.Provider value={{darkTheme, toggleTheme}}>
          {children}
        </ThemeContext.Provider>
      );
    };
    
    // Use context in a component
    const MyComponent = () => {
      const { darkTheme, toggleTheme } = useContext(ThemeContext);
    
      return (
        <div>
          <h1>{darkTheme ? 'Dark Theme' : 'Light Theme'}</h1>
          <button onClick={toggleTheme}>
            {darkTheme ? 'Switch to Light Theme' : 'Switch to Dark Theme'}
          </button>
        </div>
      );
    };
    
    // Usage in App component
    const App = () => {
      return (
        <ThemeProvider>
          <MyComponent />
        </ThemeProvider>
      );
    };
    ```
    
    In this example, a `ThemeContext` is created using `createContext()` and export from the file. A `ThemeProvider` component is created that encapsulates the logic for toggling between a dark and light theme. The `ThemeProvider` renders its children and passes the `darkTheme` and `toggleTheme` values to the `ThemeContext.Provider`.
    
    The `MyComponent` component uses the `useContext` hook to access the `darkTheme` and `toggleTheme` values from the `ThemeContext`. These values are used to render the current theme and a button to toggle between themes.
    
    Finally, the `App` component uses the `ThemeProvider` to wrap the `MyComponent` and provide access to the `ThemeContext`.
    
    **Context API** is good but it can't be used in a large project. It makes it hard to detect bugs and it is not predictable. We have some extra libraries to make it easy to find bugs and predict problems in components.
    
* **Redux Library**: Redux is a very powerful tool to manage the state in frontend. It comes with many features like it can predict which component has the bug. Bug finding is very easy using Redux.
    
    Redux makes the state centralized and makes bug fixing easy.
    
    To make a change in the state programmer need to create an action and give it to the reducer and the reducer actually makes a change in the state.
    
    ```javascript
    import { createStore, applyMiddleware, combineReducers } from "redux";
    import thunk from "redux-thunk";
    import { composeWithDevTools } from "redux-devtools-extension";
    
    // Importing reducers
    import userReducer from "./user/user.reducer";
    import cartReducer from "./cart/cart.reducer";
    import productsReducer from "./products/products.reducer";
    
    // combining reducers
    const rootReducer = combineReducers({
      user: userReducer,
      cart: cartReducer,
      products: productsReducer,
    });
    
    // creating store
    const store = createStore(
      rootReducer,
      composeWithDevTools(applyMiddleware(thunk))
    );
    
    export default store;
    ```
    
    In this example, we are combining 3 reducers, `userReducer`, `cartReducer`, and `productsReducer` using the `combineReducers` utility from Redux.
    
    After combining the reducers, we create the Redux store using the `createStore` function, passing in the `rootReducer` and middleware using `applyMiddleware(thunk)` provided by `redux-thunk` library.
    
    The store is then exported to be used in the application.
    
    ```javascript
    // action types
    export const ADD_TODO = "ADD_TODO";
    export const COMPLETE_TODO = "COMPLETE_TODO";
    
    // action creators
    export const addTodo = (text) => {
      return {
        type: ADD_TODO,
        payload: {
          text,
          completed: false,
        },
      };
    };
    
    export const completeTodo = (id) => {
      return {
        type: COMPLETE_TODO,
        payload: {
          id,
        },
      };
    };
    ```
    
    In this example, we have two Redux action creators, `addTodo` and `completeTodo`.
    
    `addTodo` accepts a `text` argument, which is the text of the todo to be added. It returns an action object with a type defined as constant `ADD_TODO` and payload containing the `text` and `completed` property.
    
    Redux is used for large projects because In large projects data can be stored in many formats and can be used by many components so It's good to make the state centralized and predictive.
    

There is some more state management tools like: Flux ,Rematch etc.

**Thankyou for reading please write some suggestion in comment to imporve the contant.**