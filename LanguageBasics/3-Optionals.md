# Optionals

Optionals are used when a value may or may not be present. A optional varibale can either contain a value or `nil`. `nil` is used with optional variables to denote that the variable is valueless. `nil` is not a pointer like in other langaugaes and can only be assigned to optional variables.

## Declaring a Optional variable

Optional variables are declared by using the `?` operator after the type annotation

```swift
var variable: String?
print(variable) // 'nil'
```

By default, values of the optional variables that are not initalized are set to `nil`

## Unwrapping optional values

Optional values cannot be used directly as Swift does not know for sure if the variable actually contains a value or not. So unwrapping a optional vairable is needed to use it successfully.

- Using `If-else`

	```swift
	var errorCode: Int? = 404
	if errorCode != nil {
		print("Error \(errorCode)")
	}
	```
	**Output**
	```
	Error 404
	```

- Using `Forced Unwrapping`

	Swift also allows forced unwrapping to skip the checks for nil and tell the compiler that the value is not nil. But it is adviced to use this only if we are sure that the optional variable is not nil and will always contain a value. To force unwrap a optinal variable we use the force unwrapping operator `!` after the variable name.

	```swift
	var number: Int? = 10
	print(number!) // 10
	```

	However if the variable contains a nil value and is force unwrapped, it throws an error.

	```swift
	var number: Int? = nil
	print(number!) // 'Fatal error: Unexpectedly found nil while unwrapping an Optional value'
	```

- Using `If-let`
  
	```swift
	var option: String? = "Yes"
	if let option = option {
		print("The option is \(option)")
	}
	```
	- **Output**
	```
	The option is Yes
	```
	
	However the unwrapped variable can only be used inside the if block scope. To use it outside the scope we must use `guard-let`

- Using `guard-let`

	```swift
	func printWorldWith(string: String?) {
    	guard var string = string else {
        	return print("World")
    	}
    	print(string, "World")
	}

	printWorldWith(string: "Hello")
	printWorldWith(string: nil)
	```
	- **Output**
	```
	Hello World
	World
	```

[Previous](2-StringAndChars.md)