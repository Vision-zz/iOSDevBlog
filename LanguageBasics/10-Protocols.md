# Protocols

A protocol defines a blueprint of methods, properties, and other requirements that suit a particular task or piece of functionality. he protocol can then be adopted by a class, structure, or enumeration to provide an actual implementation of those requirements. Any type that satisfies the requirements of a protocol is said to conform to that protocol.

```swift
protocol ProtocolName {
	// Protocol Definition
}
```

## Property Requirements

A protocol can require any conforming type to provide an instance property or type property with a particular name and type. The protocol doesn’t specify whether the property should be a stored property or a computed property—it only specifies the required property name and type. The protocol also specifies whether each property must be gettable or gettable and settable.

Property requirements are always declared as variable properties, prefixed with the var keyword. Gettable and settable properties are indicated by writing `{ get set }` after their type declaration, and gettable properties are indicated by writing `{ get }`.

Always prefix type property requirements with the static keyword when you define them in a protocol. This rule pertains even though type property requirements can be prefixed with the class or static keyword when implemented by a class

```swift
protocol FullyNamed {
    var fullName: String { get }
}

struct Person: FullyNamed {
    var firstName: String
    var lastName: String
    var fullName: String {
        get {
            "\(firstName) \(lastName)"
        }
    }
}

var person: FullyNamed = Person(firstName: "Sachin", lastName: "Tendulkar")
print(person.fullName) // Sachin Tendulkar
```

## Method Requirements

Protocols can require specific instance methods and type methods to be implemented by conforming types. These methods are written as part of the protocol’s definition in exactly the same way as for normal instance and type methods, but without curly braces or a method body. Variadic parameters are allowed, subject to the same rules as for normal methods. Default values, however, can’t be specified for method parameters within a protocol’s definition.

```swift
protocol FullyNamed {
    func getFullname() -> String
}

struct Person: FullyNamed {
    var firstName: String
    var lastName: String
    
    func getFullname() -> String {
        "\(firstName) \(lastName)"
    }
}

var person: FullyNamed = Person(firstName: "Sachin", lastName: "Tendulkar")
print(person.getFullname()) // Sachin Tendulkar
```

## Initializer Requirements

Protocols can require specific initializers to be implemented by conforming types. You write these initializers as part of the protocol’s definition in exactly the same way as for normal initializers, but without curly braces or an initializer body:

```swift
protocol SomeProtocol {
    init(someParameter: Int)
}
```

The initiazlier can be implemented as a designated init or a convenience init. Either way the `required` keyword is needed to be mentioned before the initializer

```swift
class SomeClass: SomeProtocol {
	var dummyParameter: Int
	init(someParameter: Int) {
		self.dummyParameter = someParameter
	}
}
```

## Class Only Protocols

You can limit protocol adoption to class types (and not structures or enumerations) by adding the AnyObject protocol to a protocol’s inheritance list.

```swift
protocol SomeClassOnlyProtocol: AnyObject {
   // Protocol definition
}
```

## Protocol Composition

It can be useful to require a type to conform to multiple protocols at the same time. You can combine multiple protocols into a single requirement with a protocol composition. Protocol compositions behave as if you defined a temporary local protocol that has the combined requirements of all protocols in the composition. Protocol compositions don’t define any new protocol types.

Protocol compositions have the form SomeProtocol & AnotherProtocol. You can list as many protocols as you need, separating them with ampersands (&). In addition to its list of protocols, a protocol composition can also contain one class type, which you can use to specify a required superclass.

```swift
protocol Named {
    var name: String { get }
}
protocol Aged {
    var age: Int { get }
}
struct Person: Named, Aged {
    var name: String
    var age: Int
}
func wishHappyBirthday(to celebrator: Named & Aged) {
    print("Happy birthday, \(celebrator.name), you're \(celebrator.age)!")
}
```