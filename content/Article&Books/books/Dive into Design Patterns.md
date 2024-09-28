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

