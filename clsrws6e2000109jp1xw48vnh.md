---
title: "Day 3: Operators and Expressions in python"
seoTitle: "Operators and Expressions in Python"
seoDescription: "Mastering Operators: Unveiling Expressive Python Syntax"
datePublished: Sun Feb 18 2024 19:36:40 GMT+0000 (Coordinated Universal Time)
cuid: clsrws6e2000109jp1xw48vnh
slug: day-3-operators-and-expressions-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708272478355/88afcbe2-bb8f-4511-b5da-d0706cd65a10.png
tags: python, python-beginner, learn-in-public

---

On the third day of my Python learning journey, I delve into the realm of operators and expressions. Python boasts a rich repertoire of operators, each serving distinct purposes. In this blog post, I'll dissect two fundamental topics within Python: operators and expressions. Let's unravel the intricacies of Python's operator support as we explore these foundational concepts together.

### Operators

Operators in Python enable actions to be performed on variables or data. Python boasts a diverse set of operators, including arithmetic, comparison, and logical operators, among others. These operators facilitate various operations, contributing to the language's versatility and power.

1. **Arithmetic Operator**: Arithmetic operators are used to perform mathematical operations between variables. we have many Arithmetic operators in Python like `+` , `-`, `/`*,*`**` etc.
    
    ```python
    num1 = 10
    num2 = 20
    # here + is arithmetic operator
    add = num1 + num2
    ```
    
2. **Comparison Operator**: These operators are used to compare two values. like greater, smaller, or equal. they always return the boolean value true or false.
    
    ```python
    num1 = 10
    num2 = 20
    # here > is comparison operator to check greater value.
    print("Greater or not :",num1 > num2)
    ```
    
3. **Logical Operator**: Logical operators are used to get some common value from those. like and, or, and not.
    
    ```python
    num1 = 10
    num2 = 20
    # Here we are using and operator to check two conditions
    ans = (num1 < num2) and (num2 < num1)
    # we will get false in ans
    ```
    
4. **Membership Operators**: The `in` and `not in` operators in Python serve the purpose of checking whether a value exists within a given data structure, such as a list or tuple. These operators provide a concise and efficient way to determine the presence or absence of a value, offering flexibility and ease of use in Python programming.
    
5. **Identity Operators:** Identity operators are used to compare the memory location of two objects. The identity operators are `is` and `is not`.
    

By this operator, we can perform many manipulation operations in data.

### Expressions in python

Expressions in Python encompass combinations of values and operations aimed at yielding a singular result. They encompass a range of types, including arithmetic, logical, or a blend of both. These versatile constructs are fundamental to Python programming, allowing for the manipulation and evaluation of data in diverse contexts.

1. **Arithmetic Expressions:** These are combinations of multiple Arithmetic operators.
    
    ```python
    ans = (5 + 4) - (3 + 2)
    print("Answer of this arithmetic operation is : ",ans)
    ```
    
2. **Logical Expressions**:
    
    ```python
    num1 = 10
    num2 = 20
    ans = (num1 < num2) and (num2 < num1)
    # we will get false in ans
    ```
    
3. **Relational Expression:** In arithmetic expressions involving relational operators (&gt;, &lt;, &gt;=, &lt;=), calculations occur on both sides of the operator before comparison takes place. The resulting boolean output indicates the relationship between the evaluated expressions. Such expressions, commonly known as Boolean expressions, play a crucial role in decision-making and flow control within Python programs.
    
    ```python
    a = 10
    b = 6
    c = 20
    d = 15
      
    p = (a + b) >= (c - d) 
    print(p)
    ```
    
4. **Function call Operations**: When a function is invoked with appropriate arguments, it triggers function call operations. These operations involve the execution of the function's code block, processing the provided arguments, and returning a result if applicable. Function calls are integral to program execution in Python, facilitating modularization and code reusability.
    
    ```python
    def add(a,b):
      return a+b
    
    ans = add(5,4)
    # printing the addition of two numbers
    print("Addition of two numbers is :",ans)
    ```
    

### Conclusion

In conclusion, operators and expressions constitute fundamental aspects of Python programming, offering a robust framework for manipulating and evaluating data.

Operators, including arithmetic, comparison, logical, membership, and identity operators, enable a wide array of actions to be performed on variables and data structures. They play a crucial role in facilitating various operations, contributing to Python's versatility and power.

Armed with a deeper understanding of operators and expressions, Python programmers can navigate complex tasks with ease, leveraging these foundational concepts to build efficient and scalable solutions. Additionally, function call operations serve as integral components of Python programs, enabling modularization and code reusability, further enhancing the language's flexibility and efficiency.

Thank you 💕💕💕