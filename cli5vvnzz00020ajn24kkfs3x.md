---
title: "Simplify Your Forms with Formik: Why Formik is an Essential Tool for React Development"
seoTitle: "Simplify Your Forms with Formik"
seoDescription: "Learn how Formik can help you handle form state, validation, and submission in React!"
datePublished: Sat May 27 2023 11:03:24 GMT+0000 (Coordinated Universal Time)
cuid: cli5vvnzz00020ajn24kkfs3x
slug: simplify-your-forms-with-formik-why-formik-is-an-essential-tool-for-react-development
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685030487335/6439b9b2-3806-42e7-81e5-da55fade2134.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1685185395574/976791d0-fbda-4a3c-894c-ab0180ecef6c.png
tags: javascript, reactjs, typescript, formik, yuppie-cbd-gummies

---

In this article, we will understand the use and actual need of the Formik library. we will understand why we need an external library for form handling. And also we will use the yup library to validate the form. We will see the difficulties when not using these libraries then we will get an actual idea of the importance of Formik and Yup in dealing with forms.

Generally, we are using the form on almost all websites. so you need to deal with the forms. If we are using form handling without any library then it will very difficult to manage many input fields in a form. The code will become very repetitive and we need to manage multiple useState. Formik saves our headache to manage the multiple State variables and multiple handleChange functions.

### Create a project with Formik

here are some steps for creating the react project with redux.

### 1\. Create a react app with Vite builder

```javascript
npm init vite@latest Form-handling -- --template react-ts
```

### **2\. Go to the newly created folder**

here is the command for navigating to the folder

```javascript
cd Form-handling
```

### 3\. Install the Formik and Yup library

```javascript
npm install formik yup
```

### 4\. Now run the web App

```javascript
npm run dev
```

### Form handling without any external library

Here I will create a form with four fields and handle this form without any library.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685114704371/f392a758-d7f4-4acd-8a6e-f4efbc836269.png align="center")

```javascript
import { FC, useState } from "react";

type P = {};

const Form: FC<P> = () => {
  const [formState, setFormState] = useState({
    firstName: "",
    lastName: "",
    email: "",
    phoneNo: "",
  });

  return (
    <form className="h-screen flex flex-col items-center justify-center ">
      <div className="text-center shadow-xl space-y-3 p-4 rounded-lg">
        <div className="text-3xl font-bold my-4 ">Form</div>
        <div className="flex gap-2">
          <input
            type="text"
            value={formState.firstName}
            onChange={(e) => setFormState({...formState, firstName: e.target.value })}
            placeholder="Enter the First Name"
            className="border px-4 py-2 rounded-md focus:border-indigo-500 outline-none"
          />
          <input
            type="text"
            value={formState.lastName}
            onChange={(e) => setFormState({...formState, lastName: e.target.value })}
            className="border px-4 py-2 rounded-md focus:border-indigo-500 outline-none"
            placeholder="Enter the last Name"
          />
        </div>
        <div className="flex gap-2">
          <input
            type="email"
            value={formState.email}
            onChange={(e) => setFormState({...formState, email: e.target.value })}
            placeholder="Enter the email"
            className="border px-4 py-2 rounded-md focus:border-indigo-500 outline-none"
          />
          <input
            type="phone"
            value={formState.phoneNo}
            onChange={(e) => setFormState({...formState, phoneNo: e.target.value })}
            className="border px-4 py-2 rounded-md focus:border-indigo-500 outline-none"
            placeholder="Enter the phone no."
          />
        </div>
        <button className="px-4 py-2 rounded-md bg-indigo-500 hover:bg-indigo-600 text-white">
          Submit
        </button>
      </div>
    </form>
  );
};

export default Form;
```

In this form, there is four input field so to handle these field we have four handleChange functions. we have to manage the four state variables for it.

Now check it with the Formik library.

```javascript
import { FormikProps, withFormik } from "formik";
import { FC } from "react";
import * as Yup from "yup";

type P = {} & FormikProps<I>;

const FormikForm: FC<P> = ({ values, handleChange, handleSubmit }) => {
  return (
    <form
      className="h-screen flex flex-col items-center justify-center "
      onSubmit={handleSubmit}
    >
      <div className="text-center shadow-xl space-y-3 p-4 rounded-lg">
        <div className="text-3xl font-bold my-4 ">Form</div>
        <div className="flex gap-2">
          <input
            type="text"
            value={values.firstName}
            name="firstName"
            onChange={handleChange}
            placeholder="Enter the First Name"
            className="border px-4 py-2 rounded-md focus:border-indigo-500 outline-none"
          />
          <input
            type="text"
            value={values.lastName}
            name="lastName"
            onChange={handleChange}
            className="border px-4 py-2 rounded-md focus:border-indigo-500 outline-none"
            placeholder="Enter the last Name"
          />
        </div>
        <div className="flex gap-2">
          <input
            type="email"
            value={values.email}
            name="email"
            onChange={handleChange}
            placeholder="Enter the email"
            className="border px-4 py-2 rounded-md focus:border-indigo-500 outline-none"
          />
          <input
            type="phone"
            value={values.phone}
            name="phone"
            onChange={handleChange}
            className="border px-4 py-2 rounded-md focus:border-indigo-500 outline-none"
            placeholder="Enter the phone no."
          />
        </div>
        <button className="px-4 py-2 rounded-md bg-indigo-500 hover:bg-indigo-600 text-white ">
          Submit
        </button>
      </div>
    </form>
  );
};

function submit() {}

const initialState = {
  firstName: "",
  lastName: "",
  email: "",
  phone: "",
};
type I = typeof initialState;

const schema = Yup.object().shape({
  firstName: Yup.string().required("First Name is required"),
  lastName: Yup.string().required("Last Name is required"),
  email: Yup.string().required("Email is required"),
  phone: Yup.string().required("Phone is required"),
});
const FormikHOC = withFormik({
  mapPropsToValues: () => initialState,
  handleSubmit: submit,
  validationSchema: schema,
});

export default FormikHOC(FormikForm);
```

For the same things, we don't need to create the handleChange functions for everyone. we just need to provide the state object as initial values, the schema for validation and the handleSubmit function. than Formik will return us values as state variables and handleChange function. we don't need to create handleChange or handleSubmit functions and other handle functions manually.

Also for the validation part, we don't need to write custom validation. Yup makes it easy to write.

```javascript
const schema = Yup.object().shape({
  firstName: Yup.string().required("First Name is required"),
  lastName: Yup.string().required("Last Name is required"),
  email: Yup.string().required("Email is required"),
  phone: Yup.string().required("Phone is required"),
});
```

here is a small schema design of a validator. In this validation schema, I have set the required to all fields. because we are using Yup code is clean and Yup has minimized the code.

💕Thank you for reading. please share your suggestion in the comment section.