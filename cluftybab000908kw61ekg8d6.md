---
title: "Day 45: Stack implementation using Python"
seoTitle: "Stack implementation using Python"
seoDescription: "Welcome to the forty-fifth day of our Python learning series! In today's blog, we'll delve into implementing a stack data structure."
datePublished: Sun Mar 31 2024 18:03:38 GMT+0000 (Coordinated Universal Time)
cuid: cluftybab000908kw61ekg8d6
slug: day-45-stack-implementation-using-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711908211867/b49f2588-89cf-4686-9e33-7b6ea82fc474.png
tags: python, stack

---

Welcome to the forty-fifth day of our Python learning series! In today's blog, we'll delve into implementing a stack data structure.

### Stack

A stack is a fundamental data structure in computer science that follows the Last-In-First-Out (LIFO) principle. It is named so because it behaves like a stack of plates, where the last plate placed on top is the first one to be removed.

```python
class Stack:
    def __init__(self):
        self.items = []

    def is_empty(self):
        return len(self.items) == 0

    def push(self, item):
        self.items.append(item)

    def pop(self):
        if not self.is_empty():
            return self.items.pop()
        else:
            raise IndexError("pop from an empty stack")

    def peek(self):
        if not self.is_empty():
            return self.items[-1]
        else:
            raise IndexError("peek from an empty stack")

    def size(self):
        return len(self.items)
```

```python
stack = Stack()

stack.push(10)
stack.push(20)
stack.push(30)

print("Stack size:", stack.size())  # Output: 3
print("Top element:", stack.peek())  # Output: 30

print("Popped element:", stack.pop())  # Output: 30
print("Stack size after pop:", stack.size())  # Output: 2
```

### Conclusion:

In today's blog, we delved into the implementation of a stack data structure in Python. A stack, adhering to the Last-In-First-Out (LIFO) principle, mimics a stack of plates where the last plate placed atop is the first to be removed.

Thank you💕💕