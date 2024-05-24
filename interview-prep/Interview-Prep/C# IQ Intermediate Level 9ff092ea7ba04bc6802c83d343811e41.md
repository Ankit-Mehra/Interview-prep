# C# IQ Intermediate Level

## 👦🏻 Intermediate Level

**11. Describe the differences between abstract classes and interfaces in C#. When would you use each?**

- **Abstract Classes**:
    - An abstract class is a class that cannot be instantiated and is typically used as a base class for other classes.
    - It can have a mix of abstract (unimplemented) and concrete (implemented) methods.
    - Abstract classes can have fields, properties, and constructors.
    - A class can inherit from only one abstract class.
    - You can use the `abstract` keyword to declare an abstract class.

Example:

```csharp
public abstract class Shape
{
    public abstract double CalculateArea();
}

public class Circle : Shape
{
    public double Radius { get; set; }

    public override double CalculateArea()
    {
        return Math.PI * Radius * Radius;
    }
}
```

- **Interfaces**:
    - An interface defines a contract of methods, properties, events, or indexers that implementing classes must provide.
    - Interfaces only contain method signatures and properties (without implementations) or only abstract members.
    - A class can implement multiple interfaces.
    - You use the `interface` keyword to declare an interface.

Example:

```csharp
public interface IDrawable
{
    void Draw();
}

public class Circle : IDrawable
{
    public void Draw()
    {
        // Implement the drawing logic for a circle
    }
}
```

You would use an abstract class when you want to provide a common base with some shared implementation and potentially enforce certain behaviors. Interfaces are used when you want to define a contract for classes to adhere to, often for scenarios where multiple classes need to implement the same set of methods but may have different implementations.

### **When to Use Each:**

- **Use Abstract Classes:**
    - When you want to provide a common base implementation for derived classes.
    - When you need to define non-public members or member with different access modifiers.
    - When you want to use constructors in your abstraction.
- **Use Interfaces:**
    - When you want to define a contract that multiple unrelated classes can implement.
    - When a class needs to inherit from multiple sources (C# doesn't support multiple inheritance for classes).
    - When you want to achieve a level of abstraction without providing any default implementation.

**12. How does exception handling work in C#? Explain the `try`, `catch`, and `finally` blocks.**

Exception handling in C# allows you to gracefully handle runtime errors and exceptions that may occur during program execution. It involves three main blocks:

- `try` block: This block contains the code where you anticipate an exception might occur. If an exception occurs within the `try` block, it will be caught by a matching `catch` block.
- `catch` block: When an exception occurs in the `try` block, the control is transferred to the corresponding `catch` block, which contains code to handle the exception. You can specify the type of exception to catch, or use a generic `catch` block to catch any exception.
- `finally` block: The `finally` block, if provided, is executed regardless of whether an exception occurred or not. It's typically used for cleanup code that must be executed, such as closing files or releasing resources.

Example:

```csharp
try
{
    // Code that may cause an exception
    int result = 10 / int.Parse("0");
}
catch (DivideByZeroException ex)
{
    // Handle a specific exception
    Console.WriteLine("Division by zero is not allowed.");
}
catch (Exception ex)
{
    // Handle any other exception
    Console.WriteLine($"An error occurred: {ex.Message}");
}
finally
{
    // Cleanup code
    Console.WriteLine("Cleanup code executed.");
}

```

In this example, if a `DivideByZeroException` occurs, the first `catch` block will handle it. If any other exception occurs, the second `catch` block will handle it. The `finally` block will always execute, regardless of whether an exception occurred or not.

**13. What is the purpose of LINQ (Language-Integrated Query) in C#? Provide an example of using LINQ**

**LINQ (Language-Integrated Query)** is a feature in C# that provides a unified way to query and manipulate data from various sources, such as collections, databases, XML, and more. LINQ allows developers to write queries directly within the C# code, providing a consistent and expressive syntax for data manipulation.

LINQ queries are similar to SQL queries, and they can be used with various data sources. LINQ expressions are written using a declarative syntax, making it easier to express complex queries with less code.

### Example of LINQ Query with a Collection:

Let's consider a simple example using a collection of `Person` objects:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}

public class Program
{
    public static void Main()
    {
        // Creating a list of Person objects
        List<Person> people = new List<Person>
        {
            new Person { Name = "Alice", Age = 25 },
            new Person { Name = "Bob", Age = 30 },
            new Person { Name = "Charlie", Age = 22 },
            new Person { Name = "David", Age = 35 }
        };

        // LINQ query to retrieve names of people older than 25
        var result = from person in people
                     where person.Age > 25
                     select person.Name;

        // Displaying the result
        foreach (var name in result)
        {
            Console.WriteLine(name);
        }
    }
}
```

### LINQ Method Syntax:

The same query can be expressed using the method syntax, which is an alternative to the query syntax:

```csharp
var result = people
    .Where(person => person.Age > 25)
    .Select(person => person.Name);
```

Both query and method syntax are interchangeable, and developers can choose the style that they find more readable or suitable for a given situation.

LINQ is a powerful tool for querying and manipulating data in a concise and expressive manner, making it a valuable feature for C# developers working with diverse data sources.

**Explain the difference between IEnumerable and IQueryable in the context of LINQ. How does deferred execution work?**

**IEnumerable and IQueryable** are both interfaces in C# that are commonly used in the context of LINQ (Language-Integrated Query). While they both represent sequences of data, they have different characteristics and are suitable for different scenarios.

### 1. **IEnumerable:**

- **Characteristics:**
    - Represents a forward-only cursor of data.
    - Suitable for in-memory collections like arrays, lists, and other IEnumerable implementations.
    - Queries using IEnumerable are executed locally in memory.
    - Works with LINQ to Objects.
- **Example:**
    
    ```csharp
    IEnumerable<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
    var result = numbers.Where(x => x > 2);
    ```
    
- **Use Case:**
    - Best suited for querying in-memory collections.
    - Performs well when working with data that is already in memory.

### 2. **IQueryable:**

- **Characteristics:**
    - Represents a query that can be executed against a specific data source (e.g., a database).
    - Suitable for remote data sources like databases.
    - Queries using IQueryable are converted into a form that can be executed on the data source (e.g., SQL queries).
    - Works with LINQ to Entities (Entity Framework), LINQ to SQL, and other providers.
- **Example:**
    
    ```csharp
    IQueryable<int> numbers = dbContext.Numbers;
    var result = numbers.Where(x => x > 2);
    ```
    
- **Use Case:**
    - Best suited for querying external data sources.
    - Provides better performance when working with large datasets, as the query is executed on the data source.

### Deferred Execution:

Deferred execution is a key concept in LINQ, and it means that the execution of a query is delayed until the actual results are enumerated or the query is explicitly executed. Both IEnumerable and IQueryable support deferred execution.

**How Deferred Execution Works:**

1. **Building the Query:** When you create a LINQ query using IEnumerable or IQueryable, the query is not immediately executed. Instead, the query is built as an expression tree.
2. **Execution Triggered:** The query is executed when an operation triggers enumeration, such as calling `ToList()`, `ToArray()`, or using a foreach loop. For IQueryable, the query may also be executed when certain extension methods like `First()`, `Count()`, or `Single()` are called.

**Example:**

```csharp
IEnumerable<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
var query = numbers.Where(x => x > 2);

// The query is not executed here

foreach (var item in query)
{
    // The query is executed when enumerating the results
    Console.WriteLine(item);
}
```

In the context of IQueryable, the query may be translated into a SQL query and executed on the database server when enumeration is triggered.

In summary, while both IEnumerable and IQueryable support deferred execution, they are designed for different scenarios. IEnumerable is suitable for in-memory collections, and IQueryable is designed for querying external data sources, providing the ability to generate optimized queries for those sources.

**14. Explain the concept of inheritance and polymorphism in C# with examples.**

### Inheritance in C#:

Inheritance is a fundamental concept in object-oriented programming (OOP) that allows a class (called the derived class or child class) to inherit properties and behaviors from another class (called the base class or parent class). This promotes code reusability and the creation of a hierarchy of classes.

**Example of Inheritance:**

```csharp
public class Animal
{
    public void Eat()
    {
        Console.WriteLine("Animal is eating.");
    }

    public void Sleep()
    {
        Console.WriteLine("Animal is sleeping.");
    }
}

public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Dog is barking.");
    }
}
```

### Polymorphism in C#:

Polymorphism is the ability of a class to take on multiple forms. In C#, polymorphism is achieved through two mechanisms: method overriding (runtime polymorphism) and method overloading (compile-time polymorphism).

1. **Method Overriding (Runtime Polymorphism):**
    
    In method overriding, a method in the base class is redefined in the derived class with the same signature. The actual method that gets executed is determined at runtime based on the type of the object.
    
    **Example:**
    
    ```csharp
    public class Animal
    {
        public virtual void MakeSound()
        {
            Console.WriteLine("Animal makes a sound.");
        }
    }
    
    public class Dog : Animal
    {
        public override void MakeSound()
        {
            Console.WriteLine("Dog barks.");
        }
    }
    ```
    
2. **Method Overloading (Compile-Time Polymorphism):**
    
    In method overloading, multiple methods in the same class have the same name but different parameter lists. The correct method to call is determined at compile time based on the method signature.
    
    **Example:**
    
    ```csharp
    public class Calculator
    {
        public int Add(int a, int b)
        {
            return a + b;
        }
    
        public double Add(double a, double b)
        {
            return a + b;
        }
    }
    ```
    
    Here, the `Add` method is overloaded with different parameter types (int and double). The appropriate method is called based on the types of arguments provided during the method invocation.
    

### Using Inheritance and Polymorphism Together:

```csharp
Animal myDog = new Dog();
myDog.MakeSound(); // Calls the overridden method in Dog class
```

In summary, inheritance allows classes to share and reuse code, while polymorphism enables objects to take multiple forms, allowing for flexibility in method invocation and code execution.

Inheritance and polymorphism are fundamental concepts in object-oriented programming (OOP) that play a significant role in C#. Let's delve into these concepts in detail with examples:

[C# Polymorphism (w3schools.com)](https://www.w3schools.com/cs/cs_polymorphism.php)

**15. Discuss the importance of access modifiers (e.g., `public`, `private`, `protected`) in C# and provide examples for scenarios for their use.**

Access modifiers in C# play a crucial role in defining the visibility and accessibility of classes, methods, and other members within a program. They help enforce encapsulation, control the exposure of code elements, and define the level of access that other parts of the program have to those elements. There are several access modifiers in C#, including `public`, `private`, `protected`, `internal`, and `protected internal`. Here's a discussion of their importance and examples for their use:

### 1. `public`:

- **Importance:**
    - Members with the `public` access modifier are accessible from any part of the program, including outside the defining class and from other assemblies.
    - This is often used for members that are meant to be part of the public interface of a class or library.
- **Example:**
    
    ```csharp
    public class Calculator
    {
        public int Add(int a, int b)
        {
            return a + b;
        }
    }
    ```
    

### 2. `private`:

- **Importance:**
    - Members with the `private` access modifier are only accessible within the same class or struct.
    - This promotes encapsulation by restricting direct access from outside the class, allowing the class to control its internal state.
- **Example:**
    
    ```csharp
    public class BankAccount
    {
        private decimal balance;
    
        public void Deposit(decimal amount)
        {
            balance += amount;
        }
    
        public void Withdraw(decimal amount)
        {
            if (amount <= balance)
                balance -= amount;
        }
    }
    ```
    

### 3. `protected`:

- **Importance:**
    - Members with the `protected` access modifier are accessible within the same class and its derived classes.
    - This facilitates the implementation of inheritance and allows derived classes to access or override certain behaviors.
- **Example:**
    
    ```csharp
    public class Shape
    {
        protected int width;
        protected int height;
    }
    
    public class Rectangle : Shape
    {
        public void SetDimensions(int w, int h)
        {
            width = w;   // Accessible because of the protected modifier
            height = h;  // Accessible because of the protected modifier
        }
    }
    ```
    

### 4. `internal`:

- **Importance:**
    - Members with the `internal` access modifier are accessible within the same assembly but not from outside it.
    - This is useful for creating components within an assembly that should not be exposed to external assemblies.
- **Example:**
    
    ```csharp
    // Assembly A
    internal class InternalComponent
    {
        // Implementation details hidden from external assemblies
    }
    ```
    

### 5. `protected internal`:

- **Importance:**
    - Members with the `protected internal` access modifier are accessible within the same assembly or from derived classes in other assemblies.
    - This combines the benefits of `protected` and `internal`, allowing a broader scope of accessibility.
- **Example:**
    
    ```csharp
    // Assembly A
    public class BaseClass
    {
        protected internal int Data;
    }
    
    // Assembly B
    public class DerivedClass : BaseClass
    {
        public void AccessData()
        {
            Console.WriteLine(Data);  // Accessible because of protected internal
        }
    }
    ```
    

### Conclusion:

Access modifiers in C# provide a powerful mechanism for controlling the visibility and accessibility of code elements. They contribute to encapsulation, maintainability, and the overall design of object-oriented programs by allowing developers to carefully define how parts of their code can be used or extended by other parts of the program or even external components. The appropriate choice of access modifiers depends on the desired level of encapsulation and the intended use of the code elements.

**16. What are delegates and events in C#? How are they different from regular methods and fields?**

### Delegates in C#:

A delegate in C# is a type that represents a reference to a method. It allows you to treat methods as first-class citizens, meaning you can pass them as parameters, store them in variables, and invoke them dynamically. Delegates are often used to implement callback mechanisms, event handling, and other scenarios where you want to decouple the sender of a request from the object that processes the request.

**Example of a Delegate:**

```csharp
// Declaration of a delegate
public delegate void MyDelegate(string message);

public class MessagePrinter
{
    // Method that matches the delegate signature
    public static void PrintMessage(string message)
    {
        Console.WriteLine(message);
    }
}

public class Program
{
    public static void Main()
    {
        // Instantiating the delegate with the PrintMessage method
        MyDelegate myDelegate = MessagePrinter.PrintMessage;

        // Invoking the delegate
        myDelegate("Hello, delegates!");
    }
}
```

### Events in C#:

Events are a higher-level abstraction built on top of delegates. They provide a way for a class or object to notify other classes or objects when certain actions occur. Events are declared using the `event` keyword and are associated with a delegate type.

**Example of an Event:**

```csharp
public class Button
{
    // Declaration of an event using a delegate
    public event EventHandler Clicked;

    // Method to simulate a button click
    public void Click()
    {
        Console.WriteLine("Button clicked!");

        // Triggering the event
        OnClicked();
    }

    protected virtual void OnClicked()
    {
        // Checking if any subscribers (delegates) are attached to the event
        Clicked?.Invoke(this, EventArgs.Empty);
    }
}

public class Program
{
    public static void Main()
    {
        Button myButton = new Button();

        // Subscribing to the Clicked event with an anonymous method
        myButton.Clicked += (sender, e) => Console.WriteLine("EventHandler: Button was clicked!");

        // Simulating a button click
        myButton.Click();
    }
}

```

In this example, the `Button` class has a `Clicked` event associated with the `EventHandler` delegate. When the `Click` method is called, it triggers the `Clicked` event, invoking any methods (delegates) that are subscribed to it.

### Differences from Regular Methods and Fields:

1. **Dynamic Invocation:**
    - Delegates and events allow for dynamic invocation of methods. The method to be executed can be determined at runtime.
2. **Decoupling:**
    - Delegates and events provide a level of decoupling between the sender and receiver of a message or event. The sender does not need to know the concrete types of the receivers.
3. **Multiple Subscribers:**
    - Multiple methods can be subscribed to a single event, allowing for multiple listeners to respond to an action.
4. **Extension of Behavior:**
    - Delegates and events can extend the behavior of a class without modifying its code directly, promoting modularity and flexibility.
5. **Syntax:**
    - Delegates and events have specific syntax (delegate keyword, event keyword) that distinguishes them from regular methods and fields.

While regular methods and fields are fundamental building blocks of a class, delegates and events provide a more flexible and extensible way to handle certain scenarios, particularly those involving communication between different parts of a program. They are especially useful in GUI programming, asynchronous programming, and other situations where loose coupling and dynamic invocation are beneficial.

**17. How does garbage collection work in C#? What is the role of the garbage collector?**

Garbage collection in C# is the automatic process of reclaiming memory that is no longer in use by objects in the managed heap (the area of memory where C# objects are allocated). The role of the garbage collector is to:

- Identify objects in memory that are no longer accessible or referenced by the application.
- Reclaim the memory occupied by these unreachable objects.
- Defragment and compact the memory to minimize fragmentation and improve memory usage.

The garbage collector operates in the background, periodically identifying and collecting garbage objects. Developers do not need to manually deallocate memory as in languages like C or C++.

Here's a simplified overview of how garbage collection works:

1. The garbage collector starts with a set of "root" objects, which are typically global objects, static objects, and local variables in the current call stack.
2. It traces the object graph by following references from root objects to other objects in memory.
3. Objects that are not reachable from the root objects are considered garbage and are marked for collection.
4. The garbage collector reclaims the memory occupied by the garbage objects.

Garbage collection helps prevent memory leaks and makes memory management more automatic and robust in C#.

**18. What is the difference between value type and reference type conversions in C#?**

In C#, you can convert between value types and reference types, but there are important differences:

- **Value Type Conversion**:
Value type conversion involves converting between different value types (e.g., int to double, float to int). It's typically done implicitly by the compiler when there's no risk of data loss.
    
    Example:
    
    ```csharp
    int intValue = 42;
    double doubleValue = intValue; // Implicit conversion from int to double
    ```
    
- **Reference Type Conversion**:
Reference type conversion involves converting between different reference types, such as classes or interfaces. It often requires explicit casting.
    
    Example:
    
    ```csharp
    class Animal { }
    class Dog : Animal { }
    
    Animal animal = new Dog();
    Dog dog = (Dog)animal; // Explicit casting from Animal to Dog
    ```
    

The main difference is that value type conversion usually involves implicit conversions, whereas reference type conversions require explicit casting. Additionally, reference type conversions can lead to runtime errors (e.g., `InvalidCastException`) if the types are not compatible.

**19. Can you explain the concept of asynchronous programming in C# using `async` and `await` keywords?**

Asynchronous programming in C# is a powerful feature that allows you to write code that can perform non-blocking operations, making your applications more responsive and efficient. This is especially useful when dealing with I/O-bound or long-running tasks, such as reading from a database, making network requests, or processing large files. Asynchronous programming is achieved using the `async` and `await` keywords, which work together to manage asynchronous operations.

Here's a detailed explanation of asynchronous programming in C# using examples:

**1. `async` Method Declaration:**

To define an asynchronous method, you use the `async` keyword in the method declaration. An asynchronous method returns a `Task` or `Task<T>` representing the ongoing operation.

```csharp
public async Task MyAsyncMethod()
{
    // Asynchronous operations go here
}
```

**2. `await` Keyword:**

Inside an asynchronous method, you use the `await` keyword to await the completion of asynchronous operations, such as I/O-bound tasks, network requests, or other async methods. The `await` keyword indicates that control can be returned to the calling method while the awaited operation executes, allowing the thread to be free for other tasks.

```csharp
public async Task MyAsyncMethod()
{
    // Perform some synchronous work

    // Await an asynchronous operation
    var result = await SomeAsyncOperationAsync();

    // Continue with more work
}
```

**Example: Asynchronous File Reading**

Let's take an example of reading a text file asynchronously using the `System.IO.File` class. Here's how you can do it:

```csharp
using System;
using System.IO;
using System.Threading.Tasks;

public class FileReadExample
{
    public async Task ReadFileAsync()
    {
        try
        {
            string filePath = "sample.txt";

            // Asynchronously read the file
            using (StreamReader reader = new StreamReader(filePath))
            {
                string content = await reader.ReadToEndAsync();
                Console.WriteLine(content);
            }
        }
        catch (FileNotFoundException)
        {
            Console.WriteLine("File not found.");
        }
        catch (Exception ex)
        {
            Console.WriteLine("An error occurred: " + ex.Message);
        }
    }
}
```

In this example:

- We declare an asynchronous method `ReadFileAsync`.
- Inside the method, we use `StreamReader` to read the contents of a file asynchronously using `await reader.ReadToEndAsync()`.
- The method can be invoked asynchronously, and control is returned to the caller while the file is being read.

**3. Error Handling:**

When using asynchronous code, it's essential to handle exceptions properly. You can use `try...catch` blocks as shown in the example above. Additionally, you can use `Task.Exception` or `AggregateException` to handle exceptions raised during asynchronous operations.

**4. `async` and `await` Best Practices:**

- Use asynchronous I/O operations whenever possible to avoid blocking the main thread.
- Avoid mixing synchronous and asynchronous code within the same method to prevent deadlocks.
- Be aware of proper error handling and exception propagation.
- Use `ConfigureAwait(false)` when awaiting in library code to avoid potential deadlocks in UI applications.
- Consider using `async` all the way up the call stack if you have multiple methods calling each other.

Asynchronous programming in C# is a powerful tool for building responsive and efficient applications. It allows you to perform tasks concurrently, utilize resources effectively, and create more responsive user interfaces. However, it's essential to understand the `async` and `await` keywords and apply best practices to ensure smooth and reliable asynchronous code execution.

**20. What is dependency injection, and how is it implemented in C#?**

**Dependency Injection (DI)** is a design pattern and a fundamental concept in software engineering that deals with the management of object dependencies within an application. It is a technique for achieving [Inversion of Control (IoC)](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/architectural-principles#dependency-inversion), where the control over the creation and management of objects is shifted from the application code to a separate component, typically called an Inversion of Control Container or DI Container. DI promotes loose coupling, modularity, and testability by allowing components to request their dependencies rather than creating them directly.

In the context of DI:

- **Dependency**: A dependency is an object that another object relies on to perform its function. For example, a `Logger` class may depend on a `FileWriter` class to write logs to a file.
- **Dependency Injection Container**: This is a container or framework that manages the creation and resolution of dependencies. It allows you to configure which implementations should be used for specific interfaces or classes and provides instances of those implementations when needed.
- **Dependency Injection**: This is the process of providing an object with its dependencies. Instead of the object creating its dependencies, they are provided or "injected" into the object from outside. This can be achieved through constructors, properties, or methods.

**Implementation in C# with Examples:**

Let's explore how DI is implemented in C# using examples:

**1. Constructor Injection:**

Constructor injection is the most common form of DI, where dependencies are injected through a class's constructor.

```csharp
public interface ILogger
{
    void Log(string message);
}

public class ConsoleLogger : ILogger
{
    public void Log(string message)
    {
        Console.WriteLine(message);
    }
}

public class OrderProcessor
{
    private readonly ILogger _logger;

    public OrderProcessor(ILogger logger)
    {
        _logger = logger;
    }

    public void ProcessOrder(Order order)
    {
        // Business logic
        _logger.Log("Order processed: " + order.Id);
    }
}

// Composition Root (Main Program)
class Program
{
    static void Main()
    {
        ILogger logger = new ConsoleLogger(); // Resolve the dependency
        OrderProcessor orderProcessor = new OrderProcessor(logger);
        Order order = new Order { Id = 1, Amount = 100 };
        orderProcessor.ProcessOrder(order);
    }
}
```

**2. Property Injection:**

Property injection involves injecting dependencies through public properties of a class. It's less common than constructor injection but can be useful in certain scenarios.

```csharp
public class CustomerService
{
    public ILogger Logger { get; set; }

    public void AddCustomer(Customer customer)
    {
        // Business logic
        Logger.Log("Customer added: " + customer.Name);
    }
}

// Composition Root (Main Program)
class Program
{
    static void Main()
    {
        CustomerService customerService = new CustomerService();
        customerService.Logger = new ConsoleLogger(); // Inject the dependency
        Customer customer = new Customer { Id = 1, Name = "Alice" };
        customerService.AddCustomer(customer);
    }
}
```

**3. Method Injection:**

Method injection involves injecting dependencies directly into methods when they are needed.

```csharp
public class OrderProcessor
{
    public void ProcessOrder(Order order, ILogger logger)
    {
        // Business logic
        logger.Log("Order processed: " + order.Id);
    }
}

// Composition Root (Main Program)
class Program
{
    static void Main()
    {
        ILogger logger = new ConsoleLogger();
        OrderProcessor orderProcessor = new OrderProcessor();
        Order order = new Order { Id = 1, Amount = 100 };
        orderProcessor.ProcessOrder(order, logger); // Inject the dependency
    }
}
```

**4. DI Container (e.g., Autofac, Unity, Ninject):**

Using a DI container simplifies the configuration and management of dependencies. Here's an example using Autofac as a DI container:

```csharp
// Register dependencies in a composition root (e.g., Startup.cs in ASP.NET Core)
var builder = new ContainerBuilder();
builder.RegisterType<ConsoleLogger>().As<ILogger>();
builder.RegisterType<OrderProcessor>();
var container = builder.Build();

// Resolve and use dependencies
using (var scope = container.BeginLifetimeScope())
{
    var orderProcessor = scope.Resolve<OrderProcessor>();
    Order order = new Order { Id = 1, Amount = 100 };
    orderProcessor.ProcessOrder(order);
}
```

Using DI and a DI container helps decouple components in your application, making it more maintainable, testable, and extensible. It also simplifies the management of object creation, reduces code duplication, and promotes best practices in software design.

![Untitled](C#%20IQ%20Intermediate%20Level%209ff092ea7ba04bc6802c83d343811e41/Untitled.png)

![Untitled](C#%20IQ%20Intermediate%20Level%209ff092ea7ba04bc6802c83d343811e41/Untitled%201.png)

### **Using ASP.NET Core Dependency Injection:**

ASP.NET Core comes with a built-in dependency injection container that provides more advanced features for managing dependencies. Here's a brief example:

```csharp

public interface ILogger
{
    void Log(string message);
}

public class ConsoleLogger : ILogger
{
    public void Log(string message)
    {
        Console.WriteLine(message);
    }
}

public class OrderProcessor
{
    private readonly ILogger _logger;

    public OrderProcessor(ILogger logger)
    {
        _logger = logger;
    }

    public void ProcessOrder(string order)
    {
        // Process the order

        // Log a message using the injected logger
        _logger.Log("Order processed: " + order);
    }
}

public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Registering dependencies with the container
        services.AddSingleton<ILogger, ConsoleLogger>();
        services.AddTransient<OrderProcessor>();
    }
}

public class Program
{
    public static void Main()
    {
        // Setting up ASP.NET Core host and services
        var host = Host.CreateDefaultBuilder()
            .ConfigureServices((context, services) => { new Startup().ConfigureServices(services); })
            .Build();

        // Creating a scope to resolve dependencies
        using (var scope = host.Services.CreateScope())
        {
            // Resolving dependencies and processing an order
            var orderProcessor = scope.ServiceProvider.GetRequiredService<OrderProcessor>();
            orderProcessor.ProcessOrder("12345");
        }
    }
}
```

Whether using basic dependency injection or a more sophisticated framework like ASP.NET Core's, the key idea is to invert the control of object creation and management, making the code more modular, testable, and maintainable. It also promotes the single responsibility principle, as classes are responsible for either doing their work or managing their dependencies, but not both.

[Dependency injection - .NET | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection)

**What are the four pillars of OOP, and how are they implemented in C#? Explain encapsulation, inheritance, polymorphism, and abstraction.**

The four pillars of Object-Oriented Programming (OOP) are fundamental principles that guide the design and implementation of object-oriented systems. These pillars are:

1. **Encapsulation:**
    - **Definition:** Encapsulation is the bundling of data (attributes) and methods (functions) that operate on the data into a single unit, called a class. It restricts direct access to some of the object's components and can prevent the accidental modification of data.
    - **Implementation in C#:** Encapsulation is achieved through the use of access modifiers (public, private, protected) and properties. Private fields are encapsulated within a class, and external access is controlled through getter and setter methods.
    
    ```csharp
    public class Person
    {
        private string name;
        private int age;
    
        public string Name
        {
            get { return name; }
            set { name = value; }
        }
    
        public int Age
        {
            get { return age; }
            set { age = value; }
        }
    }
    ```
    
2. **Inheritance:**
    - **Definition:** Inheritance is a mechanism that allows a new class (subclass or derived class) to inherit properties and behaviors of an existing class (base class or parent class). It promotes code reuse and establishes a "is-a" relationship between classes.
    - **Implementation in C#:** Inheritance is realized using the `:` symbol. The derived class inherits members from the base class. C# supports single inheritance (a class can inherit from only one class) but supports multiple interface inheritance.
    
    ```csharp
    public class Animal
    {
        public void Eat()
        {
            Console.WriteLine("Animal is eating.");
        }
    }
    
    public class Dog : Animal
    {
        public void Bark()
        {
            Console.WriteLine("Dog is barking.");
        }
    }
    ```
    
3. **Polymorphism:**
    - **Definition:** Polymorphism allows objects of different types to be treated as objects of a common base type. It enables a single interface to be used for different types of objects, leading to more flexible and reusable code.
    - **Implementation in C#:** Polymorphism is achieved through method overriding (in the case of inheritance) and through interfaces. Method overriding allows a derived class to provide a specific implementation of a method in the base class.
    
    ```csharp
    public class Shape
    {
        public virtual void Draw()
        {
            Console.WriteLine("Drawing a shape.");
        }
    }
    
    public class Circle : Shape
    {
        public override void Draw()
        {
            Console.WriteLine("Drawing a circle.");
        }
    }
    ```
    
4. **Abstraction:**
    - **Definition:** Abstraction is the process of simplifying complex systems by modeling classes based on the essential properties and behaviors they share. It hides the complex implementation details and focuses on the relevant features.
    - **Implementation in C#:** Abstraction is implemented through abstract classes and interfaces. Abstract classes cannot be instantiated and may contain abstract (unimplemented) methods. Interfaces define a contract for classes to implement.
    
    ```csharp
    public abstract class Shape
    {
        public abstract void Draw();
    }
    
    public interface IResizable
    {
        void Resize(int factor);
    }
    ```
    

These four pillars work together to provide a foundation for building maintainable, scalable, and modular software systems in C# and other object-oriented programming languages. They promote code organization, reusability, and the creation of systems that are easier to understand and maintain.

[Legal ](C#%20IQ%20Intermediate%20Level%209ff092ea7ba04bc6802c83d343811e41/Legal%20a0398611ebb4460183983044e477c3c6.md)