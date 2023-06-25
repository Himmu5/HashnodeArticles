---
title: "Working with APIs in ReactJS"
seoTitle: "Working with APIs in ReactJS"
seoDescription: "In this article, we will understand the APIs.Generally, we don't make a static site on ReactJS."
datePublished: Wed May 10 2023 17:29:22 GMT+0000 (Coordinated Universal Time)
cuid: clhhz6jb500090amr8eo56j10
slug: working-with-apis-in-reactjs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683564637234/ae8bd071-a03b-48b4-9e91-4d61b0698a3d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683712981406/34995938-daed-4d61-8215-63df2746f5ee.png
tags: reactjs, rest-api, axios

---

In this article, we will understand the APIs.Generally, we don't make a static site on ReactJS. The core of ReactJS is rendering multiple components and showing dynamic data. For getting that data from the server we have to use APIs. Data can be coming from the self-server or another server APIs helps us for doing that.

Here are two major components of APIs.

* **client:** The client is the user that is using the software and wants the data. Generally, clients are the end user.
    
* **server:** The server is the computer that provides the data when a client requires it.
    

### **REST APIs**

REST Apis is the most common API type that is used for fetching data. It provides us with some methods to request the data from the server. We can get or send the data by the REST APIs. We can send the data to a server in header, body or params.

**REST APIs methods**

* **GET**: This method is used to get the data from the server. This method is specially used to get the data if you are working with REST APIs. but can't send data in the body of the GET method. In React we use a popular library called Axios. It makes it easy and convenient to call an API.
    
    ```javascript
    import axios from "axios";
    
    export function fetchQuoteRandom() {                                  return axios.get("https://api.quotable.io/random").then((res)=> {
        return res.data;
      });
    }
    ```
    
    here we are calling the API using the GET method. It is a Quote fetching API it will return a random Quote object from the database. This fetchQuoteRandom method returns the promise of the JSON data.
    
* **POST**: The post method is used to create some data in the database. We have to send data that need to be created on the database generally It was present in the body of the method.
    
    ```javascript
    function handleSubmit() {
      axios
        .post("/api/addData", { data: "my data" })
        .then((res) => console.log(res.data))
        .catch((err) => console.log(err));
    }
    ```
    
    In this example, we import the `axios` library and use the `post` method to send an HTTP POST request to the `/api/addData` endpoint with the data `{data: 'my data'}`. The `then` the function is used to handle a successful response and the `catch` function is used to handle any errors that may occur.
    
* **PUT**: The put method is used to update some instances in the database. It replaces the current instance with the out-provided instance.
    
    ```javascript
    function handleUpdate() {
      axios
        .put(`/api/updateData/${data.id}`, { newData: "updated data" })
        .then((res) => console.log(res.data))
        .catch((err) => console.log(err));
    }
    ```
    
    In this example, we import the `axios` library and use the `put` method to send an HTTP PUT request to the `/api/updateData/:id` endpoint with the data `{ newData: 'updated data' }`. The :`id` parameter in the endpoint URL is replaced with the ID of the data you want to update from the `data` prop passed to the component. The `then` function is used to handle a successful response, and the `catch` function is used to handle any errors that may occur.
    
* **PATCH**: The patch method is also used to update the instance in the database but it's working differently from the put method. It does not replace the whole instance but it replace only matching keys which we are sending to the database.
    
    ```javascript
    function handleUpdate() {
      axios
        .patch(`/api/updateData/${data.id}`, { newData: "patched data" })
        .then((res) => console.log(res.data))
        .catch((err) => console.log(err));
    }
    ```
    
    In this example, we import the `axios` library and use the `patch` method to send an HTTP PATCH request to the `/api/updateData/:id` endpoint with the data `{ newData: 'patched data' }`. The `:id` parameter in the endpoint URL is replaced with the ID of the data you want to patch from the `data` prop passed to the component.
    
* **DELETE**: The delete method is used to delete some data or instances from the database.
    
    ```javascript
    function handleDelete() {
        axios.delete(`/api/deleteData/${id}`)
          .then(res => console.log(res.data))
          .catch(err => console.log(err));
      }
    ```
    
    In this example, we import the `axios` library and use the `delete` method to send an HTTP DELETE request to the `/api/deleteData/:id` endpoint. The `:id` parameter in the endpoint URL is replaced with the ID of the data you want to delete from the `id` prop passed to the component.
    

**Conclusion**: Apis helps frontend code to interact with the backend. It also helps to use the services of another software. For example, Google Apis helps to login to users in a single click. It makes possible cross-software communication.

Thank you for the reading. Please share your valuable comment in the comment section. ❤️❤️