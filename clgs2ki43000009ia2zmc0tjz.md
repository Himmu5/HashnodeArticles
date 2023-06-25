---
title: "Building your first ReactJS component"
seoTitle: "Building your first ReactJS component"
seoDescription: "In this blog, we will create a ReactJs component from scratch. During the create this component we will also see how to set up a react application too."
datePublished: Sat Apr 22 2023 14:22:12 GMT+0000 (Coordinated Universal Time)
cuid: clgs2ki43000009ia2zmc0tjz
slug: building-your-first-reactjs-component
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683215045673/0b760585-0f76-4855-bf6f-aa9e86572464.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683105556546/360e8cec-d3d9-4d24-940e-4d9b03878f16.png
tags: reactjs, components

---

In this blog, we will create a ReactJs component from scratch. During the create this component we will also see how to set up a react application too. We will use vite builder for our React application because it is lightweight and faster.

1. **Setting up environment**
    
    ```javascript
    npm create vite@latest test-app -- --template react
    ```
    
    Now go to this folder and install the packages.
    
    ```javascript
    cd test-app
    ```
    
    Then you need to install the packages. for this command is given below.
    
    ```javascript
    npm install
    ```
    
2. **Create a new File name Button.tsx**
    
    The component is a reusable code in React which can be a function or a class. so will create a Button component in the function-based component and class-based component both.
    
    Function-based components are pure javascript functions.
    
    ```javascript
    import { ButtonHTMLAttributes, FC , ReactNode } from 'react';
    
    type P = {
        children: ReactNode,
    } & ButtonHTMLAttributes<HTMLButtonElement>
    
    const Button: FC<P> = ({ children, ...rest }) => {
        return <>
            <button {...rest}>{children}</button>
        </>
    }
    
    export default Button;
    ```
    
    The same Button component is in the class-based approach.
    
    ```javascript
    import { Component, ReactNode } from "react";
    
    type S = {}
    
    type P = {
        children: ReactNode
    }
    
    class Button extends Component<P, S>{
        constructor(props: P) {
            super(props);
        }
    
        render(): ReactNode {
            return <div>
                <button {...this.props}>{this.props.children}</button>
            </div>
        }
    }
    export default Button;
    ```
    
    These components are reusable so a component can be used in another component. We just have to import it.
    

In React, Import and Export statements are used to manage the way we create and use components. By using the `export` keyword on a function or class, we can make that component available to other modules using named exports or default exports.

Here is a code example of named exports:

```javascript
export function Component1() {
  return <h1>This is component 1</h1>;
}

export function Component2() {
  return <h1>This is component 2</h1>;
}
```

Here, we are using the `export` keyword to explicitly specify which components we want to make available outside this module. We can then import these components like this:

```javascript
import { Component1, Component2 } from './components';
```

Here is a code example of a default export:

```javascript
export default function MyComponent() {
  return <h1>This is my component</h1>;
}
```

Here, we are using the `export default` syntax to export the component without giving it a specific name. We can then import this component like this:

```javascript
import MyComponent from './components';
```

Notice that we didn't need to use the curly braces when importing a default export. This is because there can be only one default export per module.

Thank you for the reading. make sure to leave a comment.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682173277194/7574dfe6-65dd-42fa-90d8-000a71a6c69e.gif align="center")