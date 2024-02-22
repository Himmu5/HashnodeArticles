---
title: "Day 7: Input/Output Handling (I/O) in Python"
seoTitle: "Input/Output Handling (I/O) in Python"
seoDescription: "Exploring Python's Input/Output Operations: From Basics to Advanced Techniques"
datePublished: Thu Feb 22 2024 17:54:34 GMT+0000 (Coordinated Universal Time)
cuid: clsxiw9yj000009jrecd8f1w2
slug: day-7-inputoutput-handling-io-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708614828908/f9188453-59ff-41ef-837b-f876a6b46a6a.png
tags: python, learning, 2articles1week, input-output, learninpublic

---

In this blog, I'll share insights gained during my 100-day Python learning journey, focusing on Python's input/output (I/O) handling. Join me as I delve into the intricacies of Python's I/O operations, from basic concepts to advanced techniques. Let's optimize our code and streamline data handling for efficient programming.

### Input/Output Operations

Input/Output (I/O) operations in programming involve interactions with users or systems. In Python, we have built-in functions like `input()` to receive user input. Consider building a game, such as a car racing game, where user responses are crucial for controlling the vehicle's movements, like turning left or right. Python's `input()` function allows us to seamlessly integrate user interactions into our programs, enhancing the gaming experience and enabling dynamic user engagement.

This Python snippet prompts the user for input and then prints the entered value:

```python
name = input("enter your name : ")
# this print function is used to print name of user.
print("user's name is : ",name)
```

Python provides built-in functions for generating output from the system. The `print()` function, for example, allows us to display output directly to the console. Additionally, we can create files to store output as responses. These capabilities enable us to efficiently communicate results and responses within our Python programs.

Printing the output -

```python
# taking a number from user as input
number = int(input("Enter a number: "))
# Showing output by printing of terminal
print("User has entered: ",number)
```

Writing output on text file:

```python
# this method will open a file called test.txt 
# or create it if not exist
# And it will write some text on it.
def my_write():
 file = open("test.txt",'w')
 file.write("Hello world! \n")
 file.write("My name is Himanshu\n")   
 file.write("I am from Rishikesh")
my_write()
```

Reading a file:

```python
file = open("test.txt",'r')
# printing the file content
print("file : ",file.read())
```

Try to build a small basic calculator:

```python
number1 = int(input("Enter the first number: "))
number2 = int(input("Enter the Second number: "))
operator = input("Enter the operator: ")
if operator == '+':
    print("Addition: ",number1 + number2)
elif operator == '-':
    print("Subtraction: ",number1 - number2)
elif operator == '*'
    print("Multiplication: ",number1 * number2)
elif operator == '/':
    print("Division: ",number1 / number2)
else:
    print("Invalid operator!!!")
```

### **Conclusion**

In this blog post, we embarked on a journey through Python's input/output (I/O) handling, exploring its fundamental concepts and advanced techniques. Through my 100-day Python learning journey, we've discovered how Python's built-in functions like `input()` and `print()` empower us to interact with users and systems seamlessly.

We delved into the intricacies of Python's I/O operations, recognizing their importance in various applications, including game development, where user responses are pivotal. Python's ability to integrate user interactions into programs, such as car racing games, enhances the gaming experience and fosters dynamic user engagement.

Furthermore, we explored the diverse capabilities of Python's output handling, from displaying output directly to the console with `print()` to storing output in files for efficient communication within programs.

Through practical code examples, we demonstrated how to prompt users for input, print output to the terminal, write output to text files and even build a basic calculator using Python's input/output functionalities.

Thankyou ❤️❤️