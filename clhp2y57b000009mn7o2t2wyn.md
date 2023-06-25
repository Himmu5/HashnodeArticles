---
title: "Routing in ReactJS: Adding Navigation to Your App"
seoTitle: "Routing in ReactJS: Adding Navigation to Your App"
seoDescription: "In this article, we will understand Routing in ReactJS."
datePublished: Mon May 15 2023 16:49:12 GMT+0000 (Coordinated Universal Time)
cuid: clhp2y57b000009mn7o2t2wyn
slug: routing-in-reactjs-adding-navigation-to-your-app
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683765777534/7c443a08-a49a-40e8-9a48-ac4bad0a4bc3.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684169312194/c888742e-27b1-4895-9ea7-32531728bcdb.png
tags: router, npm, reactjs

---

In this article, we will understand Routing in ReactJS. In ReactJS we can develop **Single Page Applications** (SPA). React makes a single-page application it doesn't change the pages It just changes the content of the page.

I will use the react-router-dom library to explain the Routing concept in ReactJS. This is a very popular library for performing routing. we can change the content without reloading the page using this library.

### **Steps to use Routing with ReactJS**

ReactJS is a library so with this we need to install a different library to change content. here I am going to setup the react-router-dom library.

**Step I: Setup a React project**

For this, I have already created a blog I am giving the link to it so you can follow that.

%[https://himanshuchauhan.hashnode.dev/mastering-responsive-ui-design-fylo-using-react-js] 

**Step II: Install the react-router-dom library**

I am using the npm to install this package if you want to use yarn feel free to use it.

```javascript
npm install react-router-dom
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684080002960/b46a6b1b-8b08-4cba-b1a3-3d63ed2dfc62.png align="center")

this command will install the router package in your project. after installing this is how your package.json will look like.

**Step III: Code setup for react-router-dom**

First, we need to provide the BrowserRouter in the whole app. so we can wrap the app component in &lt;BrowserRouter&gt;.

```javascript
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.tsx";
import "./index.css";
import { BrowserRouter } from "react-router-dom";

ReactDOM.createRoot(document.getElementById("root") as HTMLElement).render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
);
```

We have to create Routes to set the path and its corresponding element. the react-router-dom library provides us with an element for this.

```javascript
 <Routes>
     <Route path="/" element={<Navigate />} />
     <Route path="/Home" element={<Home />} />
     <Route path="/Dashboard" element={<Dashboard />} />
     <Route path="/About" element={<About />} />
 </Routes>
```

here I have set the various routes to different pages. The Navigate component is the main route of the site and we can reach to `<Home >, <Dashboard >, <About >`.

We need to set the links to change the routes. we have a `<Link >` component to change the URLs. I have used these Links to Navigate component.

```javascript
import { FC } from "react";
import { Link } from "react-router-dom";

type P = {};

const Navigate: FC<P> = () => {
  return (
    <div className="flex gap-5 my-2">
      <Link to="/Home" className="px-3 py-1 rounded-md bg-red-400 hover:bg-red-500 text-white ">Home</Link>
      <Link to={"/About"} className="px-3 py-1 rounded-md bg-red-400 hover:bg-red-500 text-white ">ABout</Link>
      <Link to={"/Dashboard"} className="px-3 py-1 rounded-md bg-red-400 hover:bg-red-500 text-white ">Dashboard</Link>
    </div>
  );
};

export default Navigate;
```

This component is showing the three Links each will redirect you to a different route.

here are some more methods to make routing better. for example, useLocation hook is you to go the previous route it works like a back button.

```javascript
import { useLocation } from "react-router-dom";

function MyComponent() {
  const location = useLocation();

  // Get the path of the current URL
  const pathname = location.pathname;

  // Get the query string of the current URL
  const queryString = location.search;

  // Get the hash fragment of the current URL
  const hash = location.hash;

  return (
    <div>
      <h1>The current URL is {pathname}</h1>
      <p>The query string is {queryString}</p>
      <p>The hash fragment is {hash}</p>
    </div>
  );
}
```

This snippet will display the current URL, query string, and hash fragment in the browser.

Thank you for the reading😍. please write your valuable suggestion that will create great value for my learning.