---
title: "Styling ReactJS Components: Using Tailwind CSS"
seoTitle: "Styling ReactJS Components: Using Tailwind CSS"
seoDescription: "In this article, we are talking about the use of tailwind CSS to import the UI of reactJS components."
datePublished: Wed May 17 2023 16:58:19 GMT+0000 (Coordinated Universal Time)
cuid: clhry5kcn000009jj1oex59sn
slug: styling-reactjs-components-using-tailwind-css
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684199319840/e965911b-606e-4c6b-92b2-8044f32def6d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684342626687/28c16e48-1f91-4091-92ad-d78c40ffb2f8.png
tags: tutorial, reactjs, tailwind-css

---

In this article, we are talking about the use of tailwind CSS to import the UI of reactJS components. Using normal CSS can make it more difficult to create UIs. This library uses atomic property classes. The meaning of atomic is to single class single property added in the element.

Tailwind CSS is a library similar to Bootstrap and SASS. tailwind makes it easy to add inline classes. It makes it very comfortable to write CSS with reactJS. It is highly customizable and It has no annoying opinionated things. It gives full freedom to write customizable components. It removes the traditional CSS part where we need to think about the name of the classes and ids.

### **Setup with ReactJS**

we can easily add tailwind CSS in our reactJS project. I am using npm to add these packages to the project.

```javascript
npm install -D tailwindcss postcss autoprefixer
```

this command will install tailwind CSS,postcss and autoprefixer in the project.

PostCSS is a JavaScript tool that transforms your CSS code into an abstract syntax tree (AST) and then provides an API (application programming interface) for analyzing and modifying it using JavaScript plugins. It transpile the special PostCSS plugin syntax into vanilla CSS.

Then generate the **tailwind.config.js** and **postcss.config.js** files.

```javascript
npx tailwindcss init -p
```

**Specify the path in the tailwind.config.js file**

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

**Add the directive layer in the index.js**

```javascript
@tailwind base;
@tailwind components;
@tailwind utilities;
```

that is the last step of setup now we can use the tailwind CSS in the project.

### **Tailwind CSS Playground**

tailwind provides a playground to taste tailwind. if someone never tries the tailwind CSS so that person can take a start from there.

%[https://play.tailwindcss.com/] 

Here is the link given above for taking a try at tailwind CSS. but it is not for development.

```javascript
<div class="flex h-screen w-full flex-col items-center justify-center bg-gray-300">
  <button class="rounded-md bg-indigo-400 px-4 py-1 text-white hover:bg-indigo-500">Button</button>
</div>
```

I have created a simple button in tailwind CSS. It is easy to write tailwind classes and it saves a lot to stress of a programmer.

Here is a blog page created using Tailwind CSS.

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <title>Blog Example</title>
</head>
<body>
  <header class="bg-gray-900 text-white py-4">
    <div class="container mx-auto flex items-center justify-between px-4">
      <h1 class="text-2xl font-bold">My Blog</h1>
      <nav>
        <ul class="flex space-x-4">
          <li><a href="#" class="hover:text-gray-400">Home</a></li>
          <li><a href="#" class="hover:text-gray-400">About</a></li>
          <li><a href="#" class="hover:text-gray-400">Contact</a></li>
        </ul>
      </nav>
    </div>
  </header>
  
  <main class="container mx-auto py-8 px-4">
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
      <div class="bg-white shadow-md p-4">
        <h2 class="text-xl font-bold mb-2">Blog Post 1</h2>
        <p class="text-gray-600 mb-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod mauris vel augue feugiat, sed ultricies turpis fringilla.</p>
        <a href="#" class="text-blue-500 hover:text-blue-700">Read more</a>
      </div>
      <div class="bg-white shadow-md p-4">
        <h2 class="text-xl font-bold mb-2">Blog Post 2</h2>
        <p class="text-gray-600 mb-4">Suspendisse at nunc nec risus ultrices eleifend id sed arcu. Nulla lacinia leo turpis, et bibendum purus posuere a.</p>
        <a href="#" class="text-blue-500 hover:text-blue-700">Read more</a>
      </div>
      <div class="bg-white shadow-md p-4">
        <h2 class="text-xl font-bold mb-2">Blog Post 3</h2>
        <p class="text-gray-600 mb-4">Quisque feugiat, erat sed convallis viverra, metus sem ultricies ipsum, ac volutpat metus lorem a arcu.</p>
        <a href="#" class="text-blue-500 hover:text-blue-700">Read more</a>
      </div>
    </div>
  </main>
  
  <footer class="bg-gray-900 text-white py-4">
    <div class="container mx-auto text-center">
      &copy; 2023 My Blog. All rights reserved.
    </div>
  </footer>
</body>
</html>
```

In this example, we have a simple blog layout with a header, main content area, and footer. The header includes a navigation menu, and the main content area displays three blog posts using a grid layout. Each blog postcard has a title, content, and a "Read more" link. The footer contains copyright information.

Tailwind CSS classes are used to style the elements. For example, classes like `bg-gray-900`, `text-white`, `py-4`, `text-2xl`, `font-bold`, `mb-2`, `text-gray-600`, `mb-4`, `text-blue-500`, `hover:text-blue-700`, etc., are applied to achieve the desired styling.

😍Thank you for reading. don't forget to leave a comment.