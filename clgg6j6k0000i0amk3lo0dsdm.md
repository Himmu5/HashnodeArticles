---
title: "Mastering Responsive UI Design FYLO using  React JS"
datePublished: Fri Apr 14 2023 06:39:54 GMT+0000 (Coordinated Universal Time)
cuid: clgg6j6k0000i0amk3lo0dsdm
slug: mastering-responsive-ui-design-fylo-using-react-js
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/zNRITe8NPqY/upload/fc0a72708cb371f4d20f1a859af6f7cb.jpeg

---

Here I have created a small responsive landing page. It is responsive and dark mode is also a nice feature in it. To create this UI we will use tailwind css, React and Typescript.

First, we have to set up a React project also install tailwind CSS as dev-dependencies. we will use vite builder to build our React project.

### **Step 1: Create a Project folder**

Open your terminal to the folder where you want to install React Project.

```javascript
npm create vite@latest your-project-name -- --template react
```

you need to replace your-project-name with your project name. we have to write `-- -- template react` to specify that we are building react project.

### **Step 2 – Reach Your Project Folder**

```javascript
cd Fylo-UI
```

This command will navigate you to your project folder.

### **Step 3 – Install Tailwind CSS**

To install Tailwind CSS to your project this command you need to write this on the terminal.

```javascript
npm install -D tailwindcss postcss autoprefixer
```

After installing these dependencies your package.json file looks like this:

```javascript
{
  "name": "fylo-ui",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-icons": "^4.8.0",
    "react-scroll": "^1.8.9"
  },
  "devDependencies": {
    "@types/react": "^18.0.28",
    "@types/react-dom": "^18.0.11",
    "@types/react-scroll": "^1.8.6",
    "@vitejs/plugin-react": "^3.1.0",
    "autoprefixer": "^10.4.14",
    "postcss": "^8.4.21",
    "tailwindcss": "^3.2.7",
    "typescript": "^4.9.3",
    "vite": "^4.2.0"
  }
}
```

### **Step 4 – Generate the Configuration Files**

```javascript
npm tailwindcss init -y
```

This command generates `tailwind.config.cjs` and`postcss.config.cjs` configuration files, also known as config files. They help you interact with your project and customize everything.

### **Step 5 – Configure Source Paths**

Copy and paste the below-given code to your project.

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  darkMode: 'class',
  theme: {
    extend: {
      colors :{
        darkBlue : "#1C2341",
        darkBluePlue : "#0B1523"
      } , 
      backgroundImage: {
        'main': "url('./public/bg.svg')"
      }
    },
  },
  plugins: [],
}
```

This code will copy pasted in tailwind.config.cjs.

And In index.js add the below code.

```javascript
@tailwind base;
@tailwind components;
@tailwind utilities;
```

And now the project setup is completed.

Deploy link: [https://fylo-ui-design.netlify.app/](https://fylo-ui-design.netlify.app/)

Github: [https://github.com/Himmu5/Fylo-UI](https://github.com/Himmu5/Fylo-UI)