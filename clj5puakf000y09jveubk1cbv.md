---
title: "Effortless Authentication: React Firebase Sign-In Made Easy"
seoTitle: "Effortless Authentication: React Firebase Sign-In Made Easy"
seoDescription: "Building a Secure React Firebase Authentication App: A Step-by-Step Guide"
datePublished: Wed Jun 21 2023 12:54:05 GMT+0000 (Coordinated Universal Time)
cuid: clj5puakf000y09jveubk1cbv
slug: effortless-authentication-react-firebase-sign-in-made-easy
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686850463596/17c1d918-2771-48ee-b0c9-3add35886aa9.png
tags: authentication, firebase, reactjs

---

User authentication is a crucial aspect of any modern web application. In this article, we will explore how to implement user authentication using Firebase, a powerful and user-friendly platform that simplifies the authentication process. We will also leverage the popular ReactJS framework and the material UI library for a seamless and visually appealing user interface.

### What is Firebase?

Firebase is a set of cloud-based tools to build a web App or Mobile app. It provides many features in it. It can be used for the development, deployment or data visualization tool.

**Features of Firebase**

1. **Real-time database**: It provides real-time database support to users. It is a NoSQL-type database. It uses a JSON-based structure to store the data.
    
2. **Authentication:** It provides many inbuild Authentication methods like sign-in with Email/Password, social login or many other methods.
    
3. **Performance Monitoring**: Firebase Performance Monitoring helps you gain insights into your app's performance, including app startup time, network latency, and other key metrics. It helps identify performance bottlenecks and optimize your app's performance.
    

### **Methods provided By Firebase for Authentication**

There are many methods to Authenticate the user. we can use email/password, token or credentials for Authentication. Also, there is some method to create a user Account we can use email/password or social media account to create an account.

* **createUserWithEmailAndPassword:** It is for creating an account with the email and password. we just need to pass the email and password to the parameter of this function and the account is created.
    
    ```javascript
    import { getAuth, createUserWithEmailAndPassword } from "firebase/auth";
    
    const auth = getAuth();
    createUserWithEmailAndPassword(auth, email, password)
      .then((userCredential) => {
        // Signed in 
        const user = userCredential.user;
        // ...
      })
      .catch((error) => {
        const errorCode = error.code;
        const errorMessage = error.message;
        // ..
      });
    ```
    
* **signInWithEmailAndPassword:** It is used to sign in to the user with an email and password.
    
    ```javascript
    import { getAuth, signInWithEmailAndPassword } from "firebase/auth";
    
    const auth = getAuth();
    signInWithEmailAndPassword(auth, email, password)
      .then((userCredential) => {
        // Signed in 
        const user = userCredential.user;
        // ...
      })
      .catch((error) => {
        const errorCode = error.code;
        const errorMessage = error.message;
      });
    ```
    
* **onAuthStateChanged**: On every page we need to get users' information so there is a function called onAuthStateChanged to get the data.
    
    ```javascript
    import { getAuth, onAuthStateChanged } from "firebase/auth";
    
    const auth = getAuth();
    onAuthStateChanged(auth, (user) => {
      if (user) {
        // User is signed in, see docs for a list of available properties
        // https://firebase.google.com/docs/reference/js/auth.user
        const uid = user.uid;
        // ...
      } else {
        // User is signed out
        // ...
      }
    });
    ```
    
    these three methods are very important and easy to use in the Firebase authentication part. There are many other methods to authenticate the user. Like: signInAnonymously, signInWithCredential, signInWithCustomToken and many more.
    

### Firebase authentication project

To understand the firebase auth we will create a project for Authenticate and create user.

**Setup the project**

First, we need to install the reactJS library. so I am using npm if you want different you can use them.

```javascript
npm init vite@latest firebase_auth -- --template react-ts
```

and for styling purposes, we will use the tailwind CSS library.

```javascript
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

After this library, we need to add the Firebase package.

```javascript
npm i firebase
```

Then we need to set up the Firebase database. for this, we need to visit [https://firebase.google.com/](https://firebase.google.com/) site.

### There are some steps to set up a database in google firebase

**Step I**: First, you need to create a Google account and log in with it. Then click on the Get Started button there.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687348479098/a60b30bb-5244-4cbc-8d80-c1907c1d9f8b.png align="center")

**Step II**: Then create a project and put the name of it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687348568945/52c1ee97-e5c1-4675-96e0-4a229626d1c3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687348692718/770007d7-761c-40d6-b090-8089d73f0aa5.png align="center")

**Step III**: Then create a Firebase database by clicking on the create firebase button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687348778814/b3266712-5b89-4ff3-813b-0f3a21c3d413.png align="center")

Now the database setup is done. so we can start the project.

### Frontend Project

I have created a ReactJS form for login and signup and managed the state of the form with the Formik library.

here is the folder structure for this.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687349854376/efe5f5f7-887d-4b28-8bfe-d67bac524c57.png align="center")

first, we need to create a Firebase config file and we will add the config code to theirs.

```javascript
// For Firebase JS SDK v7.20.0 and later, measurementId is optional
import { initializeApp } from "firebase/app";
import { getAuth } from "firebase/auth";

const firebaseConfig = {
  apiKey: "AIzaSyAIuAbhpL3RTOzYlahSAtGp9336955MUZY",
  authDomain: "auth-users-6ed23.firebaseapp.com",
  databaseURL: "https://auth-users-6ed23-default-rtdb.firebaseio.com",
  projectId: "auth-users-6ed23",
  storageBucket: "auth-users-6ed23.appspot.com",
  messagingSenderId: "689168862397",
  appId: "1:689168862397:web:749b95072a28655614bbd4",
  measurementId: "G-JBX5H6R82B",
};

export const app = initializeApp(firebaseConfig);
export const auth = getAuth(app);
```

This code we can get from the project setting part of Firebase.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687350017527/ff751734-bf34-4039-8a50-9591444b793b.png align="center")

For creating an account we can you createUserWithEmailAndPassword function.

```javascript

const initialValues = {
  firstName: "",
  lastName: "",
  email: "",
  password: "",
  confirmPassword: "",
};

type I = typeof initialValues;

function submit(value: I, bag: FormikBag<P, I>) {
  createUserWithEmailAndPassword(auth, value.email, value.password).then(
    (res) => {
      bag.props.setUser(res);
    }
  );
  bag.resetForm();
}
```

here we can pass the email and password into the function and it will store the information in the Firebase database.

And for the sign-in purpose, the signInWithEmailAndPassword function can be used.

```javascript
const initialValues = { email: "", password: "" };

type I = typeof initialValues;

function submit(values: I, bag: FormikBag<P, I>) {
  signInWithEmailAndPassword(auth, values.email, values.password).then(
    (res) => {
      bag.props.setUser(res);
    }
  );
}
```

Then the function is similar to the previous one. It also takes the email and password into the parameters and it will authenticate the credentials.

HTTP is a stateless protocol so we need to send the credentials to the server on every page. To avoid this headache we use tokens so we can authenticate the user by the token.

```javascript
 const [user, setUser] = useState<User>();

  useEffect(() => {
    onAuthStateChanged(auth, async (userData) => {
      setUser(userData || undefined);
    });
  }, []);
```

onAuthStateChanged function automatics take the Refresh token and It can authenticate the user by the token. This function keeps a user logged in until the user itself does not log out.

Firebase is a very good tool to authenticate a user with minimal effort.

💕Thank you for reading. please share your valuable suggestions in the comments.