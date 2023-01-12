# Structs

Structure is a entity in Swift that is used to store values of different types. Structures are created using the `struct` keyword. Variables of the `struct` are called as `properties` and Functions are called `methods`

**Syntax**

```swift
struct StructureName {
	// structure definition
}
```

**Example**

```swift
struct Student {
	var name: String
	var rollNo: Int
}
```

## Computed Properties
Variables inside structs can be set / returned after a computation process instead of returning them directly. The `get` and `set` keywords are used to denote the Getter and Setter of the variable.

```swift
struct Student {
    private var _name: String!
    var name: String {
        get {
            _name
        }
        set {
            _name = newValue.split(separator: " ")
				.map({ $0[$0.startIndex].uppercased() + $0.dropFirst() })
				.joined(separator: " ")
        }
    }

 	init(studentName: String) {
        name = studentName
    }

}

var s =  Student(studentName: "firstname lastname")
print(s.name) // Firstname Lastname
```

## Property Observers

Swift provides two property observers `willSet` and `didSet`to track the process of mutation of variables. `willSet` is called before setting the value of a variable and `didSet` is called after setting the value of the variable

```swift
struct Database {
    var key: String {
        willSet {
            print("Setting new database key")
        }
        didSet {
            print("Database key set successfully")
        }
    }
}

var dataBase = Database(key: "1234567890")
dataBase.key = "ABCD1234"
print(dataBase.key)
```

**Output**

```
Setting new database key
Database key set successfully
ABCD1234
```

## Mutating methods

Methods that mutate / change the values of a variable inside the struct should be explicitly mentioned as mutating method, this is done by adding the `mutating` keyword before declaring a function

```swift
struct Student {
    private var name: String
    init(name: String) {
        self.name = name
    }
    mutating func setName(name: String) {
        self.name = name
    }
    func getName() -> String {
        name
    }
}

var s = Student(name: "Firstname Lastname")
s.setName(name: "NewName")
print(s.getName()) // NewName
```
 