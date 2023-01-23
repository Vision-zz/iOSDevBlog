# Generics

Generic code enables you to write flexible, reusable functions and types that can work with any type, subject to requirements that you define. You can write code that avoids duplication and expresses its intent in a clear, abstracted manner.

## Problem that Generics solve

Let's consider that we need a swap function that swaps the value of two variables.

```swift
// Swapping two Integers
func swapInteger(_ a: inout Int, _ b: inout Int) {
	let temp = a
	a = b
	b = temp
}
```

With the above function we can swap two variables of type `Int`. Now if we need to swap two strings, we might need another function like below

```swift
func swapString(_ a: inout String, _ b: inout String) {
	let temp  = a
	a = b
	b = temp
}
```

Notice both the function body are pretty much the same, yet we had to define two different functions since the function parameter type was different. By using Generics we can solve this problem.

```swift
func swapTwoValues<T>(_ a: inout T, _ b: inout T) {
	let temp = a
	a = b
	b = temp
}
```

This above `swapTwoValues(_:_:)` function can now be used for any variable types.The generic version of the function uses a placeholder type name (called T, in this case) instead of an actual type name (such as Int, String, or Double). The placeholder type name doesn’t say anything about what `T` must be, but it does say that both a and b must be of the same type `T`, whatever `T` represents. The actual type to use in place of `T` is determined each time the `swapTwoValues(_:_:)` function is called.

## Type Parameters

In the `swapTwoValues(_:_:)` example above, the placeholder type T is an example of a type parameter. Type parameters specify and name a placeholder type, and are written immediately after the function’s name, between a pair of matching angle brackets (such as `<T>`).

Once you specify a type parameter, you can use it to define the type of a function’s parameters (such as the a and b parameters of the `swapTwoValues(_:_:)` function), or as the function’s return type, or as a type annotation within the body of the function. In each case, the type parameter is replaced with an actual type whenever the function is called. (In the `swapTwoValues(_:_:)` example above, T was replaced with Int the first time the function was called, and was replaced with String the second time it was called.)

You can provide more than one type parameter by writing multiple type parameter names within the angle brackets, separated by commas.

## Naming Type Parameters

In most cases, type parameters have descriptive names, such as `Key` and `Value` in `Dictionary<Key, Value>` and Element in `Array<Element>`, which tells the reader about the relationship between the type parameter and the generic type or function it’s used in. However, when there isn’t a meaningful relationship between them, it’s traditional to name them using single letters such as `T`, `U`, and `V`, such as `T` in the `swapTwoValues(_:_:)` function above.

## Generic Types

In addition to generic functions, Swift enables you to define your own generic types. These are custom classes, structures, and enumerations that can work with any type, in a similar way to Array and Dictionary.

Writing a non-generic version of a queue

```swift
struct Queue {
    private var items: [Int] = []
    mutating func enqueue(_ element: Int) {
        items.append(element)
    }
    mutating func dequeue() -> Int? {
        return items.isEmpty ? nil : items.removeFirst()
    }
}
```

The above `Queue` can only be used for Integer values. But we need to design a Queue so that it could be used with any value of any type, and to overcome this problem we can use Generics.

Writing a generic versin of a queue

```swift
struct Queue<T> {
    private var items: [T] = []
    mutating func enqueue(_ element: T) {
        items.append(element)
    }    
    mutating func dequeue() -> T? {
        return items.isEmpty ? nil : items.removeFirst()
    }
}
```

Now Queue can be initialized by giving it a working type and that particular queue instance would be used for that specified type

```swift
var stringQueue = Queue<String>()
stringQueue.enqueue("Hello")
stringQueue.enqueue("World")
stringQueue.dequeue() // returns "Hello"

var intQueue = Queue<Int>()
intQueue.enqueue(1)
intQueue.enqueue(5)
intQueue.enqueue(7)
intQueue.enqueue(10)
intQueue.dequeu() // returns '1'
```

## Extending a Generic Type

When you extend a generic type, you don’t provide a type parameter list as part of the extension’s definition. Instead, the type parameter list from the original type definition is available within the body of the extension, and the original type parameter names are used to refer to the type parameters from the original definition. The following Example adds extensions to the `Stack<Element>` type from the above example:

```swift
extension Queue {
    var isEmpty: Bool {
        items.isEmpty
    }
    mutating func clearQueue() {
        items.removeAll()
    }
	func peek() -> T? {
    	items.isEmpty ? nil : items.first
    }
}
```

The above example extends the generic `Queue` type to add some functions to it. The peek function returns the first element of type `T`

```swift
intQueue.peek() // returns '5'
intQueue.isEmpty // false
intQueue.clearQueue()
intQueue.isEmpty // true
```

## Type Constrain

You write type constraints by placing a single class or protocol constraint after a type parameter’s name, separated by a colon, as part of the type parameter list. The basic syntax for type constraints on a generic function is shown below (although the syntax is the same for generic types)

```swift
func findIndex<T: Equatable>(of valueToFind: T, in array:[T]) -> Int? {
    for (index, value) in array.enumerated() {
        if value == valueToFind {
            return index
        }
    }
    return nil
}
```

We can notice that we are constraining the type of T to conform to the `Equatable` protocol, this is because not all types of `T` can be compared with the equal to (`==`) operator
