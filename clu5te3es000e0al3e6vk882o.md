---
title: "Day 38: Web Socket in Python"
seoTitle: "Web Socket in Python"
seoDescription: "Real-Time Collaboration Made Easy: WebSocket Integration in Python"
datePublished: Sun Mar 24 2024 17:50:13 GMT+0000 (Coordinated Universal Time)
cuid: clu5te3es000e0al3e6vk882o
slug: day-38-web-socket-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711299835866/254eea0d-5d51-403b-a646-2c3575c06f5d.png
tags: websockets, python, 2articles1week

---

Welcome to the thirty-eighth installment of our Python Learning Series! Today, we delve into the fascinating realm of websockets in Python.

Websockets are a powerful communication protocol that allows real-time, full-duplex communication between a client (such as a web browser) and a server. Unlike traditional HTTP requests, which are stateless and require a new connection for each request, WebSockets enable persistent connections, enabling efficient data exchange for applications like chat systems, online gaming, and live data streaming.

### Setup Websocket in FastAPI

First, make sure you have the `websockets` library installed. You can install it using pip:

```python
pip install websockets
```

Now, let's create a simple WebSocket server:

```python
import asyncio
import websockets

async def handle_websocket(websocket, path):
    # Logic to handle websocket messages
    async for message in websocket:
        # Process incoming message
        print(f"Received message: {message}")
        # Echo the message back to the client
        await websocket.send(message)

async def start_server():
    server = await websockets.serve(handle_websocket, 'localhost', 8765)
    print("Websocket server started...")
    await server.wait_closed()

asyncio.run(start_server())
```

### **Creating a WebSocket Client**

To test our websocket server, let's create a simple websocket client:

```python
import asyncio
import websockets

async def send_message():
    async with websockets.connect('ws://localhost:8765') as websocket:
        message = input("Enter a message: ")
        await websocket.send(message)
        response = await websocket.recv()
        print(f"Received response: {response}")

asyncio.run(send_message())
```

In this client code, we establish a WebSocket connection to our server running on [localhost](http://localhost) port 8765. We send a message entered by the user and print the response received from the server.

### **Conclusion**

WebSockets open up exciting possibilities for building interactive and real-time web applications in Python. Whether you're creating a chat application, a live data dashboard, or a multiplayer game, understanding how to use websockets can greatly enhance your development capabilities.

Thank you💕💕