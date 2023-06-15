# Interview Questions

## General

1. Explain `Code Sign`in iOS 
2. What's difference between `AppId` & `bundleId`?
3. List options we can store data in iOS, and explain their pros & cons
4. What is the difference between `implicit` and `explicit`?
5. List out App life cycle
6. Major differences between Objective-C and Swift
7. Explain Access level in Swift
8. What is an `inout` parameter?
9. What is `lazy` Stored Property and what difference with Stored Property?
10. What's difference between `open` class ans `final` class
11. What's difference between `struct` and `class`
12. What are `failable` and throwing initializers?
13. Explain `raw` and `associated` values in enum
14. What is dynamic dispatch?
15. What are type aliases?
16. What is `escaping` closures? 
17. What are `designated` and `convenience` initializers?
18. What are benefits of `guard`?
19. What is `defer`?
20. What is the difference `Any` and `AnyObject`?
21. Explain `extension` in Swift
22. What is `Property Wrappers`?
23. What is the difference in functional programming and OOPS?
24. What's difference between `deep` and `shallow` copy
25. What's Protocol Oriented Programming?

## Concurrency
1. What's different ways of achieving concurrency in iOS?
2. What is GCD?
3. What's is Quality of Service (QoS)?
4. What's data-racing? How to prevent this issue?

## Memory management
1. Explain ARC and what's difference between ARC & GC?
2. Explain retain cycle and memory leak
3. What's difference between weak and unowned?

## Coding in/output questions

```Swift
var a = 6
var b = 9

let newClosure: () -> () = { [a, b] in
    print(a+b)
}

a = 2
b = 4
newClosure()  // -> 15
```

```Swift
print("1")
DispatchQueue.main.async {
    print("2")
    DispatchQueue.main.async {
        print(3)
    }
    print("4")
}
print("5")
// -> 1 5 2 4 3
```
```Swift
for i in 0...10 {
    DispatchQueue.main.async {
        DispatchQueue.main.async {
            print("print1",i)
        }
        print("print2",i)
    }
}
// -> print2 0 ... print2 10, print1 0 ...print1 10
```

```Swift
for i in 0...10 {
    DispatchQueue.main.async {
        DispatchQueue.main.sync {
            print("Print1",i)
        }
        print("Print2",i)
    }
}
// -> deadlock
```
```Swift
for i in 0...10 {
    DispatchQueue.main.async {
        DispatchQueue.global().sync {
            print("Print1",i)
        }
        print("Print2",i)
    }
}
// -> print1 0, print2 0 ... print1 10, print2 10
```

```Swift
for i in 0...10 {
    DispatchQueue.main.async {
        DispatchQueue.global().async {
            print("Print1",i)
        }
        print("Print2",i)
    }
}
// -> print2 0 print1 0 ... print2 10, print1 10
```

### What's problem for the following code? how to fix it?
```Swift
class Address {
  var fullAddress: String
  var city: String
  
  init(fullAddress: String, city: String) {
    self.fullAddress = fullAddress
    self.city = city
  }
}

class Person {
  var name: String
  var address: Address
  
  init(name: String, address: Address) {
    self.name = name
    self.address = address
  }
}

var headquarters = Address(fullAddress: "123 Tutorial Street", city: "Appletown")
var ray = Person(name: "Ray", address: headquarters)
var brian = Person(name: "Brian", address: headquarters)

// ray & brain's address are the same reference
```

```Swift
public class ThermometerClass {
  private(set) var temperature: Double = 0.0
  public func registerTemperature(_ temperature: Double) {
    self.temperature = temperature
  }
}

let thermometerClass = ThermometerClass()
thermometerClass.registerTemperature(56.0)

public struct ThermometerStruct {
  private(set) var temperature: Double = 0.0
  public mutating func registerTemperature(_ temperature: Double) {
    self.temperature = temperature
  }
}

let thermometerStruct = ThermometerStruct()
thermometerStruct.registerTemperature(56.0)

// thermometerStruct is immutable variable
```







-- can skip --
## UI
1. Explain difference between frame & boudle
## Objective-C
2. Expalin @synthesize and @dynamic in objc
3. Explain retain and copy in objc
