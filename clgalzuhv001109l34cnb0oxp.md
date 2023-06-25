---
title: "All about package.json file and understanding npm"
seoTitle: "All about package.json and understanding npm"
datePublished: Mon Apr 10 2023 09:06:09 GMT+0000 (Coordinated Universal Time)
cuid: clgalzuhv001109l34cnb0oxp
slug: all-about-packagejson-file-and-understanding-npm
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/oZMUrWFHOB4/upload/872c2ce73fecb1ced94599f0a9fc5e44.jpeg
tags: npm, package-manager, public-library

---

**npm** stands for node package manager it helps us for managing javascript packages. When working with javascript many times programmer needs many external codes to make their project. Code can depend on many other libraries these libraries' updates came many times to improve the library. Many times programmers have to update that library. It is a big task to update libraries manually. npm, help us to do this thing.

npm installs, update and remove libraries in code. It also helps to distribute the code to other people. It provides **Registry** to make code available to others. The registry can be public or private. The free npm Registry has become the center of JavaScript code sharing, and with **more than two million packages**, the largest software registry in the world.

### package.json file

Our code depends on that libraries so these libraries are dependency on our code. Dependency can be two types Dependency and dev dependency. Some dependencies are permanent on our code and always will depend on that library. so this library is dependency and some libraries are used only in the time of development this library is called dev-dependency.

```javascript
{
  "name": "my-awesome-project",
  "version": "1.0.0",
  "description": "This is my awesome project",
  "main": "index.js",
  "dependencies": {
    "express": "^4.17.1",
    "lodash": "^4.17.21"
  },
  "devDependencies": {
    "nodemon": "^2.0.7"
  },
  "scripts": {
    "start": "node index",
    "dev": "nodemon index"
  },
  "author": "John Doe",
  "license": "MIT"
}
```

A few brief notes on what each field means:

* **name**: The name of your project, must be unique on npm.
    
* **version**: A version number using semantic versioning (e.g. `MAJOR.MINOR.PATCH`)
    
* **description**: A Brief description of your project.
    
* **dependencies**: The list of packages that your project depends on in production.
    
* **devDependencies:** The list of packages that your project depends on during development.
    
* **script**: A dictionary of script commands that can be executed with `npm run`.
    
* **author**: The name of the author of your package.
    
* **license:** The license your project is released under.
    

### How npm manages package.json

when a programmer wants to install any package using npm. He needs to write like `npm install <package name>` into the terminal. Then npm makes the entry of this package and adds its version with some symbol.

```javascript
"nodemon": "^2.0.7"
```

In the above example, nodemon package is installed and this is the entry of that package. On the left side is the name of that package and in right is the version of this package. There is a symbol with the version that symbol is called the carrot symbol( ^ ).

Types of symbols in npm version

* **carrot( ^ )**: Using a caret (^) sign means that we can accept minor releases and patch releases, but not major releases when updating our package.
    
* **tilde( ~ )**: Using a tilde sign before our version number means that we can accept only a patch release when updating our package.
    
* **Asterisk( \* ):** Using an asterisk means “accept all releases”, but this is not advisable as it will accept major releases and may break our code.
    

### How to Remove any Package from a Project

To remove there is a command `npm uninstall <package name>` It will remove the entry from package.json and also remove files from node modules. It will also update the package-lock.json file.

Here is also another way to remove any local package from the project. first, you have to remove the entry of that package manually from package.json. And then run `npm install` it will update all the things automatically.

### **How to Update any package version**

To update there is a command `npm update <package name>` It will update a single package in the current project. To update the global package we have to add **\-g** with this command.

### **npm scripts**

package.json has a script property. It is for starting command line tools that are installed within the project's local context. some common scripts are :

* **npm test**: to run your test
    
* **npm build**: to build the project
    
* **npm start**: to run your project locally
    

Thank you for reading please drop your valuable suggestion in the comment box.

![Thank you image](https://allfreethankyounotes.com/wp-content/uploads/2021/01/all-free-thank-you-gif-5.gif align="center")

Author: Himanshu Chauhan**❤**