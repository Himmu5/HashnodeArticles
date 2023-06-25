---
title: "React and its supportive libraries environment"
datePublished: Sun Apr 02 2023 10:32:55 GMT+0000 (Coordinated Universal Time)
cuid: clfz9kmdz000709mf6emoc1cx
slug: react-and-its-supportive-libraries-environment
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/ayjnmG4oUX4/upload/365d91594d8b986300b8ebd78f4ce5fc.jpeg
tags: library, reactjs, axios, formik

---

React is a very popular **Frontend library**. For every purpose, they're many different libraries to do that thing. This is a very difficult task to identify a correct library to solve the problem. To develop a site there are many tasks to do like Form handling, Form validation, Handle API calls, icons and CSS design.

When using a library in code always remember that code can be malicious and can harm your project. Always use a library that has popular in **GitHub**. That repository should have a good number of stars on GitHub that would be safe for your code.

Popular libraries are audited by many people so there can is less chance to be unsafe code on them.

### **Libraries for Different purpose**

1. **Form handling:** Almost every web app contains a form in it. This is very tough without the use of an external library. Without a library, we have to maintain multiple states and multiple **handleChange** functions in it according to its input fields. That would be a difficult and lengthy task to get done.
    
    To do this work easily there are many libraries to help us some of them are given below:
    
    * **Formik**: This Library has 32k stars on GitHub. It is loved by many Frontend developers. It is very easy to use and it makes maintainable code. It helps to maintain the states and provides handleChange,handleSubmit and many helpful inbuild functions.
        
        `To create a simple code snippet for the Formik library, you can start by installing it using npm or yarn:`
        
        ```plaintext
        npm install formik
        ```
        
        or
        
        ```plaintext
        yarn add formik
        ```
        
        Redux Form: To connect your React Form to the Redux store it can be used. It provides function and HOCs to connect to the store.
        
    * **Form Reducer**: This function tells the reducer how to handle action that is coming from the React Form. This function needs to pass to the store. It serves **all of your form components**, so you only have to pass it once
        
    * ```javascript
          import { createStore, combineReducers } from 'redux'
          import { reducer as formReducer } from 'redux-form'
          
          const rootReducer = combineReducers({
            // ...your other reducers here
            // you have to pass formReducer under 'form' key,
            // for custom keys look up the docs for 'getFormState'
            form: formReducer
          })
        ```
        
        **2\. API handling**: Api handling is the most important part of creating a Dynamic React web app. Apis connect us with servers and it helps us to communicate with servers. Here are some libraries given below which make love when interacting with APIs.
        
    * **Axios**: It is the most popular library when we are talking about API handling. It has almost 1 lakh stars on GitHub so it is safe to use. It is trusted by most react developers.
        
    
    ```plaintext
    npm install axios
    ```
    
    Example API call:
    
    ```javascript
    import React, { useState, useEffect } from 'react';
    import axios from 'axios';
    
    const MyComponent = () => {
      const [data, setData] = useState([]);
    
      useEffect(() => {
        axios.get('https://jsonplaceholder.typicode.com/users')
          .then((response) => {
            setData(response.data);
          })
          .catch((error) => {
            console.log(error);
          });
      }, []);
    
      return (
        <div>
          <h1>Users List</h1>
          <ul>
            {data.map((user) => (
              <li key={user.id}>{user.name}</li>
            ))}
          </ul>
        </div>
      );
    }
    
    export default MyComponent;
    ```
    
    In this example, we imported Axios and called Jsonplaceholder api that will give us data about users. I am using the get method on it. there is many other methods like **get**, **post**, **put**, **patch**, and **delete**.
    

Thanks for reading.