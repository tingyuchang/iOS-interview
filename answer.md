## General

1. Explain `Code Sign`in iOS 
   
   ![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*YqhNRf3-OE5DZ5j_yyYeog.png)
   - generate CSR (Certificate signing request) in keychain
   - upload CSR(public key to apple, private key in your mac) to developer center
   - download certificate(.cer, publickey) from developer center
   - Provisioning Profile must be installed on each device your application code should run on. 
2. What's difference between `AppId` & `bundleId`?
   - AppId: teamId + bundleId
   - bundleId: unique id for app.
3. List options we can store data in iOS, and explain their pros & cons
   - in memory storage: array, dictionary, set, 
   - persistent: userdefault, keychain, localfile, coredata, sqllite.
4. What is the difference between `implicit` and `explicit`?
   - implicity: needs type inference like `let a = 10`
   - explicit: `let a: Int = 10` -> can reduce compile time
5. List out App life cycle
   - not running
   - inactive
   - active
   - backgruond
   - suspended
6. Major differences between Objective-C and Swift
   - Objective-C is more flexible than Swift, Swift is designed to catch programming errors much earlier. For instance, many errors that would occur at runtime in Objective-C—like sending a message to an object that doesn’t implement it—are now checked at compile-time. Objective-C can accomplish all of the things Swift can, but Swift can do so more safely. Swift supports more programming language features, like optionals, tuples and generics.
7. Explain Access level in Swift
   - `open` access enable entities to be used within any source file from their defining module, and also in a source file from another module that imports the defining module. You typically use open or public access when specifying the public interface to a framework. Classes and methods marked as open can be subclassed and overridden.
   - `public` Classes and methods can NOT be subclassed and overridden
   - `internal`: access enables entities to be used within any source file from their defining module, but not in any source file outside of that module. You typically use internal access when defining an app’s or a framework’s internal structure.
   - `file-private` access restricts the use of an entity to its own defining source file. Use file-private access to hide the implementation details of a specific piece of functionality when those details are used within an entire file.
   - `private` access restricts the use of an entity to the enclosing declaration, and to extensions of that declaration that are in the same file. Use private access to hide the implementation details of a specific piece of functionality when those details are used only within a single declaration.
8. What is an `inout` parameter?
   - In-out parameter lets you change the value of a function parameter from within the body of that function
     - When the function is called, the value of the argument is copied.
     - You modify the copy in the function body.
     - When the function returns, the copy's value is assigned back to the original argument.
   - This behavior is known as copy-in copy-out or call by value result.
9.  What is `lazy` Stored Property and what difference with Stored Property?
    - The closure associated to the lazy property is executed only if you read that property.
    - You can use self inside the closure of a lazy property. If you need to use self inside the function. In fact, if you're using a class rather than a structure, you should also declare `[unowned self]` inside your function so that you don't create a strong reference cycle(check the code below).
10. What's difference between `open` class ans `final` class
    - open: can be subclassed and overridden
    - final: can NOT be subclassed and overridden
11. What's difference between `struct` and `class`
    - struct is value type and class is reference type
    - struct is passed by copy, so when you assign struct b to struct a, a anb will be different object in memory, but class isn't, reference type is passed by reference so class a and class b will reference to the same object in class
    - class supports inheritance
    - struct don't need to care about memory issue and it's thread safe
    - struct usually stores in stack and class stores in heap
    - struct is faster than class
12. What are `failable` and `throwing` initializers?
    - failable initializer will return nil when it's occur error `init?`
13. Explain `raw` and `associated` values in enum
    - Enumeration provides a type-safe method of working with a group of related values. Raw values are compile time-set values directly assigned to every case within an enumeration, as in the example detailed below:
      - An enum cannot have both raw values and associated values at the same time.
      - The raw values of an enum must be of the same data type. But associated values can be of any type.
    - associated provide free to user to decide any type of the case.
14. What is dynamic dispatch?
    - dynamic dispatch is the mechanism that helps to decide which method implementation should be used
    - four dispatch techniques: inline(faster), static, virtual, dynamic (slowest)
    - Dynamic Dispatch is supported only by reference types (only inheritance used)
    - Dynamic Dispatch type:
      - table dispatch
      - message dispatch
15. What are type aliases?
    - A type alias allows you to provide a new name for an existing data type into your program
16. What is `escaping` closures? 
    - Escaping closure means, inside the function, you can still run the closure (or not); the extra bit of the closure is stored some place that will outlive the function. There are several ways to have a closure escape its containing function: 
      - `Asynchronous` execution: If you execute the closure asynchronously on a dispatch queue, the queue will hold onto the closure for you. You have no idea when the closure will be executed and there’s no guarantee it will complete before the function returns. 
      - `Storage`: Storing the closure to a global variable, property, or any other bit of storage that lives on past the function call means the closure has also escaped.
17. What are `designated` and `convenience` initializers?
    - Designated initializers are:
    - The CENTRAL point of initialization of a class.
      - Classes MUST have at least one.
      - Is the responsible for initializing stored properties.
      - Is the responsible for calling super init
    - Convenience initializers are:
      - SECONDARY supporting initializers for a class.
      - It can only call a designated initializer that is defined in the same class
      - It can also call another convenience initializers defined in the same class
      - They are not required, that sort of implied. they are just initializers that we can write for a CONVENIENCE use case
      - In a class, They use the keyword “convenience” before the init keyword.
    - Finally here are 3 basic rules of class initialization:
      - Every class must have a designated initializer, if this class inherits from another, the designated - initializer is responsible for calling the designated initializer of its immediate superclass.
      - Classes can have any number of convenience initializers, a convenience initializer must call another initializer from the same class, whether it is a designated initializer or another conveniences initializer.
      - Convenience initializers must ultimately call a designated initializer.
18. What are benefits of `guard`?
    - There are two big benefits to guard. 
      - One is avoiding the pyramid of doom, as others have mentioned — lots of annoying if let statements nested inside each other moving further and further to the right. 
      - The other benefit is provide an early exit out of the function using break or using return.
19. What is `defer`?
    - defer keyword provides a safe and easy way to declare a block that will be executed only when execution leaves the current scope.
20. What is the difference `Any` and `AnyObject`?
    - According to Apple’s Swift documentation: Any can represent an instance of any type at all, including function types and optional types. AnyObject can represent an instance of any class type.
21. Explain `extension` in Swift
    - Extensions add new functionality to an existing class, structure, enumeration, or protocol type. This includes the ability to extend types for which you do not have access to the original source code. Extensions are similar to categories in Objective-C.
22. What is `Property Wrappers`?
    - A property wrapper adds a layer of separation between code that manages how a property is stored and the code that defines a property.
23. What's difference between `deep` and `shallow` copy
    - There are two kinds of object copying: shallow copies and deep copies. The normal copy is a shallow copy that produces a new collection that shares ownership of the objects with the original. Deep copies create new objects from the originals and add those to the new collection.
24. What's Protocol Oriented Programming?
  - Protocol-Oriented Programming is a new programming paradigm ushered in by Swift 2.0. In the Protocol-Oriented approach, we start designing our system by defining protocols. We rely on new concepts: protocol extensions, protocol inheritance, and protocol compositions. The paradigm also changes how we view semantics. In Swift, value types are preferred over classes. However, object-oriented concepts don’t work well with structs and enums: a struct cannot inherit from another struct, neither can an enum inherit from another enum. So inheritance - one of the fundamental object-oriented concepts - cannot be applied to value types. On the other hand, value types can inherit from protocols, even multiple protocols. Thus, with POP, value types have become first class citizens in Swift.
  
## Concurrency
1. What's different ways of achieving concurrency in iOS?
   - NSThread
   - NSOperation
   - GCD
2. What is GCD?
   - low-level concurrency API
3. What's is Quality of Service (QoS)?
   - a prioritization of queues
4. What's data-racing? How to prevent this issue?
   - create you own queue
   - using actor

## Memory management
1. Explain ARC and what's difference between ARC & GC?
   - GC: has to stop the world, no retain cycle issue
   - ARC: has retain cycle issue, but no need stop the world
2. Explain retain cycle and memory leak
   - class has strong reference on class b and class b has strong reference on class a as well
   - they had strong reference with each other so it's impossible to deinit them
   - the object is no longer used but system can't release it, that is memory leak.
3. What's difference between `weak` and `unowned`?
   - weak: return Optional 
   - unowned: non-optional 
they both not increase reference count 
