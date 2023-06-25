---
title: "Building a simple Todo app from scratch"
seoTitle: "Building a simple Todo app from scratch"
seoDescription: "Implemanting the basic concepts of ReactJS."
datePublished: Sun May 07 2023 17:24:38 GMT+0000 (Coordinated Universal Time)
cuid: clhdoow3w00010amw6b3b8zi4
slug: building-a-simple-todo-app-from-scratch
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683280250819/ce902d38-3e14-4208-9550-9379a29b9fea.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683480266630/9ba5f74f-6a2c-47be-bc99-528f4b05389b.png
tags: reactjs, create-react-app, tailwind-css

---

Here we will build a small Todo app from scratch. This will be good practice for the understanding of event handlers, Reusable Components Passing props and understanding states.

In this app, we will add features like adding a todo and making done todo. To style this web app we will use the tailwind CSS library. If you want you can use Bootstrap as well.

### **Step I: Setup for ReactJS and Tailwind CSS**

Here we can use vite builder for creating the web app. because it is very fast in comparison with the create-react-app method.

Here is an article for setup react with vite builder and tailwind CSS.

%[https://himanshuchauhan.hashnode.dev/mastering-responsive-ui-design-fylo-using-react-js] 

You can follow this blog to setup a ReactJS Project. here I have created a complete guide to setup the project.

### **Step II: Design the folder structure carefully**

Keeping a file in the correct position is a very important thing. In a good project, we have to create a lot of components and our project can contain many other types of files so Designing the folder structure correctly can help a lot.

![Folder Structure](https://cdn.hashnode.com/res/hashnode/image/upload/v1683368861586/f1b1f7d1-948c-423c-b851-36f928c68974.png align="center")

Here is the folder structure that I am following. This is not a very big project so it can be seen as we don't need to design this but It's important.

### **Step III: Building the App**

The main components of our todo app are `<Home />, <TodoShow />, <TodoItem />`. We are managing all the todo in the Home component. The Home component is the Parent of all components. All the states are managing here because it makes it easy to pass these values to its child components.

```javascript
import { FC, useState } from "react";
import Button from "../UI-Componnet/Button";
import Form from "./Form";
import TodoShow from "../UI-Componnet/TodoShow";

type P = {};

type todo = {
  title: string;
  status: boolean;
};

const Home: FC<P> = () => {
  const [FormToggle, setFormToggle] = useState(false);
  const [todo, setTodo] = useState<todo[]>([]);

  function handleClick() {
    setFormToggle(!FormToggle);
  }

  function addTodo(newTodo: string) {
    let temp = [...todo];
    let newObj = { title: newTodo, status: false };
    temp.push(newObj);
    setTodo(temp);
  }

  const markChecked = (indx: number) => {
    const temp = [...todo];
    temp[indx].status = !temp[indx].status;
    setTodo(temp);
  };

  return (
    <div className="my-10 max-w-6xl space-y-8 mx-auto ">
      <h1 className="text-3xl font-bold">Things to get done</h1>

      <TodoShow markChecked={markChecked} todo={todo} todoListType="false" />

      {FormToggle ? (
        <Form setFormToggle={setFormToggle} addTodo={addTodo} />
      ) : (
        <Button onClick={handleClick} mode="Primary">
          Add a todo
        </Button>
      )}

      <TodoShow markChecked={markChecked} todo={todo} todoListType="true" />
    </div>
  );
};
export default Home;
```

All the important components are under the **Home.tsx** and we are passing the functions or props from here.

Here I have created a common component to map the todos and checked todos. This component takes a String in input and according to this input component will act in two different ways.

```javascript
import { FC } from "react";
import TodoItem from "../Pages/TodoItem";

type P = {
  todo: { title: string; status: boolean }[];
  markChecked: (indx: number) => void;
  todoListType: "false" | "true";
};

const TodoShow: FC<P> = ({ todo, markChecked, todoListType }) => {
  let data = [...todo];

  if (todoListType == "false") {
    data = data.filter((item) => {
      return item.status + "" == todoListType;
    });
  }
  if (todoListType == "true") {
    data = data.filter((item) => {
      return item.status + "" == todoListType;
    });
  }

  if (data.length == 0) {
    return <p>Nothing to show</p>;
  }

  return (
    <div>
      <div>
        {todo.map((obj, indx) => {
          return (
            todoListType == obj.status + "" && (
              <TodoItem indx={indx} markChecked={markChecked} obj={obj} />
            )
          );
        })}
      </div>
    </div>
  );
};

export default TodoShow;
```

This component is just taking an array of todos and mapping it. I have created a small TodoItem component to render individual todo.

```javascript
import { FC } from "react";
import Input from "../UI-Componnet/Input";

type P = {
  obj: {
    title: string;
    status: boolean;
  };
  markChecked: (indx: number) => void;
  indx: number;
};

const TodoItem: FC<P> = ({ indx, obj, markChecked }) => {
  function handleChange() {
    markChecked(indx);
  }

  let extraClass = "";
  if (obj.status === true) {
    extraClass = " line-through ";
  }

  return (
    <div className="flex gap-1">
      <Input type="checkbox" onChange={handleChange} checked={obj.status} />
      <p className={"" + extraClass}>{obj.title}</p>
    </div>
  );
};

export default TodoItem;
```

This **TodoItem** component is just rendering the object that it is getting from props.

Here is the last important component Form.tsx. This component is responsible for creating a new todo. It will create and pass the todo to the Home component and after that Home component will pass it to TodoShow and then it will get rendered.

```javascript
import { FC, useState } from "react";
import Input from "../UI-Componnet/Input";
import Button from "../UI-Componnet/Button";

type P = {
  setFormToggle: (a: boolean) => void;
  addTodo: (t: string) => void;
};

const Form: FC<P> = ({ setFormToggle, addTodo }) => {
  const [todo, setTodo] = useState("");

  function addNewTodo() {
    if (todo.length > 2) {
      addTodo(todo);
    }
  }

  return (
    <div>
      <form
        className="flex flex-col space-y-8 rounded-md shadow-xl p-5"
        onSubmit={(e) => {
          e.preventDefault();
          setTodo("");
        }}
      >
        <h1 className="text-xl ">Create a Todo</h1>

        <Input
          placeholder="Enter a Todo"
          value={todo}
          onChange={(e) => setTodo(e.target.value)}
        />

        <div className="flex gap-2">
          <Button mode="Primary" onClick={addNewTodo}>
            Save
          </Button>
          <Button mode="Secondary" onClick={() => setFormToggle(false)}>
            Cancel
          </Button>
        </div>
      </form>
    </div>
  );
};

export default Form;
```

That's all about our to-do app. This web app is not about very high-level design or very advanced things but it is about understanding basic use of state and components.

GitHub Link: [Project Code Link](https://github.com/Himmu5/Todo)

Deployed Link: [Demo Link](https://todo-app-hashnode.netlify.app/)

❤️Thank you for reading and please share your suggestions in the comment section.