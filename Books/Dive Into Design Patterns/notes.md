https://refactoring.guru/design-patterns/book

Progress: 147/396

# OOP

## Pillars of OOP

- abstraction
  - a representation of a real-world object or phenomenon, limited to a specific context, which represents all details relevant to that context.
- polymorphism
  - The ability of a program to detect the real class of an object and call its implementation even when its real type is unknown in the current context
- encapsulation
  - This is the heart of engineering. Taking something complex and making it simple. You don't need to know how the engine works - you only need to know how to interact with the limited interface.
- inheritance
  - The main benefit is code reuse and modeling object hierarchies

## Relationships

- dependency
  - changes to the definition of one class necessitate changes to the dependent class
- association
  - occurs when two classes interact with each other
- aggregation
  - one-to-many, many-to-many. One class may act as a container or collection. A component may exist without the container and can be linked to several containers at the same time.
- composition - a specific kind of aggregation in which components only exist as part of the container.
  ![[oop-relationships.png]]
  
# Design Patterns

There are three levels of code reuse

- classes, libraries, class "teams" (container/iterator)
- Patterns: a description of how a couple of classes can relate to and interact with each other
- frameworks: identify and distill the key abstractions for solving a problem

## Design Principles

- Encapsulate what varies
- Program to an interface, not an implementation
- favor composition over inheritance

## SOLID Principles

- Single Responsibility
	- Try to make every class responsible for a single part of the functionality provided by the software, and make that responsibility entirely encapsulated by the class.
- Open/Close Principle
	- Classes should be open for extension but closed for modification
- Liskov Substitution principle
	- When extending a class, remember that you should be able to pass objects of the subclass in place of objects of the parent class without breaking the client code
	- Subclass method arguments should be the same or more abstract. Subclass method return type should be the same or a more specific subtype.
	- A method in a subclass shouldn't throw types of exceptions which the base method isn't expected to throw.
	- A subclass shouldn't strengthen pre-conditions or weaken post-conditions.
	- A subclass shouldn't change the values of private fields of the superclass.
-  Interface segregation
	- Clients shouldn't be forced to depend on methods they do not use. This is a question of granularity: try to make your interfaces narrow enough that client classes don't have to implement behaviors they don't need.
-  Dependency Inversion
	- High-level classes shouldn't depend on low-level classes. Both should depend on abstractions. Abstractions shouldn't depend on details. Details should depend on abstractions


# Design Patterns

## Creational Patterns

### Factory Method

The factory method pattern suggests creating static methods for object construction. This allows for better customization and proper configuration of complex objects with many dependencies.
- The concrete objects created by the factory method should adhere to a common interface or base class.
- The creation logic is isolated in the factory, adhering to the single responsibility principle. This promotes a decoupling of the object construction and concrete implementation.
- Use the factory method when you don't know beforehand the exact types and dependencies of the object your code should work with.
- Open/Closed principle: you can introduce new types of products without breaking existing client code.

Example: Imagine software for a logistics company that needs to create various types of transportation vehicles like trucks, ships, or planes. The exact type of vehicle might depend on the cargo or destination. Using the factory pattern, the client code can simply use a factory method to get a vehicle without needing to know the details of how each type of vehicle is created or the nuances of their implementations.

Usage Steps:
1. Make all objects follow the same interface. This interface should declare methods that make sense in every product.
2. Add an empty factory method inside the creator class. The return type should match the common interface.
3. In the factory code, include the implementation details for creating each of the different variants based on a configuration parameter.
4. Create a set of creator subclasses for each type of object listed in the factory method. Override the factory method and extract the appropriate bits of construction code from the base method.
5. If there are too many object types, you can reuse the control parameter from the base class.

### Abstract Factory

This pattern provides a way to encapsulate a group of individual factories that have a common theme without specifying their concrete classes. This is useful for managing and organizing families of related or dependent objects.

Usage:
1. Map out a matrix of distinct object types and their variants
2. declare abstract object interfaces for all object types. Make concrete object classes which implement these interfaces.
3. Declare an abstract factory interface with a set of creation methods for all abstract products.
4. implement a set of concrete factory classes, one for each variant.
5. Create factory initialization code which will create one of the concrete factory classes.


### Builder

This pattern allows the construction of complex objects step by step. Typically this involves a builder class with various methods for customizing the construction of a new object. Each method call will configure different settings. Ultimately some sort of build method creates the final object based on all the configuration that was performed. Common build routines are sometimes controlled by a director class which defines the order of execution and works with a builder class to produce the final result.

Usage:
1. define the common construction steps for building all available object representations in the base builder interface.
2. create a concrete builder class for each of the object representations and implement their construction steps. Remember to include a method for retrieving the result.
3. Consider creating a director class with common build patterns.
4. Client should create instances of the builder (and optionally the director) and call the appropriate methods to configure the object as necessary. 

### Prototype
This pattern is describing the implementation of a clone method. This delegates the details of creating a copy of an object to the class itself and allows the client code to use a set of pre-built object, configured in various ways, as prototypes. Instead of instantiating a subclass that matches some configuration the client code can simply look for an appropriate prototype and clone it.

Usage:
1. Create a prototype interface and declare the clone method.
2. Implement this interface on a class to enable consumers to copy an object.
3. Optionally create a library of object prototypes which the client can clone.

### Singleton

The singleton pattern describes defining a class which can only ever have one instance. This is commonly used for classes which need to access some shared resource. 

Usage:
1. Add a private static field to the class for storing the singleton instance.
2. Declare a public static creation method for getting the singleton instance. This method should initialize the singleton instance on the first call and return it. All subsequent calls should return the previously created instance. 
3. Make the constructor of the class private. The static creation method of the class will be able to call it, but it will be impossible to instantiate otherwise.

## Structural Patterns

