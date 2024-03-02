---
title: "Day 16: Regular Expressions (Regex) in Python"
seoTitle: "Regular Expressions (Regex) in Python"
seoDescription: "Mastering Regex: Harnessing the Power of Regular Expressions in Python"
datePublished: Sat Mar 02 2024 17:40:10 GMT+0000 (Coordinated Universal Time)
cuid: cltadcfmi000209i90iyoa0cf
slug: day-16-regular-expressions-regex-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1709379746998/f3b9043d-3bd8-45b0-9ee6-0fbaecb695b6.png
tags: python, regex, learn-in-public

---

Welcome to the sixteenth day of my Python learning journey! Today, I delve into the fascinating world of Regular Expressions (regex). As I continue to deepen my understanding of Python, I'm excited to share my insights and experiences with you. In this blog post, I'll walk you through my understanding of Regular Expressions, exploring how they can be leveraged to manipulate and validate text data in Python. Join me on this journey as we unravel the mysteries of regex together!

### Regular Expressions

Regular expressions (regex or RE) define a pattern that identifies a set of strings matching it. The functions within this module enable you to determine if a specific string conforms to a given regex pattern. Conversely, they also allow you to ascertain if a provided regex pattern matches a particular string. This dual functionality provides flexibility in validating and manipulating text data according to predefined patterns.

Regex Example:

* **Pattern to match email**:
    
    ```python
    import re
    
    email_pattern = r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b'
    
    # Test the pattern
    emails = [
        "example@example.com",
        "user123@example.co.uk",
        "user.name@example-domain.com",
        "invalid_email.com",
        "user@example",
    ]
    
    for email in emails:
        if re.match(email_pattern, email):
            print(f"{email} is a valid email address.")
        else:
            print(f"{email} is not a valid email address.")
    ```
    
* **Pattern to match password**:
    
    ```python
    import re
    
    password_pattern = r'^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$'
    
    # Test the pattern
    passwords = [
        "Password123!",
        "weakpassword",
        "StrongPassword123",
        "12345678",
        "P@ssw0rd",
    ]
    
    for password in passwords:
        if re.match(password_pattern, password):
            print(f"{password} is a strong password.")
        else:
            print(f"{password} is not a strong password.")
    ```
    

### Conclusion:

Regular expressions (regex) are a powerful tool in Python for pattern matching and text manipulation. In this blog post, we explored the fundamentals of regular expressions and how they can be applied to validate and manipulate text data.

We started by understanding the concept of regular expressions, which define patterns to identify sets of strings. We learned that Python's `re` module provides functions to check if a string matches a given regex pattern or if a regex pattern matches a particular string. This dual functionality enables us to validate and manipulate text data according to predefined patterns, providing flexibility in various applications.

Thankyou💕💕