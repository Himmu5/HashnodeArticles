---
title: "Authentication and Authorization in Express.js: A Comprehensive Guide"
seoTitle: "Authentication and Authorization in Express.js: A Comprehensive Guide"
seoDescription: "Mastering User Authentication and Authorization in Express.js: From Basics to Advanced Strategies"
datePublished: Fri Oct 27 2023 10:03:44 GMT+0000 (Coordinated Universal Time)
cuid: clo8g49uv000f09mpbqy089cg
slug: authentication-and-authorization-in-expressjs-a-comprehensive-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694957177250/bfce4a7f-0678-42c9-bee5-0d8f7fbe31d0.png
tags: express, authentication, nodejs, authorization, apis

---

In this article, we will be delving into the topic of Authentication and Authorization in ExpressJS. My aim is to make this complex subject easy to understand for everyone. We will also explore some new tools that can help us to do Authentication more efficiently. Additionally, we will be implementing middleware in our code, so let's start with an explanation of middleware.

First, we will discuss the difference between Authentication and Authorization. There are some major differences between them so it should be cleared first.

### Authentication

Basically, Authentication means validating the user. if a user demands the resources then we should validate the user. we should take a record of the user first and then we can serve the data to that user.

We can Authenticate the user in many ways. Here we will discuss about JWT token. In JWT verification we encode some data in a long string and send it to the user and the user can use it to request different data. Also, this is very easy to get users' information that the user is correct or not.

### Authorization

Authorization means to check the privileges of the User. Here we have to check whether the user has privileges to use such resources or not. In many projects, there can be different roles for users user can be an Admin, owner or a normal person.

### Understand Authentication with Token verification in Express

First, we need to set up an Express project. and also we will install jsonwebtoken library to authenticate users with tokens. we will generate a token and send it when a new user is created.

First, we will create a user API to create a user in db and we will send a token in response and we will request a user for that token for all other calls.

```typescript
app.post("/user", (req, res) => {
  const reqUser = req.body;
  console.log("User", reqUser);
  const token = jwt.sign(reqUser, secretKey, { expiresIn: "24h" }); // Expires in 24 hour

  UserModel.create(reqUser)
    .then((user) => {
      res.status(201).json({user , token } );
    })
    .catch((err) => {
      res.status(500).json(err);
    });
});
```

Here is the code for creating the user and setting the response with the token.

Frontend will store this token in the browser and it will send this token with every request. In the following code, there is a third parameter in jwt. sign that is an object that contains a key called expiresIn that indicates the token will expire in 24 hours.

Then we have to write code to check the token given by the frontend with every call. so for this, I will create a middleware to check token is correct or not.

```typescript
function validateToken(req, res, next) {
    const frontEndtoken = req.header('Authorization'); // Assuming the token is provided in the "Authorization" header
    const token = frontEndtoken.split(' ')[1];
    if (!token) {
      return res.status(401).json({ message: 'No token provided' });
    }
  
    try {
      const decoded = jwt.verify(token, process.env.SECRET_KEY);
      console.log("Decoded", decoded);
      req.user = decoded; // Attach the decoded token payload to the request for later use
      next(); // Continue to the next middleware
    } catch (error) {
      return res.status(401).json({ message: 'Invalid token' });
    }
  }
```

We can use this function as middleware before every request. It will authenticate the user and send the decoded values from the token.

Here is an endpoint to get a user's particular user information. so we will use middleware to authenticate the request.

```typescript
app.get("/user/:id", validateToken, (req, res) => {
  const id = req.params.id;
  UserModel.findById(id)
    .then((user) => {
      res.status(200).json(user);
    })
    .catch((err) => {
      res.status(404).json(err);
    });
});
```

we can use the middleware in the middle of the endpoint and callback function It will authenticate the token and will send control to callback if the token is correct.

### Conclusion

Authentication and Authorization is very important part of our security process. In the process of Authentication, we can use middleware to authenticate the token. Token are the secret string with our given information which can not be decoded by any other.

Thank you for the reading.😇