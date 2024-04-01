---
title: "Day 46: Queue Implementation using Python"
seoTitle: "Queue Implementation using Python"
seoDescription: "Today is the forty-sixth day of the Python learning series and In this blog, we will discuss the Queue data structure. "
datePublished: Mon Apr 01 2024 17:33:38 GMT+0000 (Coordinated Universal Time)
cuid: cluh8bl3r000a08lfgdwneyh0
slug: day-46-queue-implementation-using-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711990790199/6cff52d0-bbf1-45af-9ac6-eb3c7b4562e9.png
tags: python, queue

---

Today is the forty-sixth day of the Python learning series and In this blog, we will discuss the Queue data structure.

### Queue

A queue is a fundamental data structure in computer science that follows the First-In-First-Out (FIFO) principle. It operates much like a line of people waiting to be served: the first person who enters the line is the first one to be served, and as more people join the line, they join at the end and wait until it's their turn to be served.

```python
class Queue:
    def __init__(self):
        self.items = []

    def enqueue(self, item):
        self.items.append(item)

    def dequeue(self):
        if not self.is_empty():
            return self.items.pop(0)
        else:
            raise IndexError("Dequeue from empty queue")

    def peek(self):
        if not self.is_empty():
            return self.items[0]
        else:
            raise IndexError("Peek from empty queue")

    def is_empty(self):
        return len(self.items) == 0

    def size(self):
        return len(self.items)
```

### Conclusion

In conclusion, we've covered the Queue data structure in this blog. A queue follows the First-In-First-Out (FIFO) principle, similar to a line of people waiting to be served where the first person who enters is the first one served. We discussed the implementation of a Queue class in Python, including operations like enqueue (adding to the end), dequeue (removing from the front), peek (viewing the front element), checking if the queue is empty, and getting its size.

Thank you💕💕