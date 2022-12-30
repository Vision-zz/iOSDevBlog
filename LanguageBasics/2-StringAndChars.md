# Strings and Characters

A string is just a bunch of characters grouped together such as `"Hello"`, it can be initialized with either String literals or the String constructor.

By default the type of a variable is `String` even if it contains a single character. A variable must be declared with either explicit type annotation with `Character` type or should be initialized with the `Character` constructor to declare the variable's type as `Character`

```swift
var a = "A" // Type 'String'
var b = String("B") // Type 'String'
var c: Character = "C" // Type 'Character'
var d = Character("D") // Type 'Character'
```

## Accessing specific character of a String
Swift's strings cannot be indexed by using integer values. Swift strings can contain unicode characters and it also combines unicode characters together. So some characters may require different memory space than others. 

Swift provides a associated index type with each `String` value which stores the position of each `Character` in the string. To access a particular `Character` of a string, Swift offers `index()` methods which can be used with subscript syntax.

```swift
let string = "Hello world!"
string[string.startIndex] // "H"
string[string.index(after: string.startIndex)] // "e"
string[string.index(before: string.endIndex)] // "d"
string[string.index(string.startIndex, offsetBy: 6)] // "w"
```

## String Interpolation
Swift provides a modern syntax for including variables, expressions inside a string literal. And this is compatible in both single and double line strings. The item that is added to the string is surrounded by paranthesis and is prefixed by a backslash

```swift
let count = 10
print("The count is \(count)") // "The count is 10"
```

[Previous](1-TheBasics.md) | [Next](3-Optionals.md)