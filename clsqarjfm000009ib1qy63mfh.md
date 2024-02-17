---
title: "Day 2: Variables and Assignments in Python"
seoTitle: "Day 2: Variables and Assignments in Python"
seoDescription: "Exploring Python Basics: A Dive into Variables and Assignments"
datePublished: Sat Feb 17 2024 16:32:33 GMT+0000 (Coordinated Universal Time)
cuid: clsqarjfm000009ib1qy63mfh
slug: day-2-variables-and-assignments-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708180070077/0213737b-cc1a-42f9-92bb-ff3e850c3c0d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1708187827813/8fdee516-8169-4789-b7d3-b9279bdfd94b.png
tags: python, learninpublic, scaleup

---

On the second day of my Python learning adventure, I delve into the fundamentals of variables and assignments. As I navigate through this territory, I'm pleased to discover how smoothly things are progressing. Basic concepts surrounding Python variables have been absorbed, and I'm eager to share my newfound knowledge through illustrative code snippets.

### Variables

Variable are the key to access some type of data. It works as lable to a data. We can access our data with the help of their address and that address is stored in a variable. Variables also helps us to call some data with a understandable name. we can make them more intuitive.

```python
name = "Himanshu"
age = 23
address = "Rishikesh"
print("A variable containing my name : ",name)
```

In the given example if a programmer wants to store a name on a variable then he/she can give a variable name like name or username so another programmer can understand what is stored in that variable.

### Assignment operator

Assignments in Python are denoted by the '=' symbol. This operator is used to store data into a variable. For example, to store a user's name into a variable called 'name', we simply write 'name = "User name"'. The '=' operator assigns the value to the variable. It's important to note that the '==' operator, on the other hand, is used for comparison, not assignment. These operators have distinct purposes and use cases.

Note: we can delete a variable with del variable\_name

```python
name = "Himanshu"
print("name variable before deleting : ",name)
delete name
print("After deleting the variable : ",name)
```

I've initialized a variable named 'name' with a specific value. Initially, I print the value stored in 'name'. However, upon executing the command 'del name', I delete the variable itself. Consequently, if an attempt is made to print the 'name' variable thereafter, an error will be raised.