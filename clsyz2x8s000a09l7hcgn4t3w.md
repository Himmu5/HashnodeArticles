---
title: "Day 8: Error Handling in Python"
seoTitle: "Error Handling in Python"
seoDescription: "Demystifying Error Handling in Python: A Beginner's Guide"
datePublished: Fri Feb 23 2024 18:15:24 GMT+0000 (Coordinated Universal Time)
cuid: clsyz2x8s000a09l7hcgn4t3w
slug: day-8-error-handling-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708684073601/79148683-37ee-4e9a-9c68-00ede41bf134.png
tags: python, error-handling, learning, day8

---

On my eighth day of learning Python, I want to share my insights into error handling. When writing code in any programming language, encountering errors is inevitable. However, understanding error handling can prevent our code from abruptly halting. Let's delve into the basics of error handling in Python.

### Error

Errors can disrupt the flow of a program, halting its execution. They typically stem from mistakes made by the programmer or system malfunctions. Errors come in two main forms: syntax errors and exceptions. Syntax errors arise from programmer mistakes, such as misspelling keywords or writing code incorrectly.

Syntax error:

```python
print("Hello world"  # missing closing parenthesis
```

This code will produce a syntax error because it lacks a closing parenthesis for the `print()` function call.

### Exceptions:

An exception occurs when a situation arises that is not covered by the code, even though the code itself is correctly written. This often happens when user input does not adhere to the specified rules. Additionally, exceptions can occur for various other reasons beyond user input, leading to unexpected behavior in the program.

**Type of exception**:

**ValueError**: A `ValueError` is raised when a function or operation receives an incorrect type of value.

```python
num = int(input("Enter a number: "))
print("user have entered : ",num)
```

> Enter a number: hima ERROR! Traceback (most recent call last): File "", line 1, in ValueError: invalid literal for int() with base 10: 'hima'

Entering a string or any other data type instead of a number in the above code snippet will result in a `ValueError`.

**IndexError:** Attempting to access an invalid index of a list will result in an `IndexError`.

```python
names = [ "Himanshu","Abhishek","Manav","Parvesh" ]
print(names[0])
# this line will print Himanshu
print(names[6])
# But this line throw IndexError exception
```

> ERROR! Himanshu Traceback (most recent call last): File "", line 4, in IndexError: list index out of range

ZeroDivisionError**:** Raised when an arithmetic error occurs, such as a division by zero.

```python
num = 10
print(num/0)
```

> ERROR! Traceback (most recent call last): File "", line 4, in ZeroDivisionError: division by zero

**Handle Exceptions:**

We use a try-except block to handle this exception. The code that we want to safeguard goes under the try block. If this code encounters an error, the except block is executed to handle the exception gracefully.

```python
try:
    # our code
except:
    # handle exception here
```

After implementing try-except blocks, the code will continue to execute smoothly for other actions even if an exception occurs and is handled gracefully. This helps prevent the program from crashing due to unexpected errors.

```python
try:
    num = float(input("Enter the number: "))
    print("User have entered: ",num)
except:
    print("except block")
    # handle exception here
```

The except block serves to catch and handle errors or exceptions that may occur in the try block. By providing a mechanism to handle exceptions, the except block can prevent the program from crashing and allow it to gracefully recover from unexpected situations. Therefore, yes, the except block can indeed save us from errors or exceptions by providing a way to handle them appropriately.

### Conclusion

In this blog, we covered the basics of error handling in Python, crucial for maintaining code stability. We distinguished between syntax errors and exceptions, exploring examples like ValueError, IndexError, and ZeroDivisionError. We introduced the try-except block as a key mechanism for gracefully handling exceptions, ensuring smooth program execution. By mastering error handling, developers can write more robust code, enhancing user experience and software reliability.

Thankyou ❤️❤️