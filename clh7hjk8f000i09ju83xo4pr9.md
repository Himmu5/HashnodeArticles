---
title: "Handling Events in a ReactJS component"
seoTitle: "Handling Events in a ReactJS component"
seoDescription: "Events in React are the actions that can be performed when the user clicks on a button or check uncheck a checkbox or writes some text in the input."
datePublished: Wed May 03 2023 09:17:55 GMT+0000 (Coordinated Universal Time)
cuid: clh7hjk8f000i09ju83xo4pr9
slug: handling-events-in-a-reactjs-component
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683014276170/8f0d1c53-f4f9-456f-982e-1ed62c9db354.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683105463737/620a1304-70f0-4e5c-9dd3-f9b7b8cf91d5.png
tags: reactjs, events

---

In the following blog, we will learn about handling Events in a React App.

Events in React are the actions that can be performed when the user clicks on a button or check uncheck a checkbox or writes some text in the input. React has all the Events like normal HTML events.

In React we use the camelCase convention when writing Events. For example `onClick, onChange etc.`

```javascript
import { FC } from "react";

type P ={}
const Test:FC<P> = ()=>{
    
    function handleChange(){
        // code on click 
    }

    return <div>
        <button onClick={handleChange}>click me</button>
    </div>
}
export default Test;
```

here I have created a Test Component that has a button click me. when the user will click on the button the handleChange function will be triggered.

When using we don't need to call actionListener.Instead, just provide a listener when the element is initially rendered.

### **Handling events in Classbassed Components**

When working in class-based components we can use these listeners by this keyword. a function call is performed in the reference with the class object. so we need to bind the function with the object of the class.

```javascript
type P = {};
type S = { Toggle: boolean };

class Toggle extends Component<P, S> {
  constructor(props: P) {
    super(props);

    this.state = {
      Toggle: false,
    };
  }

  toggleFunc() {
    this.setState({ Toggle: !this.state.Toggle });
  }

  render(): ReactNode {
    return (
      <div>
        <button onClick={this.toggleFunc}>Click me</button>
      </div>
    );
  }
}
export { Toggle };
```

In the above example, there is a component named Toggle. here is a button to call a function toggleFunc that will toggle the state.

### **Passing the argument to listeners**

We can pass some info or data in arguments to use it while running the function.

```javascript
import { FC } from "react";

type P ={}
const AddFunction:FC<P> = ()=>{

  const square = (num:number) =>{
    return num * num;
  }

    return <div>
        <button onClick={()=>square(5)}>square</button>
    </div>
}
export default AddFunction;
```

here I am passing the number 5 in an argument while calling it.

Thank you for the reading. Please write your valuable suggestion in the comment section.🥰