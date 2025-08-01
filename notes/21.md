# **SOLID Principles in Python**

The **SOLID** principles are five guidelines that help us write **clean, maintainable, and scalable object-oriented code**. These are best practices followed by experienced developers to make code better.

> 🎯 **S** – Single Responsibility Principle
> 🎯 **O** – Open/Closed Principle
> 🎯 **L** – Liskov Substitution Principle
> 🎯 **I** – Interface Segregation Principle
> 🎯 **D** – Dependency Inversion Principle

We’ll go through each one with simple, beginner-friendly examples.

---

## ✅ **1. Single Responsibility Principle (SRP)**

**Definition**: A class should have only **one reason to change**. That means, a class should do only **one job**.

### ❌ Bad Example:

```python
class Student:
    def __init__(self, name):
        self.name = name

    def save_to_database(self):
        print("Saving to database...")

    def generate_report_card(self):
        print("Generating report card...")
```

> This class is handling both **data storage** and **report generation**. Too many responsibilities!

---

### ✅ Good Example:

```python
class Student:
    def __init__(self, name):
        self.name = name

class StudentDatabase:
    def save(self, student):
        print(f"Saving {student.name} to database...")

class ReportCard:
    def generate(self, student):
        print(f"Generating report card for {student.name}...")
```

> Now each class has **one job**: Student handles data, StudentDatabase saves, ReportCard generates.

---

## ✅ **2. Open/Closed Principle (OCP)**

**Definition**: Software entities (classes, functions, etc.) should be **open for extension but closed for modification**.

### ❌ Bad Example:

```python
class Discount:
    def get_discount(self, customer_type):
        if customer_type == "regular":
            return 10
        elif customer_type == "premium":
            return 20
```

> If we add a new customer type (e.g., VIP), we need to modify this class.

---

### ✅ Good Example:

```python
class Discount:
    def get_discount(self):
        return 0

class RegularCustomer(Discount):
    def get_discount(self):
        return 10

class PremiumCustomer(Discount):
    def get_discount(self):
        return 20
```

> You can now add more customer types by **extending**, not modifying the existing code.

---

## ✅ **3. Liskov Substitution Principle (LSP)**

**Definition**: Subclasses should be able to **replace their parent class** without breaking the program.

### ❌ Bad Example:

```python
class Bird:
    def fly(self):
        print("Flying...")

class Penguin(Bird):
    def fly(self):
        raise NotImplementedError("Penguins can't fly")
```

> Penguin violates LSP because it **can’t actually replace Bird**.

---

### ✅ Good Example:

```python
class Bird:
    def move(self):
        pass

class Sparrow(Bird):
    def move(self):
        print("Flying...")

class Penguin(Bird):
    def move(self):
        print("Swimming...")
```

> Now, both follow LSP because they behave correctly when used as a Bird.

---

## ✅ **4. Interface Segregation Principle (ISP)**

**Definition**: Don’t force a class to **implement methods it does not use**.

Python doesn’t have interfaces like Java/C#, but we can still follow this idea using base classes.

### ❌ Bad Example:

```python
class Worker:
    def work(self):
        pass

    def eat(self):
        pass

class Robot(Worker):
    def eat(self):
        raise NotImplementedError("Robots don't eat")
```

> Robot shouldn’t be forced to have `eat()`.

---

### ✅ Good Example:

```python
class Workable:
    def work(self):
        pass

class Eatable:
    def eat(self):
        pass

class Human(Workable, Eatable):
    def work(self):
        print("Human working")

    def eat(self):
        print("Human eating")

class Robot(Workable):
    def work(self):
        print("Robot working")
```

> Now, each class only implements the methods it **really needs**.

---

## ✅ **5. Dependency Inversion Principle (DIP)**

**Definition**: High-level modules should not depend on low-level modules. Both should depend on **abstractions**.

### ❌ Bad Example:

```python
class Keyboard:
    def input(self):
        return "User typing..."

class Computer:
    def __init__(self):
        self.keyboard = Keyboard()

    def get_input(self):
        return self.keyboard.input()
```

> `Computer` is **tightly coupled** to `Keyboard`.

---

### ✅ Good Example:

```python
class InputDevice:
    def input(self):
        pass

class Keyboard(InputDevice):
    def input(self):
        return "User typing..."

class Mouse(InputDevice):
    def input(self):
        return "Mouse clicked"

class Computer:
    def __init__(self, device: InputDevice):
        self.device = device

    def get_input(self):
        return self.device.input()
```

> Now `Computer` depends on an **abstraction**, and you can switch the input device easily!

---

## 🧠 Summary Table

| Principle | What It Means                   | Example Tip                          |
| --------- | ------------------------------- | ------------------------------------ |
| SRP       | One class = One job             | Don’t mix save logic & display logic |
| OCP       | Extend, don’t modify            | Add new types via subclass           |
| LSP       | Subclasses must replace parents | Don’t break functionality            |
| ISP       | No unnecessary methods          | Use multiple small classes           |
| DIP       | Depend on abstraction           | Use base classes/interfaces          |

---

## 🏠 Homework

1. **SRP Practice**: Create a `Book` class that only stores details. Create another class that prints book details.
2. **OCP Practice**: Build a billing system that calculates tax based on `ProductType`. Add `Food`, `Electronics`, etc., using subclasses.
3. **LSP Practice**: Write a class `Vehicle` and subclasses like `Bike`, `Boat`. Avoid breaking behavior.
4. **DIP Practice**: Make a `HomeAppliance` system where high-level class `Remote` works with abstract `Appliance`, and you can pass `TV`, `AC`, etc.

---
### **YouTube Reference**
Watch the following YouTube video from my channel:
- [Watch the tutorial on YouTube](https://www.youtube.com/watch?v=8rrdrJQdcvM)


 Make sure to subscribe to the channel for more Python tutorial and updates!

