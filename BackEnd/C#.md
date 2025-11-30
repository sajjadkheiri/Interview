# C# 

## What is CLR

![CLR-Execution-Model](/Resources/CLR-components.png)
![CLR-Execution-Model](/Resources/CLR-Execution-Model.jpg)

## Class vs Record

- **$\textsf{\color{#008000}{Class}}$** 

    It is a reference type that represents a complex data structure /It contains fields, properties, methods, and events/a new object is created on the heap

- **$\textsf{\color{#008000}{Record}}$**

    A record is a value type that represents an $\textsf{\color{#fbbc05}{immutable}}$ data structure/ It contains fields, properties, and methods, but not events

## Tuple vs Struct:

- **$\textsf{\color{#008000}{Tuple}}$**

    It’s a reference type (class) that represents a collection of values / It’s an immutable, read-only data structure / It’s stored on the heap

- **$\textsf{\color{#008000}{Struct}}$**

    It’s a mutable value type data structure, meaning its fields can be modified after creation / It’s stored on the stack

## OOP

- **$\textsf{\color{#008000}{Encapsulation}}$**

    Bundling data and methods that operate on the data within a single unit (class).

    - A Car class has properties like color and speed and methods like drive(). Encapsulation keeps these related elements together.

- **$\textsf{\color{#008000}{Abstraction}}$**

    Hiding complex implementation details and exposing only the necessary functionality.

    - When you drive a car, you use the steering wheel and pedals without knowing the internal engine mechanics.

- **$\textsf{\color{#008000}{Inheritance}}$**

    Creating new classes from existing ones to promote code reuse. 

    - A SportsCar class can inherit from a Car class, gaining all Car properties and behaviors while adding specific features like turboBoost().

- **$\textsf{\color{#008000}{Polymorphism}}$**

    Allowing objects to be treated as instances of their parent class and letting methods perform differently based on the object.

    - A drive() method might behave differently for Car and Truck objects, depending on their specific requirements.

## Abstraction vs Interface: 

- **Implementation :**

    Abstract classes can have implementation, while interfaces cannot.

- **Inheritance :**

    Abstract classes can inherit from other classes, while interfaces cannot.

- **Abstraction** focuses is on hiding implementation details

- **Interface** is a set of methods that must be implemented


## Solid

- **$\textsf{\color{#008000}{Single responsibility}}$**
    
     A class should have only one reason to change, meaning it should have only one responsibility.

    - A User class handles user data, while an EmailService class manages email notifications, keeping responsibilities separate.

- **$\textsf{\color{#008000}{Open and close}}$**
    
     Software entities should be open for extension but closed for modification.

    - A PaymentProcessor class can be extended to support new payment types (e.g., CreditCardPayment, PaypalPayment) without changing the original class code.


- **$\textsf{\color{#008000}{Liskov sub situation}}$**
    
     Subclasses should be substitutable for their base class without altering the correctness of the program.

    - If Rectangle is a base class and Square is a subclass, Square should behave consistently as a Rectangle without breaking any logic.

- **$\textsf{\color{#008000}{Interface segregation}}$**
    
     No client should be forced to implement methods it doesn’t use. Interfaces should be specific to each client’s needs.

    - Instead of a large Worker interface with unrelated methods, create smaller, specific interfaces like IWorkable (for work()) and IEatable (for eat()), allowing classes to implement only what they need.

- **$\textsf{\color{#008000}{Dependency inversion}}$**
    
     High-level modules should not depend on low-level modules; both should depend on abstractions. 

    - Instead of a Car class depending on a concrete GasEngine class, it should depend on an IEngine interface, allowing for easy swapping with an ElectricEngine.

## Dependency Lifecycles

- **$\textsf{\color{#008000}{Transient}}$**
    
     Whenever you $\textsf{\color{#fbbc05}{ask for the instance}}$ , it always returns $\textsf{\color{#fbbc05}{new and fresh instance}}$.

    - A NotificationService configured as transient creates a new instance each time it’s used, ideal for $\textsf{\color{#fbbc05}{lightweight, stateless services}}$.

- **$\textsf{\color{#008000}{Scope}}$**
    
     Whenever you create instance, it will be $\textsf{\color{#fbbc05}{created once per user}}$ and shared $\textsf{\color{#fbbc05}{across all the request}}$. So, $\textsf{\color{#fbbc05}{user has specific scope}}$. (e.g., HTTP request, transaction).

    - A DbContext in a web application is often scoped, so each request has its own instance, preventing data conflicts.


- **$\textsf{\color{#008000}{Singleton}}$** 
    
     A single instance is $\textsf{\color{#fbbc05}{created once}}$ and $\textsf{\color{#fbbc05}{shared throughout the application’s lifetime}}$. (heavyweight, stateful objects that are expensive to create.)

    - A ConfigurationService can be a singleton, as it’s loaded once and reused globally across all requests.

## In / Out / Ref

- **$\textsf{\color{#008000}{Ref}}$**
    
    It may be modified by the method / It must be initialized before being passed to the method.

- **$\textsf{\color{#008000}{Out}}$**
    
    It must be modified by the method / It doesn’t require that the input variable be initialized before being passed

- **$\textsf{\color{#008000}{In}}$**

    It cannot modify by the method / It must be initialized before being passed to the method.The motivation is to be used with a struct to improve performance


## Boxing vs Unboxing 

The process of converting a Value Type variable (char, int etc.) to a Reference Type variable (object) is called Boxing.

## Coupling vs Cohesion 

- **$\textsf{\color{#008000}{Coupling}}$** is the level of dependency between modules. $\textsf{\color{#fbbc05}{Low coupling is ideal}}$ because it allows modules to $\textsf{\color{#fbbc05}{function independently}}$, making the code $\textsf{\color{#fbbc05}{more maintainable and flexible}}$.

- **$\textsf{\color{#008000}{Cohesion}}$** is the degree to which functions within a module are related. $\textsf{\color{#fbbc05}{High cohesion is preferred}}$, as it means $\textsf{\color{#fbbc05}{each module has a single, focused responsibility}}$, making it easier to understand, test, and maintain.


    **The $\textsf{\color{#fbbc05}{goal}}$ is to design software with $\textsf{\color{#fbbc05}{low coupling and high cohesion}}$ to improve**

## Thread vs Task

- **Threads** $\textsf{\color{#fbbc05}{require manual management}}$, while **Tasks** $\textsf{\color{#fbbc05}{handle thread management automatically through the thread pool}}$, making tasks a simpler and often more efficient choice for concurrent programming.

## Background thread vs Foreground thread

**foreground threads** $\textsf{\color{#fbbc05}{keep the application running}}$, while **background threads** $\textsf{\color{#fbbc05}{do not}}$—they allow the application to exit even if they’re still in progress.

## Immutable

An immutable object is an object that we can’t change after we instantiate it

![ObjectTypes](/Resources/ObjectTypes.png)

## Locking

Locking is a mechanism used in C# to $\textsf{\color{#fbbc05}{ensure thread-safety}}$ in multithreaded applications. It $\textsf{\color{#fbbc05}{prevents multiple threads}}$ from $\textsf{\color{#fbbc05}{accessing shared resources}}$ (like variables or objects) simultaneously, which could lead to $\textsf{\color{#fbbc05}{race conditions}}$ or $\textsf{\color{#fbbc05}{inconsistent data}}$.

- Atomic Operations
    - Interlocked Class

- Exclusive Locking
    - Lock Statement
    - Monitor Class
    - Mutex Class
    - SpinLock Class

- Non-Exclusive Locking
    - Semaphore Class
    - ReaderWriterLockSlim Class


## Thread.Sleep vs Task.Delay

### **Thread.Sleep**
 $\textsf{\color{#fbbc05}{blocks}}$ the thread/ $\textsf{\color{#fbbc05}{synchronous}}$ operation /

### **Task.Delay**
 $\textsf{\color{#fbbc05}{non-blocking}}$ and $\textsf{\color{#fbbc05}{allows the thread to continue}}$ / $\textsf{\color{#fbbc05}{synchronous operation}}$ that $\textsf{\color{#fbbc05}{returns a Task}}$.

## What is Delegate

## Func vs Action

## What is Middleware

### Action filter vs Middleware

- **Action filters** $\textsf{\color{#fbbc05}{operate at the controller action level}}$, while **middleware applies** $\textsf{\color{#fbbc05}{more globally to all requests in the ASP.NET pipeline}}$.

- Asynchronous programming


## What is GC (Garbage collector)

**GC** is a $\textsf{\color{#fbbc05}{background service}}$ that finds objects your code $\textsf{\color{#fbbc05}{no longer uses}}$ and $\textsf{\color{#fbbc05}{frees their memory automatically}}$.


Main goals:

- Avoid memory leaks
- Avoid manual memory management bugs (double free, use-after-free, etc.)
- Trade a bit of CPU time for safer / simpler development


### Generations in practice

1. Gen 0
    - Very young objects
    - Small, short-lived (local variables, small DTOs, Linq results, etc.)
    - Collected very often, very fast

2. Gen 1
    - “Middle aged” objects that survived Gen 0
    - Acts as a buffer between Gen 0 and Gen 2

3. Gen 2
    - Long-lived objects (singletons, caches, configuration, static data)
    - Full GC: collecting Gen 2 is the most expensive and happens less frequently

4. LOH (Large Object Heap)
    - Very large objects (e.g., large arrays, big strings)
    - Allocation is expensive; collection is tied to Gen 2
    - Often not compacted (or less frequently), to avoid moving huge memory blocks