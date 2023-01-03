# Functions
Function is a block of code that can perform certain tasks. We can write functions for codes that otherwise will be rewritted and could become redundant. Functions in Swift has a type, consisting of the function's `parameter type` and the `return type`. Function parameters and return types are optional

**Syntax**
```swift
func functionName(parameterName: ParameterType) -> ReturnType {
	statements
}
```

## Argument labels
A function can have argument labels for it's parameter names. These argument labels are used while calling the function and paramenter names are used inside the function code block. If no argument labels are present, then the parameter name is used

```swift
func test(with string: String) {
	print("testing with \(string)")
}
test(with: "Hello") // testing with hello
```

Argument labels can be omitted while calling a function by writing a underscore (`_`) instead of the argument label

```swift
func test(_ string: String) {
	print("testing with \(string)")
}
test("Hello") // testing with hello
```

## Default parameter values
Parameters of a function can have default value which will be considered if a value for that parameter is not provided during calling the function.

```swift
func sum(a: Int, b: Int = 10) {
	print(a + b)
}
sum(a: 5, b: 5) // 10
sum(a: 5) // 15
```

## Variadic Parameters
Variadic parameters allows passing more than one value of the same type as the parameters. It can be declared by appending three dots next to the parameter type. This parameter is accessed as an array inside the function block.

```swift
func add(_ numbers: Int...) -> Int {
	numbers.reduce(0, { a, b in a + b})
}
print(add(1, 2, 3, 4, 5)) // 15
```

## In-Out Parameters
Swift does not allow mutation to function parameters. To mutate a parameter of a function the `inout` keyword is to be used. And the caller should insert the ampersand `&` symbol before the parameter to denote that it is a `inout` parameter

```swift
func swapTwoInts(_ x: Int, _ y: Int) {
	(x, y) = (y, x)
}
var a = 5, b = 10
swapTwoInts(&a, &b)
print(a, b) // 10 5
```