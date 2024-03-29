---
title: "Day 43: E-commerce project with Python"
seoTitle: "E-commerce project with Python"
seoDescription: "Today, on the forty-third day of our Python learning journey, we're diving back into our e-commerce project."
datePublished: Fri Mar 29 2024 17:24:28 GMT+0000 (Coordinated Universal Time)
cuid: clucxo8bs000g08imeb087nj7
slug: day-43-e-commerce-project-with-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711731705771/02dc91ee-283c-4d8f-93f5-2bbf3177bee8.png
tags: python, rest-api, fastapi

---

Today, on the forty-third day of our Python learning journey, we're diving back into our e-commerce project. I'm excited to share that I've completed the remaining APIs for the cart feature, bringing us one step closer to a fully functional system.

### Task done by today:

1. **Bulk API**: This API is to get products by IDs and these IDs we are providing in params.
    
    ```python
    @product_router.get("/products/bulk",response_model=List[Product])
    async def getBulkProducts(ids: str = Query(...)):
        try:
            ids_list = ids.split(',')
            products = []
            for id in ids_list:
                product = await get_product_collection().find_one({"id": int(id)})
                if product:
                    products.append(product)
            return products;
        except:
            print('An exception occurred')
    ```
    
2. Cart APi: we have two APIs for the cart first one is to create and update the cart and the second is to get a cart.
    
    To create cart:
    
    ```python
    @cart_router.post("/carts")
    async def saveCart(request: Request, new_cart: Cart_Type):
        if "Authorization" not in request.headers:
            raise HTTPException(status_code=401, detail="Unauthorized")
    
        token = request.headers["Authorization"]
        print("data: ", dict(new_cart.data))
        
        try:
            payload = dict(verify_token(token))
            user_email = payload.get("email")
            collection = get_cart_collection()
    
            # Check if cart already exists for the user
            existing_cart = await collection.find_one({"user_email": user_email})
            
            if existing_cart:
                # Update existing cart
                await collection.update_one({"user_email": user_email}, {"$set": {"cart": json.dumps(new_cart.data)}})
            else:
                # Create new cart
                cart_data = {
                    "user_email": user_email,
                    "cart": json.dumps(new_cart.data)
                }
                await collection.insert_one(cart_data)
            
            return {"message": "Cart updated successfully"}
        except Exception as e:
            raise HTTPException(status_code=401, detail="Invalid token")
    ```
    
    For getting the cart:
    
    ```python
    @cart_router.get("/carts", response_model=List[Cart_Response])
    async def getCart(request: Request):
        if "Authorization" not in request.headers:
            raise HTTPException(status_code=401, detail="Unauthorized")
        token = request.headers["Authorization"]
        try:
            payload = dict(verify_token(token))
            user_email = payload.get("email")
            collection = get_cart_collection()
            product_collection = get_product_collection()
            # Check if cart already exists for the user
            existing_cart = await collection.find_one({"user_email": user_email})
            products = []
            if existing_cart:
                # Update existing cart
                cart_str = existing_cart.get("cart")
                cart_obj = json.loads(cart_str)
                ids = list(cart_obj.keys())
                for id in ids:
                    product = await product_collection.find_one({"id": int(id)})
                    product_object = { "product": product, "quantity": cart_obj[id] }
                    products.append(product_object)
            return products
        except Exception as e:
            raise HTTPException(status_code=500, detail="something went wrong")   
    ```
    

In upcoming blogs, we'll optimize these APIs according to best practices, ensuring they are efficient and follow industry standards for robustness and scalability in our e-commerce project.

Project Link: [https://bitbucket.org/himmu5566/ecommerce-backend](https://bitbucket.org/himmu5566/ecommerce-backend/src/main/)

Thank you💕💕