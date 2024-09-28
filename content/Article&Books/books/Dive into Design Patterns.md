#algorithm 
#programinglang 
#software-engineering 


# Chapter 1 OOP Object Oriented Programming

Object-oriented programming is a paradigm based on the concept of wrapping pieces of data, and behavior related to that  data, into special bundles called objects, which are constructed from a set of “blueprints”, defined by a programmer, called  classes. 

[[OOP]]

- OOP Pillars [[OOP#Key Concepts of OOP#]]

Let's demonstrate **Dependency** and **Composition** using Python code examples. This will illustrate how these concepts are implemented and how they differ from each other.

### Dependency Example
In the context of OOP, **dependency** means that one class depends on another class to function properly. This is often referred to as a *dependency injection*, where an object of one class is passed to another class. The dependent class uses this object to perform its operations.

#### Dependency Example Code

```python
# Define the class Engine with a start() method
class Engine:
    def start(self):
        return "Engine started"

# Define the Car class, which depends on the Engine class
class Car:
    def __init__(self, engine):
        self.engine = engine  # Dependency: Car requires an Engine object
    
    def start_engine(self):
        return self.engine.start()  # Using the Engine object to start the car's engine

# Instantiate an Engine object
engine = Engine()

# Inject the Engine object into the Car object
car = Car(engine)

# Use the Car object to start the engine
print(car.start_engine())  # Output: Engine started
```

**Explanation:**
- `Car` is dependent on the `Engine` class. It does not inherit from `Engine` but relies on an instance of `Engine` to perform its `start_engine()` method.
- This dependency is passed into the `Car` class via the constructor (`__init__` method).

### Composition Example
**Composition** is when a class is composed of one or more objects from other classes. This establishes a ***has-a* relationship**, where one class contains instances of other classes as its members.

#### Composition Example Code

```python
# Define the Engine class
class Engine:
    def start(self):
        return "Engine started"

# Define the Tire class
class Tire:
    def inflate(self):
        return "Tire inflated"

# Define the Car class using composition
class Car:
    def __init__(self):
        self.engine = Engine()  # Car has an Engine object
        self.tire = Tire()      # Car has a Tire object
    
    def drive(self):
        # Using both the Engine and Tire objects within the Car class
        return f"{self.engine.start()} and {self.tire.inflate()} - Car is driving!"

# Create an instance of Car
car = Car()

# Use the Car object to perform actions
print(car.drive())  # Output: Engine started and Tire inflated - Car is driving!
```

**Explanation:**
- The `Car` class is composed of `Engine` and `Tire` classes. It creates and maintains its own instances of these classes.
- The `Car` class interacts with its internal components (`Engine` and `Tire`) to perform its `drive()` method.
- `Car` has a stronger relationship with `Engine` and `Tire` compared to dependency. The lifecycle of `Engine` and `Tire` is controlled by `Car` itself.

### Key Differences in the Code
1. **Dependency Injection**:
   - `Car` receives an `Engine` object from outside (injected into the constructor). `Car` depends on `Engine` but does not control its creation or lifecycle.
   - Example: `car = Car(engine)` — `Car` depends on an external `engine` object.

2. **Composition**:
   - `Car` internally creates and controls its own `Engine` and `Tire` objects.
   - The `Car` class has a direct "has-a" relationship with its components (`Engine` and `Tire`).

### Conclusion
- **Dependency** involves passing an existing object to a class, making it depend on that object without being responsible for its creation or lifecycle.
- **Composition** involves a class creating and owning other objects, leading to a stronger relationship and a "whole-part" hierarchy.


### Advantages of Dependency Injection and Composition in OOP

Both **Dependency Injection** and **Composition** offer distinct advantages in Object-Oriented Programming (OOP), particularly when it comes to flexibility, maintainability, and code reusability. Let’s outline the specific benefits of each.

#### Advantages of Dependency Injection
1. **Loose Coupling**:
   - Dependency Injection (DI) reduces the coupling between classes. Instead of creating dependencies directly, dependencies are passed from outside, making the code more modular and flexible.
   
2. **Improved Testability**:
   - Since dependencies are injected from outside, it becomes easier to swap real objects with mock or stub objects during testing. This allows for isolated unit testing without needing to instantiate real dependencies.
   
3. **Enhanced Flexibility and Reusability**:
   - With DI, the behavior of classes can be changed without modifying the class itself. This is useful when you want to switch implementations or configurations without touching the main class code.

4. **Decoupled Code Maintenance**:
   - Changes in dependencies have minimal impact on dependent classes, reducing the amount of code that needs to be changed or refactored. You can update a dependency without changing the class that uses it.

5. **Promotes Interface-Based Design**:
   - DI encourages the use of interfaces or abstract classes for dependency declarations, promoting a design that separates implementation from abstraction.

6. **Adherence to SOLID Principles**:
   - DI aligns with the Dependency Inversion Principle (DIP), one of the SOLID principles, which states that high-level modules should not depend on low-level modules, but both should depend on abstractions.

#### Advantages of Composition
1. **Reusability**:
   - Composition enables code reuse by building complex objects from simpler ones. The same components can be reused across different classes, reducing code duplication and enhancing maintainability.

2. **Flexibility in Object Behavior**:
   - Composition allows for easy modification of an object’s behavior by changing its internal components. It supports adding, removing, or replacing parts at runtime without affecting the overall structure.

3. **Improved Encapsulation**:
   - Composition helps encapsulate behavior within different classes. Each class is responsible for a specific part of the functionality, making it easier to understand, maintain, and debug.

4. **Simpler Class Hierarchies**:
   - With composition, there is no need for deep inheritance hierarchies. This leads to simpler and more intuitive class structures, avoiding the pitfalls of rigid inheritance models.

5. **Dynamic Behavior Changes**:
   - Unlike inheritance, where behavior is fixed at compile-time, composition allows behavior to change dynamically at runtime. This makes it possible to alter an object’s capabilities by reassigning its components.

6. **Promotes Modular Design**:
   - Composition breaks down a complex system into smaller, manageable parts. Each part can be developed, tested, and maintained independently, promoting a modular design approach.

7. **Avoids the Fragile Base Class Problem**:
   - Inheritance can introduce issues when changes in the base class ripple through the subclass hierarchy, potentially breaking the subclasses. Composition avoids this problem since classes only interact through well-defined interfaces.

8. **Better Adherence to the Open/Closed Principle**:
   - Composition allows you to extend an object’s behavior without modifying its existing code. You can add new components or replace existing ones without changing the class itself.

### Example Scenario: Choosing Between Dependency Injection and Composition
Imagine you are designing a `Car` class that can have different types of engines (e.g., `PetrolEngine`, `DieselEngine`, or `ElectricEngine`). Here’s when you might prefer each approach:

- **Dependency Injection**: You can inject the specific engine type into the `Car` class, making it easy to change or configure the engine from outside. This is useful if the `Car` class should be agnostic of how the engine is implemented or created.
  
    ```python
    class Car:
        def __init__(self, engine):
            self.engine = engine  # Engine is injected from outside
            
        def start(self):
            return self.engine.start()
    ```

- **Composition**: If the `Car` class needs to control its internal components (like starting multiple components simultaneously or configuring them together), using composition makes more sense. This allows the `Car` class to directly manage its own internal components.

    ```python
    class Car:
        def __init__(self):
            self.engine = Engine()  # Car has an Engine object
            self.tires = Tires()    # Car has a Tires object
            
        def start(self):
            return self.engine.start() + " and tires are ready!"
    ```

### When to Use Each
- Use **Dependency Injection** when:
  - You want to reduce the coupling between classes.
  - You need flexibility in switching or configuring dependencies.
  - You want to promote testability and support different test cases.

- Use **Composition** when:
  - You want to build a class by aggregating multiple components.
  - You need to manage the lifecycle of components within a class.
  - You want dynamic behavior changes or a simpler class hierarchy.

### Conclusion
Both Dependency Injection and Composition are powerful techniques in OOP that help achieve code modularity, flexibility, and maintainability. They solve different problems and can be used together or independently, depending on the design requirements.

# Design patterns

Design patterns are typical solutions to commonly occurring  problems in software design. They are like pre-made blueprints that you can customize to solve a recurring design problem in your code. 


## Difference between Algorithm and Design Pattern

An analogy to an algorithm is a cooking recipe: both have clear  steps to achieve a goal. On the other hand, a pattern is more  like a blueprint: you can see what the result and its features  are, but the exact order of implementation is up to you. 



### Categorization of Design Patterns by Intent

All design patterns can be categorized based on their **intent** or **purpose**. The three main groups of design patterns are:

1. **Creational Patterns**:
   - **Purpose**: Provide object creation mechanisms that increase flexibility and reuse of existing code.
   - **Examples**: Singleton, Factory Method, Abstract Factory, Builder, Prototype.

2. **Structural Patterns**:
   - **Purpose**: Explain how to assemble objects and classes into larger structures while keeping the structures flexible and efficient.
   - **Examples**: Adapter, Bridge, Composite, Decorator, Facade, Flyweight, Proxy.

3. **Behavioral Patterns**:
   - **Purpose**: Take care of effective communication and the assignment of responsibilities between objects.
   - **Examples**: Chain of Responsibility, Command, Interpreter, Iterator, Mediator, Memento, Observer, State, Strategy, Template Method, Visitor.



Design patterns are a toolkit of tried and tested solutions  to common problems in software design. Even if you never  encounter these problems, knowing patterns is still useful  because it teaches you how to solve all sorts of problems using  principles of object-oriented design.

# Software Design Principles

## Code Reuse

## Extensibility



### Software Design Principles

Software design principles are guidelines and best practices that developers follow to create robust, maintainable, and scalable software systems. These principles help in managing complexity, reducing dependencies, and promoting code reuse. They serve as a foundation for writing clean, understandable, and efficient code.

Here are some of the most widely adopted software design principles:

### 1. Single Responsibility Principle (SRP)
- **Definition**: A class should have only one responsibility and should have only one reason to change. Each class should focus on a single functionality or feature, which makes the code more modular and easier to maintain.
  
- **Example**: Consider a class `Document` that handles both file reading and content formatting. This violates the SRP because it has multiple responsibilities.
  
  ```python
  # Violation of SRP
  class Document:
      def read_file(self, filename):
          # Read content from a file
          pass
      def format_content(self):
          # Format the content of the document
          pass
  ```
  
  Instead, refactor it into separate classes:
  
  ```python
  # Following SRP
  class FileReader:
      def read_file(self, filename):
          # Read content from a file
          pass

  class ContentFormatter:
      def format_content(self):
          # Format the content of the document
          pass
  ```
  
  Each class now has a single responsibility: `FileReader` reads files, and `ContentFormatter` handles formatting.

### 2. Open/Closed Principle (OCP)
- **Definition**: Software entities (such as classes, modules, functions) should be open for extension but closed for modification. This means you should be able to extend a class's behavior without modifying its existing code.
  
- **Example**: Suppose you have a `Shape` class that calculates the area of various shapes. Adding new shapes would require modifying the existing code, which violates OCP.
  
  ```python
  # Violation of OCP
  class Shape:
      def area(self, shape_type, dimension):
          if shape_type == "circle":
              return 3.14 * dimension * dimension
          elif shape_type == "square":
              return dimension * dimension
  ```
  
  Instead, use polymorphism to extend the `Shape` class:
  
  ```python
  # Following OCP
  class Shape:
      def area(self):
          pass

  class Circle(Shape):
      def __init__(self, radius):
          self.radius = radius
      def area(self):
          return 3.14 * self.radius * self.radius

  class Square(Shape):
      def __init__(self, side):
          self.side = side
      def area(self):
          return self.side * self.side
  ```
  
  Now, adding new shapes like `Rectangle` or `Triangle` can be done by extending the `Shape` class without modifying the existing code.

### 3. Liskov Substitution Principle (LSP)
- **Definition**: Subtypes must be substitutable for their base types without affecting the correctness of the program. This principle ensures that a derived class can replace its base class without changing the desired behavior.
  
- **Example**: Consider a `Bird` base class with a method `fly`. A subclass `Ostrich` that cannot fly would violate LSP.
  
  ```python
  # Violation of LSP
  class Bird:
      def fly(self):
          pass

  class Ostrich(Bird):
      def fly(self):
          raise Exception("Ostriches can't fly!")
  ```
  
  Refactor using a more appropriate hierarchy:
  
  ```python
  # Following LSP
  class Bird:
      pass

  class FlyingBird(Bird):
      def fly(self):
          pass

  class Sparrow(FlyingBird):
      def fly(self):
          print("Sparrow is flying!")

  class Ostrich(Bird):
      # Ostrich class does not implement fly(), preserving LSP
      pass
  ```

### 4. Interface Segregation Principle (ISP)
- **Definition**: Clients should not be forced to implement interfaces they do not use. This principle suggests splitting large interfaces into smaller, more specific ones so that clients only need to know about the methods that are relevant to them.
  
- **Example**: Suppose you have an interface `IWorker` with methods `work()` and `eat()`. A `Robot` class implementing `IWorker` would have to implement `eat()`, which is not applicable.
  
  ```python
  # Violation of ISP
  class IWorker:
      def work(self):
          pass
      def eat(self):
          pass

  class Robot(IWorker):
      def work(self):
          print("Robot working")
      def eat(self):
          raise Exception("Robots don't eat!")
  ```
  
  Split the interface to avoid irrelevant implementations:
  
  ```python
  # Following ISP
  class IWorkable:
      def work(self):
          pass

  class IFeedable:
      def eat(self):
          pass

  class Robot(IWorkable):
      def work(self):
          print("Robot working")

  class Human(IWorkable, IFeedable):
      def work(self):
          print("Human working")
      def eat(self):
          print("Human eating")
  ```

### 5. Dependency Inversion Principle (DIP)
- **Definition**: High-level modules should not depend on low-level modules. Both should depend on abstractions. Also, abstractions should not depend on details. Details should depend on abstractions. This principle helps in decoupling modules and promoting flexible code.
  
- **Example**: Consider a `Light` class that is controlled by a `Switch` class. If the `Switch` class directly depends on the `Light` class, it violates DIP.
  
  ```python
  # Violation of DIP
  class Light:
      def turn_on(self):
          print("Light turned on")
      def turn_off(self):
          print("Light turned off")

  class Switch:
      def __init__(self, light):
          self.light = light

      def operate(self, state):
          if state == "ON":
              self.light.turn_on()
          elif state == "OFF":
              self.light.turn_off()
  ```
  
  Refactor to depend on an abstraction:
  
  ```python
  # Following DIP
  class Switchable:
      def turn_on(self):
          pass
      def turn_off(self):
          pass

  class Light(Switchable):
      def turn_on(self):
          print("Light turned on")
      def turn_off(self):
          print("Light turned off")

  class Switch:
      def __init__(self, device):
          self.device = device

      def operate(self, state):
          if state == "ON":
              self.device.turn_on()
          elif state == "OFF":
              self.device.turn_off()
  ```
  
  By introducing the `Switchable` interface, the `Switch` class now depends on an abstraction rather than a concrete implementation.

### Additional Software Design Principles

1. **DRY (Don't Repeat Yourself)**:
   - Avoid code duplication. Each piece of knowledge should have a single, unambiguous representation in the system.
   - **Example**: If the same piece of code appears in multiple places, refactor it into a separate function or class.

2. **KISS (Keep It Simple, Stupid)**:
   - Write simple and straightforward code. Avoid unnecessary complexity, as complex solutions are more prone to errors and harder to maintain.
   - **Example**: Instead of using complex nested loops and conditions, try to break down the logic into smaller, understandable functions.

3. **YAGNI (You Ain't Gonna Need It)**:
   - Avoid implementing features or functionality until they are actually needed.
   - **Example**: Don’t add extra methods or properties to a class based on future use cases unless there is a clear requirement for them.

4. **Composition Over Inheritance**:
   - Favor using composition (has-a relationships) over inheritance (is-a relationships) to achieve greater flexibility and code reuse.
   - **Example**: Instead of using class inheritance to extend functionality, use object composition to mix and match capabilities as needed.

### Conclusion
Software design principles are fundamental to writing clean, maintainable, and scalable software. By adhering to these principles, developers can create systems that are easier to understand, modify, and extend, ultimately leading to more robust and reliable software.


# Design Patterns

[[Creational Design Patterns]]
