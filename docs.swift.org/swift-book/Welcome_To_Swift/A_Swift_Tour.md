* Hello World
	* Don't need to import a separate library for I/O or string handling.
	* Code written at global scope is used as the entry point.
		* So you don't need a `main()` function.
	* Don't need to write semicolons at the end of every statement.
```swift
print("Hello, world!")
// Prints "Hello, world!"
```
# Simple Values
* `let`
	* Use to create constant.
	* Value of constant doesn't need to be known at compile time.
	* Assign value only once.
* `var`
	* Use to create variable.
```swift
var myVariable = 42
myvariable = 50
let myConstant = 42
```
* A constant or variable must have the same type as the value.
	* You don't have to write the type explicitly.
	* Type can be inferred by the compiler when value is provided.
	* If initial value is not provided or doesn't provide enough information, specify the type by writing it after the variable, separated by a colon.
```swift
let implicitInteger = 70
let implicitDouble = 70.0
let explicitDouble: Double = 70
```
* Values are never implicitly converted to another type.
	* If you need to convert a value to a different type, explicitly make an instance of the desired type,
```swift
let label = "The width is "
let width = 94
let widthLabel = label + String(width)
```
* You can include dynamic values in a string.
	* Write the value in parentheses and write a backslash (\) before the parentheses.
```swift
let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."
```
* Use three double quotation marks (""") for multi-line strings.
	* Indentation at the start of each line is removed as long as it matches the indentations of the closing quotation mark.
* Create arrays and dictionaries using brackets ([]).
	* Access their elements by writing the index or key in brackets.
	```swift
	var shoppingList = ["catfish", "water", "tulips"]
	shoppingList[1] = "bottle of water"
	```
	* A comma is allowed after the last element.
	```swift
	var occupations = [
		"Malcolm" : "Captain",
		"Kaylee" : "Mechanic",
	]
	```
	* Arrays automatically grow as you add elements.
	```swift
	shoppingList.append("blue paint")
	print(shoppingList)
	```
	* To create an empty array or dictionary, use the initializer syntax.
	```swift
	let emptyArray = [String]()
	let emptyDictionary = [String: Float]()
	```
	* If type information can be inferred, you can write an empty array as [] and an empty dictionary as [:], for example when you set a new value for a variable or pass an argument to a function.
	```swift
	let anotherEmptyArray = []
	let anotherEmptyDictionary = [:]
	```
# Control Flow
# References
* https://docs.swift.org/swift-book/GuidedTour/GuidedTour.html
