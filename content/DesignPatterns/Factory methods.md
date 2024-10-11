
The **Factory Method Pattern** is a creational design pattern that provides an interface for creating objects, but allows subclasses to alter the type of objects that will be created. Instead of calling a constructor directly to create an object, the factory method delegates the creation to subclasses or derived classes, allowing for more flexibility and decoupling in object creation.

### Key Concepts:

1. **Factory Method**: Defines an interface or abstract method for creating an object, but lets subclasses decide which class to instantiate. Thus, the method is deferred to subclasses.
2. **Product**: The object that is created. The factory method defines the type of product (typically an interface or an abstract class).
3. **Concrete Product**: The actual object that is created by the factory method, typically implementing the Product interface or extending the Product abstract class.
4. **Creator (Factory)**: Declares the factory method that returns a product object. It may also include default implementations.
5. **Concrete Creator (Concrete Factory)**: Overrides the factory method to create and return a specific type of product.

### Structure of the Factory Method Pattern:

- **Creator**: This class declares the factory method, which returns an object of type `Product`.
- **ConcreteCreator**: This subclass implements the factory method to return an instance of `ConcreteProduct`.
- **Product**: This is the interface or abstract class for objects created by the factory method.
- **ConcreteProduct**: This is a class that implements the `Product` interface.

### When to use the Factory Method Pattern:
- When the exact class of objects to be created is not known until runtime.
- When you want to decouple the code that creates objects from the code that uses objects.
- When a class wants its subclasses to specify the objects to be created.
- When you have a class with multiple potential subclasses, and you want to delegate object creation based on some criteria.

### Example Scenario:

Let's say you are building a logistics system, and you want to have different transportation modes like trucks and ships. The transportation mode might be chosen at runtime, depending on factors like the type of goods, location, or cost. You can use the Factory Method to handle the creation of the appropriate transportation mode.

### Example Code:

#### Step 1: Define the Product Interface

```python
from abc import ABC, abstractmethod

# Abstract Product
class Transport(ABC):
    @abstractmethod
    def deliver(self):
        pass
```

#### Step 2: Implement Concrete Products

```python
# Concrete Product 1
class Truck(Transport):
    def deliver(self):
        print("Delivering by land in a truck.")

# Concrete Product 2
class Ship(Transport):
    def deliver(self):
        print("Delivering by sea in a ship.")
```

#### Step 3: Define the Creator (Factory) with the Factory Method

```python
# Abstract Creator (Factory)
class Logistics(ABC):
    @abstractmethod
    def create_transport(self) -> Transport:
        pass

    def plan_delivery(self):
        transport = self.create_transport()
        transport.deliver()  # Delegate the creation and execution to the transport object
```

#### Step 4: Implement Concrete Creators (Concrete Factories)

```python
# Concrete Creator 1 (Factory)
class RoadLogistics(Logistics):
    def create_transport(self) -> Transport:
        return Truck()

# Concrete Creator 2 (Factory)
class SeaLogistics(Logistics):
    def create_transport(self) -> Transport:
        return Ship()
```

#### Step 5: Client Code

The client code interacts with the factory to get the right product (transportation mode). It is decoupled from the actual classes of the products being created.

```python
# Client code
def client_code(logistics: Logistics):
    logistics.plan_delivery()

# Example Usage
if __name__ == "__main__":
    # Choosing road logistics
    print("Road logistics:")
    road_logistics = RoadLogistics()
    client_code(road_logistics)
    
    print("\nSea logistics:")
    # Choosing sea logistics
    sea_logistics = SeaLogistics()
    client_code(sea_logistics)
```

### Output:

```
Road logistics:
Delivering by land in a truck.

Sea logistics:
Delivering by sea in a ship.
```

### Explanation:

- **Product Interface (`Transport`)**: Defines the general behavior (i.e., the `deliver` method).
- **Concrete Products (`Truck`, `Ship`)**: Implements the behavior for specific types of products (i.e., different delivery methods).
- **Creator (`Logistics`)**: Declares the factory method `create_transport()` that returns a `Transport` object.
- **Concrete Creators (`RoadLogistics`, `SeaLogistics`)**: Override the factory method to instantiate specific products (`Truck` or `Ship`).
- **Client Code**: Works with the factory (i.e., `Logistics`) to create the appropriate object and execute the corresponding method (`deliver`).

### When to Use Factory Method:

1. **When you don’t know beforehand which exact class of objects your system will need**: If the exact class of the object that will be created is determined at runtime (based on some conditions), the Factory Method is a good fit.
   - Example: If you’re building a notification system, and at runtime you decide whether to send an email, SMS, or push notification, the Factory Method would help create the appropriate notification sender without hardcoding any specific classes.

2. **When you want to decouple object creation from the client code**: If you want to centralize the creation of objects in a specific place (the factory) and let the client interact with abstract interfaces, this pattern works well.
   - Example: In a game engine, different character types (e.g., Warrior, Mage, Archer) might be created at different points in the game. The game logic would only interact with the abstract `Character` class, and the Factory Method would handle creating the right type of character.

3. **When you want to follow the Open/Closed Principle**: If you anticipate adding new product types or variants in the future, the Factory Method allows you to do so without modifying existing code.
   - Example: In the logistics example, if you later introduce `AirLogistics`, you can add a new `AirLogistics` class without changing the existing code that handles `RoadLogistics` or `SeaLogistics`.

### Difference from Abstract Factory:

- **Factory Method** creates a single product (one type of object), and subclasses decide which concrete class to instantiate.
- **Abstract Factory** creates a family of related objects, and subclasses determine which concrete classes to instantiate for all products in the family.

The Factory Method is useful when you need flexibility in object creation without exposing the concrete classes to the client code, while the Abstract Factory is useful when creating families of related objects.


