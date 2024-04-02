---
title: "Day 48: Linked list implementation with Python"
seoTitle: "Linked list implementation with Python"
seoDescription: "Welcome back to the Python Learning Series! Today marks the forty-sixth day of our journey, and we're diving into the fascinating world of Linked Lists."
datePublished: Tue Apr 02 2024 18:04:16 GMT+0000 (Coordinated Universal Time)
cuid: cluioutld000n08jvaab99w63
slug: day-48-linked-list-implementation-with-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1712080904524/824a3ed8-445b-4124-ab17-03b8307501ad.png
tags: python, queue

---

Welcome back to the Python Learning Series! Today marks the forty-sixth day of our journey, and we're diving into the fascinating world of Linked Lists.

## **Introduction to Linked Lists**

A Linked List is a fundamental data structure in computer science that consists of a sequence of elements, called nodes, where each node points to the next one in the sequence. Unlike arrays, which have contiguous memory allocation, linked lists use pointers to connect elements, allowing for dynamic memory allocation and flexibility in inserting and deleting elements.

## **Types of Linked Lists**

There are several types of Linked Lists, including:

1. **Singly Linked List**: Each node points to the next node in the sequence.
    
2. **Doubly Linked List**: Each node has pointers to both the next and previous nodes.
    
3. **Circular Linked List**: The last node points back to the first node, forming a circular structure.
    

In this blog, we'll focus on implementing a basic Singly Linked List in Python.

## **Implementing a Singly Linked List in Python**

```python
pythonCopy codeclass Node:
    def __init__(self, data=None):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        last_node = self.head
        while last_node.next:
            last_node = last_node.next
        last_node.next = new_node

    def prepend(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    def delete(self, key):
        current_node = self.head
        if current_node and current_node.data == key:
            self.head = current_node.next
            current_node = None
            return
        prev_node = None
        while current_node and current_node.data != key:
            prev_node = current_node
            current_node = current_node.next
        if current_node is None:
            return
        prev_node.next = current_node.next
        current_node = None

    def print_list(self):
        current_node = self.head
        while current_node:
            print(current_node.data, end=" ")
            current_node = current_node.next
        print()
```

## **Conclusion**

In conclusion, we've explored the concept of Linked Lists in Python. Linked Lists offer dynamic memory allocation and efficient insertion/deletion operations compared to arrays. We've implemented a basic version of a Singly Linked List, including methods like appending, prepending, and deleting nodes. Linked Lists are powerful data structures worth mastering for various programming tasks.

Thank you💕💕