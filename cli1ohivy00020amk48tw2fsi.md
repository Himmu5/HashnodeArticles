---
title: "Redux Toolkit: The Redux Way to Write Redux"
seoTitle: "Redux Toolkit: The Redux Way to Write Redux"
seoDescription: "A comparison of Redux Toolkit and core Redux."
datePublished: Wed May 24 2023 12:25:22 GMT+0000 (Coordinated Universal Time)
cuid: cli1ohivy00020amk48tw2fsi
slug: redux-toolkit-the-redux-way-to-write-redux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684977392283/69795ec6-b5ad-4d6c-998c-06ceeeb43068.png
tags: reactjs, redux, redux-toolkit

---

In this article, we will discuss the advantages of using Redux Toolkit over Core Redux. Redux Toolkit is a set of tools that make it easier to develop Redux applications. It provides a number of features that can help you to write more concise, maintainable, and efficient code.

Redux toolkit is a better tool to write redux logic because when we are writing the core redux then we need to write more boiler code. It makes it faster to write the redux logic. In the core redux there are many things that we need to do manually Like creating the actions. In react we can't mutate the state variable so we do not mutate the state of the redux store in reducers that make hard the state changes.

Redux toolkit is officially recommended by Redux since 2019.

### **Redux Toolkit Setup**

here are some steps for creating the react project with redux.

### 1\. Create a react app with Vite builder

```javascript
npm init vite@latest React-ReduxToolkit -- --template react-ts
```

### **2\. Go to the newly created folder**

here is the command for navigating to the folder

```javascript
cd React-ReduxToolkit
```

### 3\. Install the @reduxjs/toolkit and react-redux library

```javascript
npm install @reduxjs/toolkit react-redux
```

### 4\. Now run the web App

```javascript
npm run dev
```

### **Redux Toolkit Vs Redux**

here is some major difference between Redux Toolkit and Redux

* There is a lot of boilerplate code in Redux. this problem is reduced in Redux Toolkit.
    
* In core Redux we need to install additional tools like immer, reselect, Normalizer etc. These libraries are inbuild in the redux Toolkit.
    
* In Redux we can't mutate the state directly. Redux toolkit provides this thing.
    

### **Redux Toolkit Vs Context API**

* Redux Toolkit is an external library but Context API is provided by the React library.
    
* Both tools are for maintaining the state globally but the Redux toolkit also makes it predictable.
    
* In Context, there is no way to test the errors. Redux Toolkit makes error handling easier.
    
* We can play or pause in the Redux toolkit to see changes.
    

### Code snippets for Redux Toolkit

**Creating Store**

```javascript
export const store = configureStore({
    reducer:{
        router: routerReducer,
        quote : quoteReducer
    },
    middleware:[sagaMiddleWare , routerMiddleware]
})
```

In the Redux toolkit creating a store is a much easier task than the core Redux. It can combine the reducers and pass the middleware in easily.

**Reducers**

```javascript
const initialState = {
  loading: false,
  quotes: {} as { [id: string]: { _id: string; contant: string } },
};
type State = typeof initialState;

const todoSlice = createSlice({
  name: "quote",
  initialState,
  reducers: {
    loading: loadingFunction,
    fetchQuote: getQuote,
  },
});
export const { loading , fetchQuote } = todoSlice.actions;
export const todoReducer = todoSlice.reducer;
```

here we don't need to create the reducers Redux toolkit provides slices that can create actions and reducers for the developer. There are many things we can do here in the concept of entityAdapter This tool is for managing our state automatically.

Thank you❤️ for the reading. Please share your suggestion in the comments.