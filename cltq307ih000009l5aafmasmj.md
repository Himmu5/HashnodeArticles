---
title: "Day 27: Asynchronous Programming (asyncio) in Python"
seoTitle: "Asynchronous Programming (asyncio) in Python"
seoDescription: "Exploring the Asynchronous programming with python"
datePublished: Wed Mar 13 2024 17:35:02 GMT+0000 (Coordinated Universal Time)
cuid: cltq307ih000009l5aafmasmj
slug: day-27-asynchronous-programming-asyncio-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710327219155/85ec8e55-b6e8-4af4-b5ba-6ef1eed14d87.png
tags: python, asynchronous, asyncio

---

Welcome to the blog! Today, we delve into the intricate world of asynchronous programming. While initially challenging, mastering this topic can significantly elevate the quality of your software. Join me on the twenty-seventh day of my Python learning journey as we explore this essential concept.

### Asynchronous Programming

There are two types of programming;

* **Synchronous Programming**: A synchronous program executes one step at a time, requiring each statement to complete its execution before proceeding to the next. In essence, if a program consists of four statements, each subsequent statement waits for the previous one to finish executing before proceeding.
    
* **Asynchronous Programming**: In asynchronous programming, each step executes independently without waiting for the completion of the previous one. For instance, in a program with four statements, the execution begins with the first statement, but it can jump to the next statement before completing the current one. the running statement will run parallelly in the background.
    

```json
import asyncio
import time
import requests

# URL of the image you want to download
image_url = "https://images.unsplash.com/photo-1512100356356-de1b84283e18?q=80&w=1975&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
async def first():


    # Send a GET request to the image URL
    response = requests.get(image_url)

    # Check if the request was successful (status code 200)
    if response.status_code == 200:
        # Open a file in binary write mode and write the content of the response to it
        with open("image1.jpg", "wb") as f:
            f.write(response.content)
    print('First')
 
async def second():
     # Send a GET request to the image URL
    response = requests.get(image_url)

    # Check if the request was successful (status code 200)
    if response.status_code == 200:
        # Open a file in binary write mode and write the content of the response to it
        with open("image2.jpg", "wb") as f:
            f.write(response.content)
    print('second')
 
async def third():
    # Send a GET request to the image URL
    response = requests.get(image_url)

    # Check if the request was successful (status code 200)
    if response.status_code == 200:
        # Open a file in binary write mode and write the content of the response to it
        with open("image3.jpg", "wb") as f:
            f.write(response.content)
    print('third')

async def main():
    res = await asyncio.gather(
        first(),
        second(),
        third()
    )
    print("res: ",res)

asyncio.run(main())
    
```

This code is to download three images with asyncio.

### Conclusion

In conclusion, asynchronous programming offers a significant departure from synchronous programming by enabling independent execution of tasks without waiting for each other to complete. This approach can greatly enhance the efficiency and responsiveness of software applications, especially in scenarios involving I/O-bound operations such as downloading images from URLs. By utilizing asynchronous techniques such as asyncio in Python, developers can leverage parallelism and concurrency to improve the overall performance and user experience of their applications.

Thankyou💕💕💕