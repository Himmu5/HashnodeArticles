---
title: "Handling props and state in ReactJS classbassed component"
seoTitle: "Handling props and state in ReactJS classbassed component"
seoDescription: "Here is the article for showing the state and props management in class-based components."
datePublished: Mon May 01 2023 10:07:59 GMT+0000 (Coordinated Universal Time)
cuid: clh4og99e000309mkdaf2brff
slug: handling-props-and-state-in-reactjs-classbassed-component
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683215119484/8a0cabcf-4b02-4180-bec8-be7e9d545000.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682935630010/247812ff-5e7b-4630-847a-138129ed1638.png
tags: props, states-in-react, difference-between-prop-and-state-in-react

---

Here is the article for showing the state and props management in class-based components. Chances are less anybody is creating a new project in class-based components. Functional components are more popular than class-based components. Because to learn class-based components a programmer should have a good understanding of OOPs concepts. OOPs makes some difficulty with the beginner-to-learn class component.

### **handling State with Class component**

If you are familiar with functional components we can use hooks there to create a state variable. here we do not have hooks but we can directly create a state variable in the constructor. We don't need to create it by calling hooks.

```javascript

type P = {};
type S = {
  userName: string;
};

class Welcome extends Component<P, S> {
  constructor(props: P) {
    super(props);

    this.state = {
      userName: "Himanshu",
    };
  }

  render(): ReactNode {
    return <div>Welcome, {this.state.userName}</div>;
  }
}

export default Welcome;
```

In the above example, there is a component named Welcome. It is to show the welcome message to a new user. Managing the state in the class component is different from the functional component. here we need to pass an object to a nonstatic variable state. we can create multiple states just using this.

`the code is in Typescript If not comfortable then you can ignore the typings in it.`

And for setting a new value in the state react provides us a function that takes a new object and a new state value in it. Only an updated state key should be added to it. we don't need to spread all values in it.

```javascript
function changeState(){
    this.setState({userName:"Akhil Tiwari"})
}
```

This function is to update the user name in it. if there is more than one state Like userId or userPhone then also we don't need to spread all the values in the setState function.

### **handling Props with Class component**

Here we can get props in a props object. In the class component, there is no such big difference in using props. here just we don't need to take from parameters we can just call it with this function.

```javascript

type P = {
  userName:string
};
type S = {};

class Welcome extends Component<P, S> {
  
constructor(props: P) {
    super(props);
  }

  render(): ReactNode {
    return <div>Welcome, {this.props.userName}</div>;
  }
}
export default Welcome;
```

In the above example, we are getting the props and just showing them.

Passing the props are same as the function-based component. we just need to write the name as a tag in the parent component and pass the props in attributes.

```javascript
import { Component, ReactNode } from "react";
import Welcome from "./Welcome"

class App extends Component{
  render(): ReactNode {
      return <div>
        <Welcome userName="Himanshu Chauhan" />
      </div>
  }
}
export default App;
```

In this example, I am passing the username as a prop in the Welcome component.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682904352680/b65d55fa-1d97-424c-a5d5-2309a9eae78a.gif align="center")

Thank you for the reading😍😍😍. I hope this will help you a lot. Please comment with suggestions or queries.