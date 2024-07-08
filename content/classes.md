+++
title = "Classes"
+++

## Classes in Python

Python is an object-oriented programming language, which means that it provides features that support object-oriented programming (OOP). One of the key features of OOP is the ability to define classes, which are user-defined data structures that model real-world entities.

A class is a blueprint for creating objects (instances), providing initial values for state (attributes) and implementations of behavior (methods).

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hello, my name is {self.name} and I am {self.age} years old."
```

In the example above, we define a `Person` class with two attributes (`name` and `age`) and a method (`greet`). The `__init__` method is a special method called a constructor, which is used to initialize the object's state.

To create an instance of a class, we call the class as if it were a function, passing the necessary arguments to the constructor.

```python
person = Person("Alice", 30)
print(person.greet()) # Output: Hello, my name is Alice and I am 30 years old.
```
