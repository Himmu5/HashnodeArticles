---
title: "ExpressJS Unleashed: A Journey from Basics to Building Dynamic Web Applications"
seoTitle: "ExpressJS Unleashed: A Journey from Basics to Building Dynamic Web App"
seoDescription: "Harnessing the Speed and Simplicity of Node.js for Modern Web Development"
datePublished: Sat Sep 16 2023 15:45:47 GMT+0000 (Coordinated Universal Time)
cuid: clmm7a7ol000k09l50d8sczf2
slug: expressjs-unleashed-a-journey-from-basics-to-building-dynamic-web-applications
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692065361448/be9f3905-35e1-4328-80ef-00862e4683ea.png
tags: express, mongodb, nodejs, crud

---

In this article, we will try to understand the importance of ExpressJS while we are building modern web applications. and also try to find the points to use express while we have NodeJS. We will try to create a small backend to create and login an account in ExpressJS.

### Introduction

ExpressJS is an unopinionated Nodejs framework for creating web applications. We can create API with the use of Express. By the use of many utility methods and middleware, we can create robust APIs quickly.

Express provides us with many methods to quickly make and use an API. It follows the MVC(model, view, controller ) model to create web APIs.

### Why you might choose to use Express when working with Node.js

**Simplifies Routing**: It simplifies the Routing as we can simply use GET, POST, PUT and DELETE methods to create routes.

```typescript
//Import the express module
const express = require("express");
const app = express();
const PORT = 3000;

//Routes
app.get("/", (req, res) => {
  res.send("Welcome to the server!");
});

//Server port set
app.listen(PORT, () => {
  console.log("listening on : ", PORT);
});
```

In the above example, we can easily create GET, POST or any other method by just calling app.get or app.post.

**MiddleWares**: Express supports middleware that helps to authenticate users, logging or request parsing. Basically, middlewares are the functions that we want to perform before entering into the main endpoint code.

```typescript
// Simple middleware
function middleware(req , res , next){
  console.log("Hello I am middleware");
  next();
}
// API get Route
app.get("/", middleware , (req, res) => {
  res.send("Welcome to the server!");
});
```

Here I have created a simple code to explain the middleware. We have a get route that is simply returning a message. but we want to perform some code before running the get method code then we will create a middleware. In the above example, I have created a middleware called middleware that is just printing a message. but we can perform any other task like validate the request or change the path or something else.

In middleware, we can get a third parameter called next which is a function to send our request to the main route function.

**Template Engines:** There are methods to serve HTML using the backend in Express. Express supports many template engines like PUG, EJS, handlebars etc.

**Performance:** Express is lightweight and it is used to build high-performance web applications.

### Mini Project

We will work on a small mini-project to develop a good understanding of Express. In this project, we will create APIs to create users into the database and we will perform CRUD operation on this data. We will use MongoDB as a database in our project.

For this First, we will create a Project and install all the important dependencies in it.

```typescript
{
  "name": "Project-0.0.1",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "nodemon ./index.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "dotenv": "^16.3.1",
    "express": "^4.18.2",
    "mongoose": "^7.5.0"
  }
}
```

In the process of performing CRUD operations first operation is CREATE. so we will create a user account into the DB and for the database I am using MongoDB.

### Step 1:Connect to database

First, we have to connect our backend to the database. I am Mongoose and dotenv libraries to connect the database.

```typescript
const express = require("express");
const mongoose = require("mongoose");
const app = express();
require("dotenv").config();

const port = process.env.PORT;

async function main() {
  await mongoose.connect(process.env.MONGO_URL);
  console.log("Db connection established");
}
main();

app.listen(port, () => {
  console.log("listening on port " + port);
});
```

Here is the code to create a connection with DB.

### Step 2: Create a User Account API

To create a user in DB we need to create a model using Mongoose schema.

```typescript
const mongoose = require("mongoose");

const userSchema = mongoose.Schema({
  name: { type: String, require: true },
  password: { type: String, require: true },
});

const UserModel = mongoose.model('user', userSchema);

module.exports = { UserModel }
```

This is a very simple model for user accounts. there is a simple name and password to create a User in the DB.

```typescript
app.post("/createUser", async (req, res) => {
  const { email, password } = req.body;
  const user = await UserModel.create({ email, password });
  if (user) {
    res.status(201).json({ user, message: "User created successfully " });
  }
  res.status(400).json(`user not created`);
});
```

Here is the simple API to create a user account in DB. here we are just taking the email and password into the body. and creating that user.

### Step 3:Fetch User data

To fetch data from the database I will create an API with the get method.

```typescript
app.get('/getUser' , async (req , res)=>{
    const { email, password } = req.body;
    const user = await UserModel.find({email , password })
    if(user){
        res.status(200).json({ user , message : "user fetched successfully" });
    }else{
        res.status(404).json("User not found");
    }
})
```

Here is getuser API to get the user's information. In this API I am just fetching data from db. I am not validating the data.I will cover the validation in a different blog with full details.

### Step 4: Update data in the database

To update data we can use the put or patch method here I will use the put method to update the existing data.

```typescript

app.put('/updateUser' , async (req , res) =>{
  const { email , password } = req.body;
  const updatedData = await UserModel.findOneAndUpdate({ email } , { email , password : "NewPassword" } , {new :  true})
  if(!updatedData){
    res.status(404).json("user is not updated");
  }else{
    res.status(200).json({ user : updatedData , message : "User updated successfully" });
  }
})
```

### Step 5:Delete User from the Database

At the last, we will try to delete the user from the database. For this, we will create an API with the Delete method.

```typescript
app.delete("/deleteUser" , async (req , res)=>{
  const { email } = req.body;

  const deletedUser = await UserModel.findOneAndDelete({ email });
  if(!deletedUser){
    res.status(400).json("User not deleted");
  }
  res.status(200).json({ user : deletedUser , message : "User deleted successfully" });

})
```

These are simple CRUD APIs I will cover the CRUD operations with validation also in a further blog.

### Conclusion

ExpressJS is a very good Framework for creating APIs. It helps us to create rest APIs very fast. It works with Nodejs environment so it is very convenient for javascript developers.