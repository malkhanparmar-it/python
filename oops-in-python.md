# 🐍 Object-Oriented Programming (OOP) in Python

## 📖 Introduction

Object-Oriented Programming (OOP) is a programming paradigm that organizes code into **objects**. An object is an **instance of a class** that contains both **data (attributes)** and **behavior (methods)**.

### Why Use OOP?

OOP helps developers write code that is:

- ✅ Reusable
- ✅ Modular
- ✅ Easy to maintain
- ✅ Scalable
- ✅ Secure

Python is a fully object-oriented programming language that supports all the major OOP principles.

---

# 🚗 Real-World Analogy

Consider a **Car**.

### Attributes (Properties)

- Brand
- Model
- Color
- Speed

### Methods (Behaviors)

- Start()
- Stop()
- Accelerate()
- Brake()

### Similarly, in Python

| OOP Concept | Real World |
|-------------|------------|
| Class | Blueprint of a Car |
| Object | Actual Car |

---

# 📦 What is a Class?

A **class** is a blueprint used to create objects.

## Syntax

```python
class ClassName:
    pass
```

## Example

```python
class Student:
    pass
```

The above code creates a class named **Student**.

---

# 🎯 What is an Object?

An **object** is an instance of a class.

## Example

```python
class Student:
    pass

student1 = Student()
student2 = Student()

print(student1)
print(student2)
```

### Output

```text
<__main__.Student object at 0x...>
<__main__.Student object at 0x...>
```

Each object occupies a different memory location.

---

# 🏗 Constructor (`__init__`)

A constructor initializes object data automatically when an object is created.

## Syntax

```python
class Student:

    def __init__(self):
        print("Constructor Called")
```

## Example

```python
class Student:

    def __init__(self):
        print("Student Object Created")

student = Student()
```

### Output

```text
Student Object Created
```

---

# 👤 The `self` Keyword

`self` refers to the current object.

Python automatically passes it when methods are called on an instance.

## Example

```python
class Student:

    def __init__(self, name):
        self.name = name

student = Student("John")

print(student.name)
```

### Output

```text
John
```

---

# 📌 Instance Variables

Instance variables belong to an individual object.

## Example

```python
class Student:

    def __init__(self, name, age):
        self.name = name
        self.age = age

student = Student("Alice", 22)

print(student.name)
print(student.age)
```

### Output

```text
Alice
22
```

---

# ⚙ Instance Methods

Methods that operate on object data.

```python
class Student:

    def __init__(self, name):
        self.name = name

    def display(self):
        print("Student Name:", self.name)

student = Student("David")
student.display()
```

### Output

```text
Student Name: David
```

---

# 🌍 Class Variables

Shared by all objects.

```python
class Student:

    school = "ABC School"

    def __init__(self, name):
        self.name = name

student1 = Student("John")
student2 = Student("Emma")

print(student1.school)
print(student2.school)
```

### Output

```text
ABC School
ABC School
```

---

# 🏫 Class Methods

Operate on class-level data.

```python
class Student:

    school = "ABC School"

    @classmethod
    def show_school(cls):
        print(cls.school)

Student.show_school()
```

### Output

```text
ABC School
```

---

# 🔧 Static Methods

Utility methods that don't require instance (`self`) or class (`cls`) data.

```python
class Calculator:

    @staticmethod
    def add(a, b):
        return a + b

print(Calculator.add(10, 20))
```

### Output

```text
30
```

---

# 🏛 Four Pillars of OOP

1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

---

# 🔒 1. Encapsulation

Encapsulation combines data and methods within a class while controlling access to the data.

```python
class BankAccount:

    def __init__(self):
        self.__balance = 1000

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance

account = BankAccount()

account.deposit(500)

print(account.get_balance())
```

### Output

```text
1500
```

> **Note:** `__balance` uses name mangling to discourage direct external access.

---

# 👨‍👩‍👦 2. Inheritance

Inheritance allows one class to reuse another class's properties and methods.

```python
class Animal:

    def sound(self):
        print("Animal Sound")

class Dog(Animal):

    def bark(self):
        print("Dog Barks")

dog = Dog()

dog.sound()
dog.bark()
```

### Output

```text
Animal Sound
Dog Barks
```

---

# 📚 Types of Inheritance

## Single Inheritance

```python
class A:
    pass

class B(A):
    pass
```

## Multiple Inheritance

```python
class A:
    pass

class B:
    pass

class C(A, B):
    pass
```

## Multilevel Inheritance

```python
class A:
    pass

class B(A):
    pass

class C(B):
    pass
```

## Hierarchical Inheritance

```python
class Animal:
    pass

class Dog(Animal):
    pass

class Cat(Animal):
    pass
```

## Hybrid Inheritance

A combination of two or more inheritance types using multiple inheritance.

---

# 🔄 `super()`

The `super()` function lets a child class access the parent class methods.

```python
class Animal:

    def __init__(self):
        print("Animal Constructor")

class Dog(Animal):

    def __init__(self):
        super().__init__()
        print("Dog Constructor")

Dog()
```

### Output

```text
Animal Constructor
Dog Constructor
```

---

# 🎭 3. Polymorphism

Polymorphism means **one interface, many implementations**.

```python
class Dog:

    def sound(self):
        print("Bark")

class Cat:

    def sound(self):
        print("Meow")

animals = [Dog(), Cat()]

for animal in animals:
    animal.sound()
```

### Output

```text
Bark
Meow
```

---

# 🔁 Method Overriding

A child class provides its own implementation of a parent class method.

```python
class Animal:

    def sound(self):
        print("Animal Sound")

class Dog(Animal):

    def sound(self):
        print("Dog Bark")

dog = Dog()
dog.sound()
```

### Output

```text
Dog Bark
```

---

# ➕ Method Overloading

Python does not support traditional method overloading. Use default arguments or `*args`.

```python
class Calculator:

    def add(self, a, b=0, c=0):
        return a + b + c

calc = Calculator()

print(calc.add(10))
print(calc.add(10, 20))
print(calc.add(10, 20, 30))
```

### Output

```text
10
30
60
```

---

# 🎯 4. Abstraction

Abstraction hides implementation details while exposing only essential functionality.

```python
from abc import ABC, abstractmethod

class Shape(ABC):

    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):

    def __init__(self, length, width):
        self.length = length
        self.width = width

    def area(self):
        return self.length * self.width

rectangle = Rectangle(10, 5)

print(rectangle.area())
```

### Output

```text
50
```

---

# 🧩 Composition

Composition models a **has-a** relationship.

```python
class Engine:

    def start(self):
        print("Engine Started")

class Car:

    def __init__(self):
        self.engine = Engine()

    def drive(self):
        self.engine.start()
        print("Car is Moving")

car = Car()
car.drive()
```

### Output

```text
Engine Started
Car is Moving
```

---

# ✨ Special (Magic) Methods

Python provides special methods to customize object behavior.

```python
class Book:

    def __init__(self, title):
        self.title = title

    def __str__(self):
        return self.title

book = Book("Python Basics")

print(book)
```

### Output

```text
Python Basics
```

### Common Magic Methods

| Method | Description |
|---------|-------------|
| `__init__()` | Initialize objects |
| `__str__()` | User-friendly string representation |
| `__repr__()` | Developer-friendly representation |
| `__len__()` | Define behavior for `len()` |
| `__eq__()` | Equality comparison |

---

# ✅ Advantages of OOP

- Code Reusability
- Better Organization
- Easier Maintenance
- Improved Security through Encapsulation
- Extensible Design
- Scalable Applications
- Better Collaboration in Team Development

---

# 💡 Best Practices

- Follow the Single Responsibility Principle (SRP).
- Use meaningful class and method names.
- Keep methods focused on a single responsibility.
- Prefer composition over inheritance when appropriate.
- Keep internal data private unless it needs to be exposed.
- Write clear docstrings and comments.
- Avoid deeply nested inheritance hierarchies.

---

# 🌍 Real-World Applications of OOP

- Banking Systems
- E-Commerce Platforms
- Hospital Management Systems
- Library Management Systems
- School Management Systems
- Game Development
- Desktop Applications
- Web Applications
- Inventory Management Systems
- Enterprise Software

---

# 📋 Summary

| Concept | Description |
|---------|-------------|
| Class | Blueprint for creating objects |
| Object | Instance of a class |
| Constructor | Initializes object data |
| `self` | Refers to the current instance |
| Instance Variable | Data unique to each object |
| Class Variable | Data shared across all instances |
| Instance Method | Operates on instance data |
| Class Method | Operates on class-level data |
| Static Method | Utility method independent of instance/class state |
| Encapsulation | Bundles data and methods together while controlling access |
| Inheritance | Reuses and extends behavior from existing classes |
| Polymorphism | One interface, multiple implementations |
| Abstraction | Hides implementation details and exposes essential behavior |
| Composition | Builds classes by combining other objects |
| Magic Methods | Customize built-in object behavior |

---

# 🎯 Conclusion

Object-Oriented Programming is one of the most important concepts in Python for building maintainable, reusable, and scalable applications. By mastering classes, objects, inheritance, encapsulation, polymorphism, abstraction, and composition, you can develop software that is easier to understand, extend, and maintain. Practice these concepts by building real-world projects such as banking systems, inventory management applications, library management systems, and web applications to strengthen your OOP skills.
