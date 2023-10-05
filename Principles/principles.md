### Single Responsibility Principle (SRP)

SRP states that a class should have only one reason to change, i.e., it should have only one responsibility.
```
class Customer:
    def __init__(self, name):
        self.name = name

    def calculate_discount(self, order_total):
        # Calculate customer-specific discount logic
        pass

    def send_email(self, message):
        # Send an email to the customer
        pass
```
##### In this example, the Customer class violates SRP because it has two responsibilities: calculating discounts and sending emails. It's better to separate these into two classes.

### Open/Closed Principle (OCP)

OCP states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification.

```
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

class AreaCalculator:
    def calculate_area(self, shapes):
        total_area = 0
        for shape in shapes:
            if isinstance(shape, Rectangle):
                total_area += shape.width * shape.height
            # If we add more shapes, we need to modify this class
        return total_area
```
##### This code violates the OCP because if we want to add more shapes, we have to modify the AreaCalculator class. A better approach is to use polymorphism and abstract classes.

### Liskov Substitution Principle (LSP)

LSP states that objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.

```
class Bird:
    def fly(self):
        pass

class Ostrich(Bird):
    def fly(self):
        raise Exception("Ostrich can't fly")

def make_bird_fly(bird):
    bird.fly()

ostrich = Ostrich()
make_bird_fly(ostrich)  # This violates LSP
```
##### In this example, when an Ostrich object is passed to make_bird_fly, it raises an exception. This violates LSP because it's not substitutable for a general Bird.

### Interface Segregation Principle (ISP)

ISP states that clients should not be forced to depend on interfaces they do not use.

```
class Worker:
    def work(self):
        pass

    def eat(self):
        pass

class Robot(Worker):
    def work(self):
        pass

    def eat(self):
        pass
```
##### This violates ISP because not all clients of the Worker interface need both work and eat methods. It's better to split the interface into two smaller ones.

### Dependency Inversion Principle (DIP)

DIP states that high-level modules should not depend on low-level modules. Both should depend on abstractions.

```
class LightBulb:
    def turn_on(self):
        pass

    def turn_off(self):
        pass

class Switch:
    def __init__(self, bulb):
        self.bulb = bulb

    def operate(self):
        pass
```
##### This code violates DIP because the Switch class depends directly on a low-level class, LightBulb. To adhere to DIP, we can introduce an abstraction or interface for the device.
