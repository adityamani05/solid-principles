![Alt Mountblue Technologies](https://static.wixstatic.com/media/3aca1c_390a2917371943159fa1eb8274ff9c32~mv2_d_5331_3743_s_4_2.png/v1/crop/x_0,y_16,w_5331,h_3711/fill/w_96,h_67,al_c,q_85,usm_0.66_1.00_0.01/MountBlue%20Logo_2x.webp)


# S.O.L.I.D Principles
The SOLID principle was introduced by Robert C. Martin, in his 2000 paper [Design Principles and Design Patterns](https://web.archive.org/web/20150906155800/http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf). The SOLID principle helps in reducing tight coupling. Tight coupling means a group of classes are highly dependent on each other. It has 5 important design principles which we should follow while doing OOP (Object Oriented Programming). In this article, I will be covering these principles with examples.

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
It states that “do not implement an interface for a class which is irrelevant to them“. Suppose if you enter a restaurant and you are pure vegetarian. The waiter in that restaurant gave you the menu card which includes vegetarian items, non-vegetarian items, drinks, and sweets. In this case, as a customer, you should have a menu card which includes only vegetarian items, not everything which you don’t eat in your food. Here the menu should be different for different types of customers. The common or general menu card for everyone can be divided into multiple cards instead of just one. Using this principle helps in reducing the side effects and frequency of required changes.

```python
class IShape:
    def draw(self):
        raise NotImplementedError

class Circle(IShape):
    def draw(self):
        pass

class Square(IShape):
    def draw(self):
        pass

class Rectangle(IShape):
    def draw(self):
        pass
```
Another nice trick is that in our business logic, a single class can implement several interfaces if needed. So we can provide a single implementation for all the common methods between the interfaces. The segregated interfaces will also force us to think of our code more from the client’s point of view, which will in turn lead to loose coupling and easy testing. So, not only have we made our code better to our clients, we also made it easier for ourselves to understand, test and implement.

## Dependency Inversion Principle (DIP)
Dependency should be on abstractions not concretions. High-level modules should not depend upon low-level modules. Both low and high level classes should depend on the same abstractions. Abstractions should not depend on details. Details should depend upon abstractions. Two key points are here to keep in mind about this principle
* High-level modules/classes should not depend on low-level modules/classes. Both should depend upon abstractions.
* Abstractions should not depend upon details. Details should depend upon abstractions.
```python
class AuthenticationForUser():
  def __init__(self, connector:Connector):
		self.connection = connector.connect()
	
	def authenticate(self, credentials):
		pass
	def is_authenticated(self):
		pass	
	def last_login(self):
		pass

class AnonymousAuth(AuthenticationForUser):
	pass

class GithubAuth(AuthenticationForUser):
	def last_login(self):
		pass

class FacebookAuth(AuthenticationForUser):
	pass

class Permissions()
	def __init__(self, auth: AuthenticationForUser)
		self.auth = auth
		
	def has_permissions():
		pass
		
class IsLoggedInPermissions (Permissions):
	def last_login():
		return auth.last_log
```
There comes a point in software development where our app will be largely composed of modules. When this happens, we have to clear things up by using dependency injection. High-level components depending on low-level components to function. To create specific behavior you can use techniques like inheritance or interfaces.

## References
* https://www.geeksforgeeks.org/solid-principle-in-programming-understand-with-real-life-examples/
* https://itnext.io/solid-principles-explanation-and-examples-715b975dcad4
* https://web.archive.org/web/20150906155800/http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf
* https://medium.com/@dorela/s-o-l-i-d-principles-explained-in-python-with-examples-3332520b90ff
