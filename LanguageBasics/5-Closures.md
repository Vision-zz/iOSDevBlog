# Closures

Closures are a block of code similar to functions that can be passed around and used. It is similar to `Lambda functions` in Java or `Arrow Functions` in JavaScript.

**Syntax**

```swift
{ (parameters) -> returnType in
	statements
}
```

The `in` keyword is used to seperate statements from parameters

**Example**

```swift
var arr = [10, 5, 19, 4, 27, 9, 33, 12]
var sortedArr = arr.sorted(by: { a, b in a < b })
print(sortedArr) // [4, 5, 9, 10, 12, 19, 27, 33]
```

## Shorthand Arguments

Swift provides short hand arguments to use with closures by the names `$0`, `$1` ... `$n-1` where `n` is the number of arguments. Using this syntax, the `in` keyword in the synta can be avoided.

```swift
var arr = [10, 5, 19, 4, 27, 9, 33, 12]
var sortedArr = arr.sorted(by: { $0 < $1 })
print(sortedArr) // [4, 5, 9, 10, 12, 19, 27, 33]
```

## Trailing Closures

Swift allows us to write closure espressions after the function call's paranthesis.

```swift
var arr = [10, 5, 19, 4, 27, 9, 33, 12]
var sortedArr = arr.sorted() { $0 < $1 }
print(sortedArr) // [4, 5, 9, 10, 12, 19, 27, 33]
```