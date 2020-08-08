# S.O.L.I.D Principles
The SOLID principle was introduced by Robert C. Martin, in his paper [Design Principles and Design Patterns](https://web.archive.org/web/20150906155800/http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf). The SOLID principle helps in reducing tight coupling. Tight coupling means a group of classes are highly dependent on each other. It has 5 important design principles which we should follow while doing OOP (Object Oriented Programming). In this article, I will be covering these principles with examples.

### The Five principles of SOLID
1. Single Responsibility Principle (SRP)
2. Open/Closed Principle
3. Liskov’s Substitution Principle (LSP)
4. Interface Segregation Principle (ISP)
5. Dependency Inversion Principle (DIP)

## Single Responsibility Principle (SRP)
This principle says  “a class in any object-oriented programing language should have only one responsibility” which means every class should have a single responsibility or single job or single purpose. We should not define more functions in a single class, It is a bad programming practice, we should break that class into small modules or groups so that in future if we want to change anything then we won't face any issues. See this by example

```python
class User:
    def __init__(self, name: str):
            self.name = name
    
    def get_name(self):
        pass


class UserDB:
    def get_user(self, id) -> User:
        pass

    def save(self, user: User):
```

we can do this by using one class but we are following the Single Responsibility Principle so we have two classes here with single purpose. 

## Open/Closed Principle
This principle states that “ we can use classes, modules, functions in OOP but we cannot modify them” which means you should be able to extend a class behavior, without modifying it.  See this by example
```python
 class Discount:
    def __init__(self, customer, price):
      self.customer = customer
      self.price = price

    def get_discount(self):
      return self.price * 0.2

class VIPDiscount(Discount):
    def get_discount(self):
      return super().get_discount() * 2
```
We can use only one class Discount and we can add a method into that class and that will also work but here we are following the Open/Closed Principle so we are doing this and not modifying the main class but we are using that class.

## Liskov’s Substitution Principle (LSP)
This principle states that “Child classes must be substitutable for their base or parent classes“ which means if the child wants then they can replace their father and for this, they should have all the behavior of parents class. 

```python
class Bird:
    paas

class FlyingBirds(Bird):
    def fly():
        paas

class Duck(FlyingBirds):
    paas

class Ostrich(Bird):
    paas
```
We can see that the class Duck can replace the Bird because it has all the functionality of the Bird class.

## Interface Segregation Principle (ISP)
It states that “do not implement an interface for a class which is irrelevant to them“. we can understand this by example
