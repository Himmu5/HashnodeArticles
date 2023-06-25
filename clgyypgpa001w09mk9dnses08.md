---
title: "Understanding Props and State in ReactJS"
seoTitle: "Understanding Props and State in ReactJS"
seoDescription: "Here we will learn about React Props and States. These are very common terms that you will use during the programming with reactJS."
datePublished: Thu Apr 27 2023 10:08:28 GMT+0000 (Coordinated Universal Time)
cuid: clgyypgpa001w09mk9dnses08
slug: understanding-props-and-state-in-reactjs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683215084482/2c9f7b13-5b46-4edf-8a00-b26fefdc7b93.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683105605820/c77f4147-7908-4c49-b069-502bcebbe2ac.png
tags: props-in-reactjs, state-in-react, managing-props-and-stat

---

Here we will learn about React Props and States. These are very common terms that you will use during the programming with reactJS. Props and States both are items that are connected with the lifecycle of the react app. The term ReactJS lifecycle we will understand in further articles.

Props and State both can re-render the component. Props have some different things that can be shared with another component and State have its local scope for its component.

### **Component State**

The state is the local variable in the component to store state data. The state can not be modified outside the Component. The state is used for storing the local data of that component. The state is associated with a particular component.

```javascript
import { FC, useState } from "react";

type P = {};

const Name: FC<P> = () => {
  const [name, setName] = useState("Random Name");

  return <div>Welcome, {name}</div>;
};

export default Name;
```

here is this example I have created a component Name. This is a component to show the welcome message to the user. In this component name is a state variable that is created by useState hook. so it is a local state and we can't modify it from outside.

### **Component Props**

Component Props are like input for the component to control from outside. The developer can control the view of a component from the outside of the component. React components are made for reuse multiple times. props made it easy to change the view of the component.

```javascript
import { FC } from "react";

type P = {
  name:string
}

const Welcome:FC<P> = ({ name })=>{
  return <div>
    Welcome, {name}
  </div>
}

export default Welcome;
```

here in the above example, I have created a Component named Welcome. It is for showing a welcome message to the user. This component is getting the name in props. so this can be used in multiple web apps.

We need to create a component that can be used by outside. The component should be dumb and pure. The component's main responsibility should be getting props and just showing them.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682589886809/03e2a106-5592-4bb5-85b2-03f24ac41c1f.gif align="center")

Thank you for the reading... If you like you can also follow my other blogs. 💕💕