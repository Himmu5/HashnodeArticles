---
title: "Day 31: Introduction of FastAPI"
seoTitle: "Introduction of FastAPI"
seoDescription: "This blog is part of my Python learning series, specifically focusing on FastAPI, a new web framework."
datePublished: Sun Mar 17 2024 17:13:51 GMT+0000 (Coordinated Universal Time)
cuid: cltvs0cxi00000al8hivlbckn
slug: day-31-introduction-of-fastapi
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710689053574/c914b83d-ceef-48ca-81e5-95a3cea2edef.png
tags: python, ecommerce, databases, fastapi

---

This blog is part of my Python learning series, specifically focusing on FastAPI, a new web framework. We will delve into building an e-commerce site project using FastAPI, providing hands-on experience in developing APIs with Python. Additionally, we'll incorporate technologies such as Docker, AWS, and Kubernetes, enhancing the project's scalability and deployment capabilities.

### FastAPI

FastAPI is a modern web development framework designed for building APIs with Python 3.8+ using standard Python type hints. It was first released on December 5, 2018. Notably, FastAPI boasts superior speed compared to older Python frameworks like Django.

**Features of FastAPI**

* **Fast**: FastAPI is more faster then the other framework like Nodejs, or Go.
    
* **Fast to code**: Increase the speed to develop features by about 200% to 300%.
    
* **Easy**: Designed to be easy to use and learn. Less time reading docs.
    
* **Short**: Minimize code duplication. Multiple features from each parameter declaration. Fewer bugs.
    

### Setup a fastAPI project

Installed dependencies in our fastAPI project.

```powershell
annotated-types==0.6.0
anyio==4.3.0
click==8.1.7
colorama==0.4.6
fastapi==0.110.0
greenlet==3.0.3
h11==0.14.0
httptools==0.6.1
idna==3.6
pydantic==2.6.4
pydantic_core==2.16.3
python-dotenv==1.0.1
PyYAML==6.0.1
sniffio==1.3.1
SQLAlchemy==2.0.28
starlette==0.36.3
typing_extensions==4.10.0
uvicorn==0.28.0
watchfiles==0.21.0
websockets==12.0
```

Folder Structure:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710694557501/939ff784-c4ea-45d3-8406-ed254f8a5501.png align="left")

Run this project:

```powershell
uvicorn main:app --reload
```

### Conclusion

In conclusion, this blog is part of a Python learning series focusing on FastAPI, a modern web framework for building APIs with Python 3.8+. The blog covers the advantages of FastAPI, such as its speed compared to older frameworks like Django, its ease of use, and its reduced code duplication leading to fewer bugs. The blog also provides a brief overview of the features of FastAPI and includes a setup guide for starting a FastAPI project, along with a folder structure example and a command to run the project using uvicorn. Overall, the blog aims to provide readers with a hands-on experience in developing APIs with FastAPI and leveraging technologies like Docker, AWS, and Kubernetes for scalability and deployment.

Thankyou💕💕