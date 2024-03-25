---
title: "Day 39: Server Side Rendering in Python"
seoTitle: "Server Side Rendering in Python"
seoDescription: "Unlocking the Power: Exploring Server-Side Rendering with Python"
datePublished: Mon Mar 25 2024 18:48:20 GMT+0000 (Coordinated Universal Time)
cuid: clu7awp0v000208l62w5qaspw
slug: day-39-server-side-rendering-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711389638998/f659e8c1-ad4e-457a-9fce-50fc5b0c27ff.png
tags: python, server-side-rendering, fastapi, 2articles1week

---

Welcome to the thirty-ninth blog in our Python learning series! In this post, we'll delve into the realm of Server-Side Rendering in Python. I'll share my latest insights and discoveries on this topic, demonstrating how to create and render pages using the FastAPI server. Let's dive in and explore the power of Server-Side Rendering in Python together!

### Server-side rendering

Server-side rendering (SSR) is a technique used in web development where the server generates the HTML content of a web page and sends it to the client's browser. This is particularly useful for rendering dynamic content, handling SEO requirements, and improving initial page load performance.

To implement Server-Side Rendering in a FastAPI application, you typically use a templating engine like Jinja2 or Mako.

**Steps to render some pages:**

* Installing dependencies
    
    ```python
    pip install fastapi jinja2 uvicorn
    ```
    
* After creating fastAPI project create `app.py` file:
    
    ```python
    from fastapi import FastAPI, Request
    from fastapi.templating import Jinja2Templates
    from fastapi.responses import HTMLResponse
    
    app = FastAPI()
    templates = Jinja2Templates(directory="templates")
    
    @app.get("/",response_class=HTMLResponse)   
    def root(request: Request):
        return templates.TemplateResponse(name="index.html", context={"request": request})
    
    @app.get("/about",response_class=HTMLResponse)   
    def root(request: Request):
        return templates.TemplateResponse(name="about.html", context={"request": request})
    
    @app.get("/contact",response_class=HTMLResponse)
    def root(request: Request):
        return templates.TemplateResponse(name="contact.html", context={"request": request})
    
    if __name__ == "__app__":
        import uvicorn
        uvicorn.run(app, host="127.0.0.1", port=8000)
    ```
    
* Additionally, we'll optimize our setup by creating three HTML files within the 'template' folder: 'index.html' for the home page, 'about.html' for the about page, and 'contact.html' for the contact page. This structured approach will enhance our development process and make rendering pages with FastAPI even more seamless.
    

And finally, we have it corresponding routes for the HTML page.

### Conclusion:

In this blog, we learned about Server-Side Rendering (SSR) using FastAPI and Jinja2Templates. SSR involves the server generating HTML content and sending it to the client's browser. We implemented SSR in FastAPI by creating route handlers for the home, about, and contact pages and rendering HTML templates with Jinja2. This approach optimizes performance and SEO, making FastAPI an excellent choice for SSR in Python web development.

Thank you💕💕