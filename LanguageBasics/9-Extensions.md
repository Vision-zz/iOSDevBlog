# Extensions

Extensions add new functionality to an existing class, structure, enumeration, or protocol type. This includes the ability to extend types for which you don’t have access to the original source code (known as retroactive modeling). Extensions can be declared by the `extensions` keyword

```swift
extension TypeName {
	// Extension definition
}
```

## Initializers

Extensions can add new initializers to the existing type. Extensions cannot add new designated initializers or deinitializers

```swift
struct Size {
    var width = 0.0, height = 0.0
}
struct Point {
    var x = 0.0, y = 0.0
}
struct Rect {
    var origin = Point()
    var size = Size()
}
extension Rect {
    init(center: Point, size: Size) {
        let originX = center.x - (size.width / 2)
        let originY = center.y - (size.height / 2)
        self.init(origin: Point(x: originX, y: originY), size: size)
    }
}
let centerRect = Rect(center: Point(x: 4.0, y: 4.0), size: Size(width: 3.0, height: 3.0))
```

## Methods

Extensions can add new functions / methods to existing types to extend it's functionality

```swift
extension String {
    func echo(times count: Int) -> String {
        return String(repeating: self, count: count)
    }
}

print("Hello\n".echo(times: 5))
```

**Output**

```
Hello
Hello
Hello
Hello
Hello
```

## Subscripts

Extensions can add new subscripts to and existing type

```swift
extension String {
    subscript(_ index: Int) -> String {
        return String(self[self.index(startIndex, offsetBy: index)])
    }

    subscript(_ range: ClosedRange<Int>) -> String {
        return String(self[self.index(startIndex, offsetBy: range.lowerBound)...self.index(startIndex, offsetBy: range.upperBound)])
    }
}

print("Hello"[1]) // e
print("Hello"[0...2]) // Hel
```