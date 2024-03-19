---
title: "Day 33: E-commerce project day 3"
seoTitle: "E-commerce project day 3"
seoDescription: "In the thirty-third blog post of my Python learning series, I dive into showcasing my progress."
datePublished: Tue Mar 19 2024 16:22:18 GMT+0000 (Coordinated Universal Time)
cuid: cltyl1rov000308igaglmfogq
slug: day-33-e-commerce-project-day-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710859415954/188acd4e-2b57-436d-bc62-b0137c8bdef3.png
tags: security, apis, python3, jwt, fastapi

---

In the thirty-third blog post of my Python learning series, I dive into showcasing my progress and insights gained from working on an e-commerce project using FastAPI. This project revolves around storing user information and product data in MongoDB, which has been a rich learning experience for me. Throughout this journey, I have gained valuable knowledge and skills that I'm excited to share in this blog post.

### Blog Progress:

1. Product API Updated: we have already created API to get a single product and to get all products. I have modified that Api today.
    
    ```powershell
    
    @product_router.get("/product/{id}", response_model=Product)
    async def get_product(id:str) -> Any:
        try:
            if id is not None:
                # Assuming get_product_collection() returns a list of Product objects
                data = await get_product_collection().find_one({"id": int(id)})
                if data:
                    return data  # Return single Product object
                else:
                    raise HTTPException(status_code=404, detail="Product not found")
            else:
                raise HTTPException(status_code=404, detail="Product Id not given")
        except Exception as e:
            raise HTTPException(status_code=500, detail=str(e))
        
    @product_router.get("/products", response_model=Dict[str, Any])
    async def get_products(
        sortBy: Optional[str] = Query(None, description="Sort field (e.g., 'title', 'price')"),
        sortType: Optional[str] = Query(None, description="Sort type ('asc' for ascending, 'desc' for descending)"),
        page: Optional[int] = Query(1, description="Page number (default: 1)"),
        limit: Optional[int] = Query(20, description="Number of products per page (default: 20, max: 100)"),
        search: Optional[str] = Query(None, description="Search products by title")
    ) -> Any:
        collection = get_product_collection()
        try:
            # Default filters
            filters = {}
            if search:
                filters["title"] = {"$regex": f".*{search}.*", "$options": "i"}
    
            # Sorting
            sort_criteria = []
            if sortBy:
                sort_criteria.append((sortBy, 1 if sortType != 'desc' else -1))  # 1 for ascending, -1 for descending
            else:
                sort_criteria.append(("id", 1))  # Default sorting by ID ascending
    
            # Count total matching documents
            total_products = await collection.count_documents(filters)
    
            # Calculate start and end index for pagination
            start_index = (page - 1) * limit
            end_index = start_index + limit
    
            # Retrieve products based on filters, sorting, and pagination
            products_cursor = collection.find(filters).sort(sort_criteria).skip(start_index).limit(limit)
            products_data = await products_cursor.to_list(None)
    
            # Convert MongoDB documents to Product instances
            products = [Product(**product_data) for product_data in products_data]
            meta = {
                "total": total_products,
                "per_page": limit,
                "current_page": page,
                "last_page": (total_products + limit - 1) // limit,
                "first_page": 1,
                "first_page_url": f"/products?page=1",
                "last_page_url": f"/products?page={(total_products + limit - 1) // limit}",
                "next_page_url": f"/products?page={page + 1}" if page < (total_products + limit - 1) // limit else None,
                "previous_page_url": f"/products?page={page - 1}" if page > 1 else None
            }
    
            return {"meta": meta, "data": products}
        except Exception as e:
            raise HTTPException(status_code=500, detail=str(e))
    ```
    
    We've developed two essential APIs for our e-commerce platform. The first API allows users to fetch a specific product based on its unique productId. The second API is more comprehensive, enabling users to retrieve all products with additional filtering options.
    
    In the second API, we've introduced pagination to enhance the browsing experience. This means users can navigate through product listings more efficiently, with results displayed in manageable chunks. Additionally, we've implemented a sortBy filter, empowering users to sort product listings based on title or price criteria. These enhancements contribute to a more user-friendly and organized product browsing experience on our platform.
    
2. **User's Authentication:** We've introduced two APIs to facilitate user registration and account creation securely. Leveraging JWT (JSON Web Tokens) authentication, we've bolstered the security of these APIs, ensuring that user data remains protected throughout the registration process.
    
    The registration API allows users to create a new account, providing essential details such as email, password, and full name. Upon successful registration, a JWT token is generated, granting authenticated access to authorized endpoints within our system.
    
    Meanwhile, the signup API serves as a gateway for users to authenticate themselves and gain access to our platform's features. By integrating JWT authentication, we've established a robust authentication mechanism that safeguards user credentials and enhances the overall security posture of our APIs.
    
    For the JWT setup, I have created `jwt_auth.py`.
    
    ```powershell
    from jose import jwt
    
    SECRET_KEY = "MY_SECRET_KEY"
    ALGORITHM = "HS256"
    
    def create_access_token(data: dict):
        to_encode = data.copy()
        encoded_jwt = jwt.encode(to_encode, SECRET_KEY, algorithm=ALGORITHM)
        return encoded_jwt
    
    def verify_token(token: str):
        return jwt.decode(token, SECRET_KEY, algorithms=[ALGORITHM])
    ```
    
    And User APIs is in `user_router.py` .
    
    ```powershell
    from fastapi import APIRouter,HTTPException,status
    from fastapi.responses import JSONResponse
    from .models import SIGNIN_REQUEST,SIGNUP_REQUEST,SIGNIN_RESPONSE
    from .jwt_auth import create_access_token
    from .db_config import get_user_collection
    import pymongo.errors
    user_router = APIRouter()
    
    @user_router.post("/login", response_model=SIGNIN_RESPONSE)
    async def get_user(cred: SIGNIN_REQUEST):
        print("cred: ",cred)
        if not cred.email:
            return JSONResponse(content={"error": "Email not found"}, status_code=400)
        elif not cred.password:
            return JSONResponse(content={"error": "Password not found"}, status_code=400)
        else:
            user = await authenticate_user(cred.email, cred.password)
            if not user:
                return JSONResponse(content={"error": "Invalid credentials"}, status_code=400)
            else:
                data = {"email": cred.email,"password": cred.password}
                token ="bearer "+create_access_token(data)
                user['id'] = str(user['_id'])
            return {"user": user, "token": token}
     
    
    @user_router.post("/signup", response_model=SIGNIN_RESPONSE, status_code=status.HTTP_201_CREATED)
    async def signup(cred: SIGNUP_REQUEST):
        if not cred.email or not cred.fullName or not cred.password:
            raise HTTPException(status_code=status.HTTP_400_BAD_REQUEST, detail="Invalid input data")
        else:
            user = await create_user(cred.email, cred.password, cred.fullName)
            data = {"email": cred.email,"password": cred.password}
            token = "bearer "+create_access_token(data)
            return { "user": user, "token": token}
        
    async def create_user(email: str, password: str, fullName: str):
        try:
            collection = get_user_collection()
            # Create the unique index on email if it doesn't exist yet
            collection.create_index("email", unique=True)
            created_user = await collection.insert_one({'email': email, 'password': password, 'fullName': fullName})
            return {
                'id': str(created_user.inserted_id),
                'email': email,
                'fullName': fullName
            }
        except pymongo.errors.DuplicateKeyError:
            raise HTTPException(status_code=status.HTTP_400_BAD_REQUEST, detail="Email already exists")
        except Exception as e:
            raise HTTPException(status_code=status.HTTP_500_INTERNAL_SERVER_ERROR, detail=str(e))
        
    async def authenticate_user(email: str, password: str):
        collection = get_user_collection()
        return await collection.find_one({"email": email, "password": password})
    ```
    
3. Models: Today I have learned something about Pydantic models. A Pydantic model is a data validation and parsing library for Python. It is primarily used for data serialization and deserialization, ensuring that data objects adhere to a defined structure or schema. Pydantic models are often used in web frameworks like FastAPI to validate incoming request data, handle data conversion, and enforce data integrity. I have created some models for users and product APIs.
    
    ```python
    from pydantic import BaseModel, EmailStr
    
    class Product(BaseModel):
        id: int
        title: str
        description: str
        price: float
        discount_percentage: float
        thumbnail: str
        category: str
        brand: str
        
    class SIGNIN_REQUEST(BaseModel):
        email: EmailStr
        password: str
        
    class SIGNUP_REQUEST(BaseModel):
        email: EmailStr
        password: str
        fullName: str
    
    class User(BaseModel):
        id: str
        email: EmailStr
        fullName: str
        
    class SIGNIN_RESPONSE(BaseModel):
        user: User
        token: str
    ```
    

### Conclusion

In this blog post, I shared my progress in developing an e-commerce project using FastAPI, MongoDB for data storage, JWT authentication for security, and Pydantic models for data validation. The key highlights include:

1. **Product API Updates:** Enhanced APIs to retrieve single and multiple products with pagination, sorting, and search filters for improved user experience.
    
2. **User Authentication:** Implemented secure user registration and login APIs using JWT tokens for authentication, ensuring data security.
    
3. **Pydantic Models:** Utilized Pydantic models for data validation and serialization, ensuring structured and reliable data handling.
    

Overall, this blog showcases practical implementations in FastAPI development, data management, and security measures, providing valuable insights into backend web development techniques.

Thank you💕💕