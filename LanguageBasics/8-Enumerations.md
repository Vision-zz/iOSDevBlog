# Enumerations

An enumeration defines a common type for a group of related values and enables you to work with those values in a type-safe way within your code.

```swift
enum EnumerationName {
	// Enum definition
}
```

**Example**

```swift
enum CompassPoints {
	case north
	case south
	case east
	case west
}
```

Multiple enum classes can be written on the same line

```swift
enum CompassPoint {
	case north, south, east, west
}
```

## Matching enum with switch case

We can match individual enumeration values with a switch statement

```swift
var directionToHead = CompassPoint.south
switch directionToHead {
	case .north:
	    print("Lots of planets have a north")
	case .south:
	    print("Watch out for penguins")
	case .east:
	    print("Where the sun rises")
	case .west:
    	print("Where the skies are blue")
}
// Prints "Watch out for penguins"
```

## Iterating a Enum

We can iterate over a enumeration by conforming to the `CaseIterable` protocol. Swift exposes a collection of all the cases as an allCases property of the enumeration type.

```swift
enum CompassPoint: CaseIterable {
	case north, south, east, west
}

for direction in CompassPoint {
	print(direction)
}

print("There are \(CompassPoint.allCases.count) directions in total")
```

**Output**

```
north
south
east
west
There are 4 directions in total
```

## Raw values

Enumeration cases can come prepopulated with default values (called raw values), which are all of the same type.

```swift 
enum ASCIIControlCharacter: Character {
    case tab = "\t"
    case lineFeed = "\n"
    case carriageReturn = "\r"
}
```

Raw values can be strings, characters, or any of the integer or floating-point number types. Each raw value must be unique within its enumeration declaration.

Raw values can be automatically assigned if the enum's raw value stores integers or strings. We don't have to explicitly store raw values for each enum case. 

```swift
enum CompassPoint {
	case north = 1, south, east, west
}
```

Here the direction `north` has an explicit raw value of 1 and following that `south` has a raw value of 2 and so on.

```swift
print(CompassPoint.north.rawValue) // 1
print(CompassPoint.east.rawValue) // 3
```

## Associated Values

Associated values are values of other types that are stored along the case values of a enumeration. 

```swift
enum Barcode {
	case upc(Int, Int, Int, Int)
	case qrCode(String)
}

var productBarcode = Barcode.upc(8, 85909, 51226, 3)

switch productBarcode {
	case .upc(let numberSystem, let manufacturer, let product, let check):
	    print("UPC: \(numberSystem), \(manufacturer), \(product), \(check).")
	case .qrCode(let productCode):
	    print("QR code: \(productCode).")
}
// Prints "UPC: 8, 85909, 51226, 3."
```

If all of the associated values for an enumeration case are extracted as constants, or if all are extracted as variables, you can place a single var or let annotation before the case name, for brevity

```swift
switch productBarcode {
	case let .upc(numberSystem, manufacturer, product, check):
	    print("UPC : \(numberSystem), \(manufacturer), \(product), \(check).")
	case let .qrCode(productCode):
	    print("QR code: \(productCode).")
}
// Prints "UPC: 8, 85909, 51226, 3."
```
