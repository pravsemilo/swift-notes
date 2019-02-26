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
* Conditionals
	* `if`
	* `switch`
* Loops
	* `for-in`
	* `while`
	* `repeat-while`
* Parentheses around the condition or loop variable are optional.
* Braces around the body are required.
```swift
let individualScores = [75, 43, 103, 87, 21]
var teamScore = 0
for score in individualScores {
	if score > 50 {
		teamScore += 3
	} else {
		teamScore += 1
	}
}
print(teamScore)
// Prints "11"
```
* You can use `if` and `let` together to work with values that might be missing.
	* These values are represented as optionals.
	* An optional value either contains a value or contains nil to indicate a missing value.
	* Write a question mark (?) after the type of a value to mark the value as optional.
	* If the optional value is nil, the conditional is false and the code in braces is skipped.
	* Otherwise, the optional value is unwrapped and assigned to the constanct after let, which makes the value available inside the block of code.
```swift
var optionalString: String? = "Hello"
print(optionalString == nil)
// Prints false

var optionalName: String? = "John Appleseed"
var greeting = "Hello!"
if let name = optionalName {
	greeting = "Hello, \(name)"
}
```
* Another way to handle optional values is to provide a default value using `??` operator.
```swift
let nickName: String? = nil
let fullName: String = "John Appleseed"
let informalGreeting = "Hi \(nickName ?? fullName)"
```
* `switch` supports any kind of data and a wide variety of comparison operators.
	* After executing the code inside the matched switch case, the program exits from the switch statement.
	* Execution doesn't continue to the next case.
	* There is no need to explicitly break out of the switch.
```swift
let vegetable = "red pepper"
switch vegetable {
case "celery":
	print("Add some raisins and make ants on a log.")
case "cucumber", "watercress":
	print("That would make a good tea sandwich.")
case let x where x.hasSuffix("pepper"):
	print("Is it a spicy \(x)?")
default:
	print("Everything tastes good in soup.")
}
// Prints "Is it a spicy red pepper?"
```
* `let` can be used in a pattern to assign the value that matched the pattern to a constant.
* Use `for-in` to iterate over items in a dictionary by providing a pair of names to use for each key-value pair.
	* Dictionaries are unordered collections.
```swift
let interestingNumbers = [
	"Prime": [2, 3, 5, 7, 11, 13],
	"Fibonacci": [1, 1, 2, 3, 5, 8],
	"Square": [1, 4, 9, 16, 25],
]
var largest = 0
for (kind, numbers) in interestingNumbers {
	for number in numbers {
		if number > largest {
			largest = number
		}
	}
}
print(largest)
// Prints "25"
```
* Use `while` to repeat a block of code until a condition changes.
	* Condition can be at the end of loop, ensuring that the loop runs atleast once.
```swift
var n = 2
while n < 100 {
	n *= 2
}
print(n)
// Prints "128"

var m = 2
repeat {
	m *= 2
} while m < 100
print(m)
// Prints "128"
```
* You can keep an index in a loop by using "..<".
	* Use `..<` to omit the upper value.
	* Use `...` to include the upper value.
```swift
var total = 0
for i in 0..<4 {
	total += i
}
print(total)
// Prints 6
```
# Functions and Closures
* Use `func` to declare a function.
* Call a function by following its name with a list of arguments in parentheses.
* Use `->` to separate the parameter names and types from the function's return type.
```swift
func greet(person: String, day: String) -> String {
	return "Hello \(person). today is \(day)."
}
greet(person: "Bob", day: "Thursday")
```
* By default, functions use their parameter names as labels for their arguments.
	* You can write a custom argument label before the parameter name.
	* You can write underscore (_)to use not argument label.
```swift
func greet(_ person: String, on day: String) -> String {
	return "Hello \(person). today is \(day)."
}
greet("John", on: "Wednesday")
```
* Use a tuple to make a compound value - for example, to return multiple values.
	* Elements of a tuple can be referred by name or number.
```swift
func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
	var min = scores[0]
	var max = scores[0]
	var sum = 0
	for score in scores {
		if score > max {
			max = score
		} else if score < min {
			min = score
		}
		sum += score
	}
}
let statistics = calculateStatistics(scores: [5, 3, 100, 3, 9]
print(statistics.sum)
// Prints 120
print(statistics.2)
// Prints 120
```
# References
* https://docs.swift.org/swift-book/GuidedTour/GuidedTour.html
