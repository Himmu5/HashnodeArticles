---
title: "Day 37: Object Oriented Programming with Python(code examples)"
seoTitle: "Object Oriented Programming with Python(code examples)"
seoDescription: "Welcome to our journey into the world of object-oriented programming (OOP)! "
datePublished: Sat Mar 23 2024 18:14:10 GMT+0000 (Coordinated Universal Time)
cuid: clu4et1wy00000aiea5ygbm67
slug: day-37-object-oriented-programming-with-pythoncode-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711216212335/80972566-7472-4900-8646-d9005c1d9b24.png
tags: oop, python, 2articles1week

---

Welcome to our journey into the world of object-oriented programming (OOP)! We'll explore theory and practical examples to help you understand OOP easily.

In this blog post, we'll break down OOP concepts with clear code examples. We want to make learning OOP exciting and straightforward for you.

By combining theory and practice, we aim to give you a solid grasp of OOP principles. Whether you're new to programming or looking to refresh your knowledge, this blog will make OOP concepts come alive for you.

### Pillars of OOPS

* **Inheritance**: Inheritance is a mechanism where a class (child/subclass) can inherit properties and behaviors from another class (parent/superclass).
    
    ```python
    class Animal:
        def speak(self):
            pass  # Abstract method, to be overridden in subclasses
    
    class Dog(Animal):
        def speak(self):
            return "Woof!"
    
    class Cat(Animal):
        def speak(self):
            return "Meow!"
    
    dog = Dog()
    cat = Cat()
    
    print(dog.speak())  # Output: Woof!
    print(cat.speak())  # Output: Meow!
    ```
    
* **Encapsulation**: Encapsulation is the bundling of data (attributes) and methods that operate on that data within a class, restricting direct access from outside the class.
    
    ```python
    class BankAccount:
        def __init__(self):
            self.balance = 0
    
        def deposit(self, amount):
            self.balance += amount
    
        def withdraw(self, amount):
            if amount <= self.balance:
                self.balance -= amount
            else:
                print("Insufficient funds!")
    
        def get_balance(self):
            return self.balance
    
    account = BankAccount()
    account.deposit(1000)
    print(account.get_balance())  # Output: 1000
    account.withdraw(500)
    print(account.get_balance())  # Output: 500
    ```
    
* **Polymorphism**: Polymorphism allows objects to be treated as instances of their parent class, even when they are instances of subclasses.
    
    ```python
    class Shape:
        def area(self):
            pass  # Abstract method
    
    class Rectangle(Shape):
        def __init__(self, length, width):
            self.length = length
            self.width = width
    
        def area(self):
            return self.length * self.width
    
    class Circle(Shape):
        def __init__(self, radius):
            self.radius = radius
    
        def area(self):
            return 3.14 * self.radius ** 2
    
    shapes = [Rectangle(4, 5), Circle(3)]
    for shape in shapes:
        print(shape.area())
    ```
    
* **Access Control**: Python uses name mangling and access modifiers like public, protected, and private to control access to class members.
    
    ```python
    class MyClass:
        def __init__(self):
            self.public_var = "Public"  # Public attribute
            self._protected_var = "Protected"  # Protected attribute
            self.__private_var = "Private"  # Private attribute
    
        def get_private_var(self):
            return self.__private_var
    
    obj = MyClass()
    print(obj.public_var)  # Output: Public
    print(obj._protected_var)  # Output: Protected
    # print(obj.__private_var)  # Error: AttributeError
    print(obj.get_private_var())  # Output: Private
    ```
    

### Conclusion:

In conclusion, mastering Object-Oriented Programming (OOP) concepts in Python, including Inheritance, Encapsulation, Polymorphism, and Access Control, equips you with the tools to create organized, reusable, and flexible code. By understanding these pillars, you can design elegant solutions, model real-world entities effectively, and build robust applications. Keep exploring and applying OOP principles to elevate your Python programming skills and create impactful projects.

Thank you💕💕