# The Basics

Swift is a programming language used to create applications for all the Apple devices available out there

## Type Category

- #### Value Types
	Value type instance holds its data in a independent memory

	```swift
	var tuple1 = ("tuple", "ONE")
	var tuple2 = tuple1
	tuple2.1 = "TWO"
	print(tuple1) // ("tuple", "ONE")
	print(tuple2) // ("tuple", "TWO")
	```
	Here `tuple2` is a new copy of `tuple1` and changing the values of `tuple2` does not affect `tuple1`

- #### Reference Types
	Reference type instance share a single copy of the data. So each instance point to the same 
	
	```swift
	class Car {
		var name: String
	}

	var car1 = Car(name: "Audi")
	var car2 = car1
	car2.name = "Benz"
	print(car1.name) // Benz
	print(car2.name) // Benz
	```
	Here `car2`

## Data Types

- `Int` - Integer numbers 
- `Double`, `Float` - Floating point values
- `String` - Strings
- `Bool` - Booleans
- `Character` - Single characters

Swift also provides a variety of Collection types (`Array`, `Set`, `Tuple`, `Dictionary`) to store data in different forms.

## Declaring Variables

Swift uses two keywords to declare variables, `let` and `var`

```swift
let immutableVariable = "Varibales declared with let are not mutable"
immutableVariable = "Time to try something that won't work" // Throws error

var mutableVariable = "Variables declared with var are mutable"
mutableVariable = "Okay this works" // No error
```

## Integers Types
- `Int` - Signed integer, used to store negative and non-negative integers
- `UInt` - Unsigned integer, used to store non-negative integers only

Integers can also be explicitly declared with different forms.

- #### Signed Integer

	- **Int8** - `-128` to `127`
	- **Int16** - `-32768` to `32767`
	- **Int32** - `-2147483648` to `2147483647`
	- **Int64** - `-9223372036854775808` to `9223372036854775807`

- ##### Unsigned Integer

	- **UInt8** - `0` to `255`
	- **UInt16** - `0` to `65535`
	- **UInt32** - `0` to `4294967295`
	- **UInt64** - `0` to `18446744073709551615`
	
## Type Safety

Swift is a type safe language which means a variable declared and initialized with one type cannot be reinitialized to another type.

```swift
var number: Int = 7
number = "This will not work" // error: cannot assign value of type 'String' to type 'Int'
```

## Type Inference

Swift can infer the data type to a variable automatically from the initialized value. So it doesn't always need (but supports) explicit mentioning of the type of the variable.

```swift
var a = 10
var b = "hello"
print(type(of: a)) // Int
print(type(of: b)) // String
```

## Type Aliases
Swift allows renaming the inbuilt types. This new name could be used to reference variables.

```swift
typealias char = Character
var a: char = "A"
```

[Previous](0-Swift.md) | [Next](2-StringAndChars.md)