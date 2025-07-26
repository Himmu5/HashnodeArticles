---
title: "Introduction of NextJS"
seoTitle: "Introduction of NextJS"
seoDescription: "The Framework for Production-Grade React Applications"
datePublished: Sat Jul 26 2025 05:29:03 GMT+0000 (Coordinated Universal Time)
cuid: cmdjt8i6g000c02ju9iby8f9v
slug: introduction-of-nextjs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1752850274168/204edc3d-4cee-42d8-b207-0e68333aaf39.png
tags: basics, nextjs

---

In the world of Modern web applications, there are a large number of frameworks. Every Framework has its own pros and cons. However, we will now begin discussing the most popular Web application framework. So we will start our discussion around NextJS. We have a lot to talk about this framework, so we will discuss this topic in depth in a complete series.

# What is NextJS?

NextJS is a full-stack framework for building modern web applications. It’s built on top of the ReactJS library. Next.js comes up with many great features like SSR, CSR, SSG, etc. It is highly optimized for building single-page model applications. And this is a full-stack framework, so we can create APIs or call a database query directly with this framework. It has many optimizations like caching, Image Optimization, Font Optimization, and OG Images. NextJS's server-side approach makes it safe to use.

## Core feature of NextJS

In Next.js, there are a lot of good features to make the application fast and smooth.

* File-based routing: NextJS has its own file based routing. We just need to add the route name as the folder name and need to create a page.jsx or page.tsx file in it. In the example below, we are creating /test a route. So we created a folder in the app directory and created a page.tsx file.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1753022006702/7ea97edb-3b2d-4d13-906f-0e3451cd6ad8.png align="left")
    
* Static Site Generation (SSG): Generating pages at build time to make pages faster. This is best for a blog, a landing page.
    
* Server-Side Rendering (SSR): Rendering the page on the server to reduce load on the client so the app can work faster.
    
* API Routes: Creating API routes in NextJS is very fast and clean. We need to create an API folder in the app directory and create a route.js or route.ts file in it.
    
* Image Optimization: NextJS provides a built-in Image component to show images in an optimized manner.
    

## NextJS vs ReactJS

NextJS is built on top of ReactJS, so it already inherits all its features. The first thing that we should consider while comparing both technologies, ReactJS is a library and NextJS is a full-stack framework.

### ReactJS

React is a JavaScript library built to create a User interface. It has a focus on rendering UI on the client side. It requires React Router for routing. This is best for where data is updating very frequently. It is very flexible to integrate with other libraries.

### NextJS

NextJS is built on ReactJS. It focuses on rendering pages on the server for faster loading. it is a full-stack framework, so we can build APIs and UI both with this framework. It has its own routing technique, so we don’t need to install any third-party library for routing. NextJS makes the application SEO friendly. It has many features like SSR, OG Images, meta tags, etc.

## Setup NextJS application

To set up a Next.js application, we have a single prerequisite: Node.js. There are a few basic steps to set up a NextJS application below:

1. First, we need to run the following command:
    
    ```typescript
    npx create-next-app@latest
    ```
    
2. There are some options that we can choose as per our needs:
    
    ```plaintext
    What is your project named? my-app
    Would you like to use TypeScript? No / Yes
    Would you like to use ESLint? No / Yes
    Would you like to use Tailwind CSS? No / Yes
    Would you like your code inside a `src/` directory? No / Yes
    Would you like to use App Router? (recommended) No / Yes
    Would you like to use Turbopack for `next dev`?  No / Yes
    Would you like to customize the import alias (`@/*` by default)? No / Yes
    What import alias would you like configured? @/*
    ```
    
3. Run the project with the following command:
    
    ```typescript
    npm run dev
    ```
    

## Conclusion

Next.js stands out as a powerful framework that builds on top of React to deliver production-grade web applications with ease. It simplifies routing, improves performance with features like SSR and SSG, and enhances developer experience through built-in optimizations like image handling and API routes. Whether you're building a simple blog or a complex enterprise app, Next.js provides the flexibility, scalability, and speed modern web projects demand. If you're already comfortable with React, learning and adopting Next.js is a natural and highly rewarding next step.