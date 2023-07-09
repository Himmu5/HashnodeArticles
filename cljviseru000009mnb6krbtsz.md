---
title: "Understanding React's Virtual DOM: A Key Concept for Building Efficient UIs"
seoTitle: "Understanding React's Virtual DOM: A Key Concept for Building Efficien"
seoDescription: "Exploring the Inner Workings of React's Virtual DOM for Seamless User Experiences"
datePublished: Sun Jul 09 2023 14:18:40 GMT+0000 (Coordinated Universal Time)
cuid: cljviseru000009mnb6krbtsz
slug: understanding-reacts-virtual-dom-a-key-concept-for-building-efficient-uis
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688872583411/0c2ae8fc-ab4b-4475-ad1e-b407dff22c3c.png
tags: virualdom

---

In this article, we delve into ReactJS's powerful core feature known as Virtual DOM, which plays a pivotal role in making ReactJS highly efficient. Join us as we uncover the inner workings of this impressive feature, examining how it enhances the performance of our websites. Furthermore, we aim to draw comparisons with other popular frontend frameworks like Angular and Vue, highlighting the unique advantages of ReactJS. Discover how leveraging ReactJS's Virtual DOM can elevate your web development endeavors to new heights.

In the traditional methods and in the different frameworks they all are directly working with the original dom. Modifying the Original dom is very expensive and time-consuming. So ReactJS comes with a different approach called Virtual DOM. Virtual DOM is a copy of the original dom but it takes less time to update.

### What is Real Dom?

Dom stands for document object model it is the structure of our website. In the traditional DOM model if there is some change in the data then we need to repaint the whole page. Dom is an abstraction of the HTML page. After introducing the virtual dom it feels very inefficient and expensive. For example, if we are making a chat application like Facebook or Instagram and we are working with the original DOM. on every state change, we need to repaint the whole site. On every notification or message changes will demands to repaint the whole page. so that is very inefficient and also very expensive.

### What is Virtual Dom?

Virtual Dom is an abstraction of the real Dom. It is a copy of the DOM. It compares the old state with the new state and if it gets any difference between them it repaints the exact component where the state is changed. For example, if we are making the exact Chat Application with the virtual dom then on every state changes it does repaint the whole application it will directly repaint the exact component where the state is changed. It is very efficient and less expensive than the original Dom.

Popular libraries like ReactJS and Vuejs are using virtual dom. and Angular is using the real dom to make changes on the web apps.

### Conclusion:

Dom and Virtual Dom both have their own use cases we have to choose the right technology for our project. What we are using is totally dependent on what we are creating. First, we need to think according to the project and then choose a technology.