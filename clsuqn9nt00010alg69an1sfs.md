---
title: "Day 5: Basic Data Structures (lists, tuples, dictionaries) in Python"
seoTitle: "Basic Data Structures (lists, tuples, dictionaries) in Python"
seoDescription: "Mastering Python's Foundation: Unveiling Lists, Tuples, and Dictionaries"
datePublished: Tue Feb 20 2024 19:08:12 GMT+0000 (Coordinated Universal Time)
cuid: clsuqn9nt00010alg69an1sfs
slug: day-5-basic-data-structures-lists-tuples-dictionaries-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708442386023/ce0e1c0c-a217-4319-a39d-a5015fa4787e.png
tags: python, 2articles1week, learning-journey, learn-in-public

---

In this introductory blog, I embark on the exploration of fundamental data structures in Python, marking the fifth day of my Python learning journey. Join me as I delve into the intricacies of essential data structures such as lists, tuples, and dictionaries. Through this exploration, I aim to share my learning and insights, laying the foundation for understanding and utilizing these versatile structures effectively.

### Data Structures

The core purpose of a data structure is to efficiently store and organize data, enabling seamless accessibility and processing. By employing suitable storage techniques, data retrieval and manipulation are streamlined, ultimately enhancing overall efficiency. The selection of the appropriate data structure is a crucial task in this regard.

* List: The list data structure is employed for sequential data storage, accommodating diverse types including strings, integers, booleans, and even functions. Elements within a list can be accessed by their respective index.
    
    ```python
    list = [ 5 , "10" , 5.20 ] 
    # this list contains int,string and float data type
    print("printing list : ",list)
    ```
    
    ```python
    list = [ 1 , 2 , 3 ]
    list.append(4)
    print("after appending new value : ",list)
    ```
    
    The `append()` method is utilized to add a new element to a list, placing it at the last index position within the list.
    
    ```python
    list = [ 1 , 2 , 3 , 4 ]
    # remove method will remove 3 from the list
    list.remove(3)
    print("after removing element : ",list)
    ```
    
* **Dictionary:** The dictionary data structure is employed to store data in key-value pairs. The values associated with keys can be of any data type, including lists, dictionaries, or any other type of data.
    
    ```python
    dict = { 'name' : "Himanshu chauhan" , roll_no : 10 }
    print("dict :",dict)
    ```
    
    we can also spread a dictionary to another dictionary.
    
    ```python
    dict1 = { "first" : 1 , "second" : 2 }
    dict2 = { "third" : 3 }
    # spreading dictionaries to a new dictionary
    new_dict = { **dict1 , **dict2 }
    ```
    
    To access this dictionary we can use key names to access their values.
    
    ```python
    dict1 = { "first" : 1 , "second" : 2 }
    # printing first value in dict1
    print("value of first : ",dict1["first"])
    ```
    
* **Tuple**: Tuples are immutable data structures, meaning their values cannot be changed after creation. Unlike lists, tuples cannot be updated or deleted once defined. They are similar to lists in structure but lack mutability.
    
    ```python
    tup = ( 4 , 5 , 5 )
    print("printing the tuple : ",tup)
    ```
    
* **Set**: A set in Python is an unordered collection of unique elements. Sets are mutable, allowing for the updating and deletion of elements. They are denoted by curly braces `{}`.
    
    ```python
    temp_set = {1, 2, 3, 4, 5}
    print(temp_set)  # Output: {1, 2, 3, 4, 5}
    ```
    
    To add a new element to this set:
    
    ```python
    temp_set.add(6)
    print("updated set : ",temp_set) # Output: {1, 2, 3, 4, 5, 6}
    ```
    
    remove an element from the set:
    
    ```python
    temp_set.remove(5)
    print("updated set : ",temp_set) # Output: {1, 2, 3, 4, 6}
    ```
    
    Conclusion:
    
    In this introductory blog, we embarked on an exploration of fundamental data structures in Python, marking the fifth day of our Python learning journey. We delved into the intricacies of essential data structures such as lists, tuples, dictionaries, and sets.
    
    Key takeaways:
    
    * Data structures serve the core purpose of efficiently storing and organizing data, enabling seamless accessibility and processing.
        
    * By employing suitable storage techniques, such as lists, tuples, dictionaries, and sets, we enhance overall efficiency in data retrieval and manipulation.
        
    * Lists provide sequential data storage, accommodating diverse types and allowing for dynamic updates using methods like `append()` and `remove()`.
        
    * Dictionaries store data in key-value pairs, facilitating easy access to values associated with keys. They offer versatility in handling different data types.
        
    * Tuples are immutable data structures, similar to lists but lacking mutability. Once defined, their values cannot be changed or deleted.
        
    * Sets are unordered collections of unique elements, providing flexibility in handling mutable data and supporting operations like adding and removing elements.
        
    
    By understanding and utilizing these versatile data structures effectively, we lay a strong foundation for Python programming and data manipulation tasks.
    

Thank you ❤️❤️❤️