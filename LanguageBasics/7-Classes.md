# Classes

A class is a blueprint of a object. Classes are similar to structures in most ways. But they both differ in some parts

- Classes are reference types while structs are value types.
- Classes support inheritance and typecasting.
- Classes have deinitializers.

```swift
class ClassName {
	// class definition
}
```

## Initializers

Classes does not support memberwise intializers automatically. Initializers are needed to be created otherwise compile time error will be thrown. Initializers can be failable, meaning that the initializers can return nil instead of a instance due to any reasons

```swift
class Number {
    var number: Int
    
    init?(_ num: Int) {
        if num < 0 {
            return nil
        }
        self.number = num
    }
}

let arr = [10, 5, 0, -5, -10]
for x in arr {
    if let num = Number(x) {
        print(num.number)
    } else {
        print("Invalid number")
    }
}
```

**Output**

```
10
5
0
Invalid number
Invalid number
```

## Deinitializers

Swift provides options for classes to have deinitializers. It is created by using the `deinit` keyword. Deinitializer of a class is called right before when the class is about to be deinitialized.

```swift

class Number {
    var number: Int
    
    init?(_ num: Int) {
        if num < 0 {
            return nil
        }
        self.number = num
    }
    
    deinit {
        print("Number \(number) is deinitialized")
    }
    
    
}

let arr = [10, 5, 0, -5, -10]

for x in arr {
    if let num = Number(x) {
        print(num.number)
    } else {
        print("Invalid number")
    }
}
```

**Output**

```
10
Number 10 is deinitialized
5
Number 5 is deinitialized
0
Number 0 is deinitialized
Invalid number
Invalid number
```

## Inheritance

Swift supports inheritance just like other languages. Class that inherits properties and methods from another class is called as Sub class / Child class and the class from which the methods and properties are inherited is called as Super class / Parent class.

```swift
class ClassName : SuperClassName {
	// Class Members
}
```

**Example**

```swift
class Animal {
    var canFly: Bool
    
    init(canFly: Bool) {
        self.canFly = canFly
    }
    
    func makeSound() {
        print("Animal noises")
    }
}

class Dog: Animal {
     init() {
        super.init(canFly: false)
    }
    
    override func makeSound() {
        print("Dog sound")
    }
}

class Bird: Animal {
    init() {
        super.init(canFly: true)
    }
    
    override func makeSound() {
        print("Bird sound")
    }
}

var dog = Dog()
var bird = Bird()
dog.makeSound()
bird.makeSound()
```

**Output**

```
Dog sound
Bird sound
```