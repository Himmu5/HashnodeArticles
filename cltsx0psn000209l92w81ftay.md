---
title: "Day 29: Web Development Frameworks (FastAPI)"
seoTitle: "Web Development Frameworks (FastAP)"
seoDescription: "In this blog, we delve into Python's web development frameworks as part of my ongoing Python learning journey."
datePublished: Fri Mar 15 2024 17:10:47 GMT+0000 (Coordinated Universal Time)
cuid: cltsx0psn000209l92w81ftay
slug: day-29-web-development-frameworks-fastapi
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710499530186/0e0a250e-8f89-4236-a189-0d44455d969c.png
tags: python, django, flask, fastapi

---

In this blog, we delve into Python's web development frameworks as part of my ongoing Python learning journey. This marks the twenty-ninth installment of this series. In today's programming landscape, frameworks play a pivotal role in driving development efforts. We aim to explore Python frameworks extensively, understanding their significance and the necessity they fulfill in the realm of web development.

### Web Development Framework

In today's fast-paced business environment, companies are continuously developing software at a rapid pace. However, this often leads to repetitive code writing by programmers. To mitigate this issue and streamline development processes, web frameworks prove to be invaluable tools. They allow developers to avoid redundant code and focus on building efficient and scalable software solutions.

### Web Framework in Python

* Django
    
* Flask
    
* FastAPI
    
* web2py
    

In this blog, we will try to CRUD operation in user's information with fastAPI.

### Creating a project with fastAPI

* first, we have to create a directory.
    

```json
 mkdir blog-fastAPI
```

* Setup virtual environment
    
    ```json
    py -m venv venv
    ```
    
* creating Python file
    
    ```json
    main.py
    ```
    
* Activating virtual environment
    
    ```json
    /venv/Scripts/activate
    ```
    
* Install FastAPI and uvicorn server
    
    ```python
    pip install fastapi uvicorn
    ```
    
* Importing modules and creating instance
    
    ```python
    from fastapi import FastAPI
    from pydantic import BaseModel
    
    app = FastAPI()
    ```
    
* Creating user model
    
    ```python
    class User(BaseModel):
        id: int
        name: str
        email: str
        age: int
    ```
    
* Performing CRUD operations
    
    ```python
    users_db = []
    @app.post("/users/", response_model=User)
    def create_user(user: User):
        users_db.append(user)
        return user
    
    @app.get("/users/{user_id}", response_model=User)
    def read_user(user_id: int):
        for user in users_db:
            if user.id == user_id:
                return user
        raise HTTPException(status_code=404, detail="User not found")
    
    @app.put("/users/{user_id}", response_model=User)
    def update_user(user_id: int, updated_user: User):
        for index, user in enumerate(users_db):
            if user.id == user_id:
                users_db[index] = updated_user
                return updated_user
        raise HTTPException(status_code=404, detail="User not found")
    
    @app.delete("/users/{user_id}", response_model=User)
    def delete_user(user_id: int):
        for index, user in enumerate(users_db):
            if user.id == user_id:
                deleted_user = users_db.pop(index)
                return deleted_user
        raise HTTPException(status_code=404, detail="User not found")
    ```
    
* start the app
    
    ```python
    uvicorn main:app --reload
    ```
    
    ### **Conclusion**:
    
    * Python's web development frameworks are essential tools for developers to streamline software development processes and avoid code duplication.
        
    * FastAPI stands out for its efficiency in handling CRUD operations and building RESTful APIs.
        
    * The provided code snippets illustrate how FastAPI simplifies the implementation of CRUD functionality, enhancing development speed and productivity.
        

Thankyou💕💕