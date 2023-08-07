---
title: "NodeJS Fundamentals: A Journey into the Heart of Server-side JavaScript"
seoTitle: "NodeJS Fundamental: A Journey into the Heart of Server-side JavaScript"
seoDescription: "Embark on an enriching journey into Node.js backend development with our comprehensive Beginner to Advanced series!"
datePublished: Mon Aug 07 2023 15:14:42 GMT+0000 (Coordinated Universal Time)
cuid: cll10k6d8000109l08ydrgeyj
slug: nodejs-fundamentals-a-journey-into-the-heart-of-server-side-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691151212042/8c842a21-c98c-40bd-a966-3724d4ec868a.png
tags: express, nodejs, backend, apis, developer

---

Embark on an enriching journey into Node.js backend development with our comprehensive Beginner to Advanced series! Starting with this article, we delve into the foundational aspects of Node.js, setting the stage for your learning adventure.

Our inaugural piece introduces Node.js, laying a solid foundation for beginners. Uncover core concepts, kindling curiosity about backend development. From dynamic web apps to efficient solutions, Node.js's potential will be harnessed.

Stay tuned as we unlock the realm of Node.js, guiding you from novice to advanced levels. Prepare to master backend development, one step at a time.

### What is NodeJS?

NodeJS is a runtime for javascript in the backend. It allows javascript to work on the backend side also. Javascript is made to write frontend logic but we can use it to communicate with databases and services with the help of NodeJS. It uses a Chrome V8 engine to work with javascript. When working with NodeJS it feels like Javascript but it's not. Actually, It has all the features of javascript except the specific frontend feature like a document or window model. but it has some additional features like HTTP or file system.

### Chrome V8 engine

V8 engine is a javascript engine that is used to execute the javascript in the browser. By this engine, NodeJS is capable to execute the javascript on the server side. It is using in NodeJS since 2009. There are some more popular javascript engine that is used in different browsers. For example, Spidermonkey is the name of a javascript engine that is used in Firefox. Safari browser has javaScriptCore engine.

### NODEJS server

Generating the server in NodeJS is not very hard. We just need to import the HTTP class and then we have to use the createServer method to generate the server.

```typescript
const http = require('http');

const PORT = 5000;

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello, World!\n');
});

server.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

In the above code, there is a constant variable PORT to get our port value and the server is using that value to create a server.

### GET API in NodeJS

```typescript
const http = require('http');
const PORT = 5000;

const server = http.createServer((req, res) => {
  if (req.method === 'GET' && req.url === '/api') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    const data = {
      message: 'This is a sample GET API response'
    };
    res.end(JSON.stringify(data));
  } else {
    res.writeHead(404, { 'Content-Type': 'text/plain' });
    res.end('Not Found');
  }
});

server.listen(PORT, () => {
  console.log(`API server is running on port ${PORT}`);
});
```

To create a get API using NodeJS we have to set headers and we have to write status code and content type manually.

### Conclusion

NodeJS is a great tool to write javascript as a backend. It makes a easy to convert a frontend developer to a full-stack developer. Javascript is the most popular programming language for Frontend development and it can be also used in the backend by NodeJS.