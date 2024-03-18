---
title: "Day 32: E-commerce project Day 2"
seoTitle: "E-commerce project Day 2"
seoDescription: "In this blog, I delve into the second day of my e-commerce project, which revolves around my exploration of FastAPI for project development. "
datePublished: Mon Mar 18 2024 18:47:20 GMT+0000 (Coordinated Universal Time)
cuid: cltxasfr600040al54j4s8zcb
slug: day-32-e-commerce-project-day-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710781132327/d426945a-7ba4-40ff-a33a-1954fb6649c7.png
tags: python, mongodb, rest-api, fastapi, pydantic

---

In this blog, I delve into the second day of my e-commerce project, which revolves around my exploration of FastAPI for project development. As I navigate through the intricacies of FastAPI, I am gaining invaluable insights into its capabilities and functionalities. This journey has been instrumental in enhancing my understanding of modern web development frameworks and their application in real-world projects. Through hands-on experimentation and continuous learning, I am unlocking new possibilities and refining my skills to create robust and efficient solutions. Stay tuned as I share my experiences, challenges, and victories in this exciting endeavor!

Blog Progress:

1. Database: For this blog, I am using MongoDB as the main database.
    
2. Data Insertion: Currently I have added a hundred products to the database.
    
3. Db setup: setup created to interact with MongoDB by the motor library.
    
    ```powershell
    from motor.motor_asyncio import AsyncIOMotorClient
    from pydantic import BaseModel
    
    MONGO_URL = "mongodb://localhost:27017"
    client = AsyncIOMotorClient(MONGO_URL)
    database = client["ecommerceDb"]
    
    def get_product_collection():
        return database["products"];
    ```
    
4. Get products API: Also created an endpoint to get Product by id and get all products.
    
    ```powershell
    
    @app.get("/products/{id}", response_model=Union[List[Product], Product])
    async def read_root(id: Optional[str] = None) -> Any:
        try:
            if id is not None:
                # Assuming get_product_collection() returns a list of Product objects
                data = await get_product_collection().find_one({"id": id})
                if data:
                    return data  # Return single Product object
                else:
                    raise HTTPException(status_code=404, detail="Product not found")
            else:
                data = await get_product_collection().find().to_list(1000)
                return data  # Return list of Product objects
        except Exception as e:
            raise HTTPException(status_code=500, detail=str(e))
    ```
    
5. Project structure:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710784921564/ff92d22b-5c1a-40e6-9b62-fd541a52a045.png align="left")
    

### Conclusion

To summarize, my exploration of FastAPI for my e-commerce project's second day was highly productive. Using MongoDB as the primary database, I efficiently inserted a hundred products, creating a robust product catalog.

The motor library facilitated seamless interaction with MongoDB asynchronously. Additionally, I implemented a reliable API endpoint for retrieving product information by ID or fetching all products, enhancing user experience.

This hands-on experience with FastAPI expanded my technical skills and deepened my understanding of modern web development frameworks. I look forward to sharing further progress in future updates. Stay tuned for more insights into my e-commerce project powered by FastAPI and MongoDB.

Thankyou💕💕