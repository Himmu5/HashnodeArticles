---
title: "Day 36: E-commerce project day 4"
seoTitle: "E-commerce project day 4"
seoDescription: "The paragraph summarizes a blog post about an e-commerce project using FastAPI and MongoDB."
datePublished: Fri Mar 22 2024 18:21:49 GMT+0000 (Coordinated Universal Time)
cuid: clu2zn0q4000008kw6pyt1w1a
slug: day-36-e-commerce-project-day-4
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711129370333/2b778426-1686-4c71-9ac4-30d49858ed46.png
tags: python, 2articles1week

---

In the thirty-sixth blog post of my Python learning series, I dive into showcasing my progress and insights gained from working on an e-commerce project using FastAPI. This project revolves around storing user information and product data in MongoDB, which has been a rich learning experience for me. Throughout this journey, I have gained valuable knowledge and skills that I'm excited to share in this blog post.

Today Progress:

* Re-Auth API: Authentication APIs typically include an endpoint that receives a token from the client and validates the user's identity.
    
    ```python
    @user_router.get("/me",response_model=User)
    async def reAuth(authorization: str = Header(...)):
        try:
            if not authorization.startswith("Bearer "):
                raise HTTPException(status_code=401, detail="Invalid authorization header")
            token = authorization.replace("Bearer ", "")
    
            # Example: Replace with your token verification logic
            user = verify_token(token)
            if user is None:
                raise HTTPException(status_code=401, detail="Invalid token")
            # Example: Replace with your user authentication logic
            verified_user = await authenticate_user(user.get("email"), user.get("password"))
            if verified_user is None:
                raise HTTPException(status_code=401, detail="User not found")
    
            verified_user['id'] = str(verified_user['_id'])
            return verified_user
        except Exception as e:
            raise HTTPException(status_code=401, detail=str(e))
        
            
    async def authenticate_user(email: str, password: str):
        collection = get_user_collection()
        return await collection.find_one({"email": email, "password": password})   
    ```
    
* Middleware: Middleware is a set of common code that executes before an API is called. It allows us to perform various operations efficiently.
    
    ```python
    class AuthMiddleware(APIRoute):
        async def __call__(self, request: Request) -> Callable:
            if "Authorization" not in request.headers:
                raise HTTPException(status_code=401, detail="Unauthorized")
    
            token = request.headers["Authorization"].replace("Bearer ", "")
            try:
                payload = verify_token(token)
                request.state.user = payload
            except Exception as e:
                raise HTTPException(status_code=401, detail="Invalid token")
    
            return await super().__call__(request)
    ```
    

For the next day, we have some work on cart apis.

### Conclusion:

In my recent blog post, I shared insights from my e-commerce project using FastAPI and MongoDB. I discussed the Re-Auth API for user authentication, showcasing token validation and user verification logic. Additionally, I emphasized the significance of middleware in API development, particularly for executing common code efficiently before API calls.

Next, I plan to work on cart APIs to further enhance project functionality. Overall, the blog post offers a concise summary of my FastAPI learning journey and practical implementations in the e-commerce domain.

Thank you💕💕