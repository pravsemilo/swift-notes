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
* Functions can be nested.
	* Nested functions have access to variables that were declared in the outer function.
```swift
func returnFifteen() -> Int {
	var y = 10;
	func add() {
		y += 5
	}
	add()
	return y
}
```
* Functions are a first-class type.
	* This means that a function can return another function as its value.
	```swift
	func makeIncrementer() -> ((Int) -> Int) {
		func addOne(number: Int) -> Int {
			return 1+ number
		}
		return addOne
	}
	var increment = makeIncrementer()
	increment(7)
	```
	* A function can take another function as its arguments.
	```swift
	func hasAnyMatches(list: [Int], condition: (Int) -> Bool) -> Bool {
		for item in list {
			if (condition(item) {
				return true
			}
		}
		return false
	}
	func lessThanTen(number: Int) -> Bool {
		return number < 10
	}
	var numbers = [20, 19, 7, 12]
	hasAnyMatches(list: numbers, condition: lessThanTen)
	```
* Functions are a special case of closures ; blocks of code that can be called later.
	* This code in a closure has access to things like variables and functions that were available in the scope where the closure was created, even if the closure is in a different scope when it is executed.
	* You can create a closure without a name by surrounding code with braces ({}).
	* Use `in` to separate the arguments and return type from the body.
	```swift
	numbers.map({ (number: Int) -> Int int
		let result = 3 * number
		return result
	})
	```
	* When a closure's type is already known, such as the callback for a delegate, you can omit the type of its parameters, its return type or both.
	* Single statement closures implicitly return the value of their only statement.
	```swift
	let mappedNumbers = numbers.map({ number in 3 * number })
	```
	* You can refer to parameters by number instead of name.
	* A closure passed as the last argument to a function can appear immediately after the parentheses.
	* When a closure is the only argument to a function, you can omit the parentheses entirely.
	```swift
	let sortedNumbers = numbers.sorted { $0 > $1 }
	```
# Objects and Classes
* Use `class` followed by the class's name to create a class.
	* A property declaration is written the same way as a constant or a variable declaration.
	* Method and function declarations are written the same way.
	```swift
	class Shape {
		var numberOfSides = 0
		func simpleDescription() -> String {
			return "A shape with \(numberOfSides) sides."
		}
	}
	```
* Create an instance of a class by putting parentheses after the class name.
	* Use the dot syntax ot access the properties and methods of the instance.
	```swift
	var shape = Shape()
	shape.numberOfSides = 7
	var shapeDescription = shape.simpleDescription()
	```
* Use `init` to create an initializer to setup the instance.
	* `self`
	* Every property needs a value assigned - either in its declaration or in the initializer.
	```swift
	class NamedShape {
		var numberOfSides: Int = 0
		var name: String

		init(name; String) {
			self.name = name
		}

		func simpleDescription() -> String {
			return "A shape with \(numberOfSides) sides."
		}
	}
	```
* Use `deinit` to create a deinitializer if you need to perform some cleanup before the object is deallocated.
* Subclasses include their superclass named after their class name, separated by a colon.
	* Methods on a subclass that override the superclass's implementation are marked with `override`.
	* Overridding a method by accident, without `override` is detected by the compiler as an error.
	* The compiler also detects methods with `override` that don't actually override any method in superclass.
	```swift
	class Square : NamedShape {
		var sideLength: Double

		init(sideLength: Double, name: String) {
			self.sideLength = sideLength
			super.init(name: name)
			numberOfSides = 4
		}

		func area -> Double {
			return sideLength * sideLength
		}

		override func simpleDescription() -> String {
			return "A square with sides of length \(sideLength)."
		}
	}
	let test = Square(sideLenght: 5.2, name: "My test square")
	test.area()
	test.simpleDescription()
	```
* Properties can have getters and setters.
	* In the setter the new value has the implicit value `newValue`.
	* You can provide an explicit name in the parentheses after set.
```swift
class EquilateralTriangle: NamedShape {
	var sideLength: Double = 0.0

	init (sideLength: Double, name: String) {
		self.sideLength = sideLength
		super.init(name: name)
		numberOfSides = 3
	}

	var perimeter: Double {
		get {
			return 3.0 * sideLength
		}
		set {
			sideLength = newValue / 3.0
		}
	}

	override func simpleDescription() -> String {
		return "An equilaterla triangle with sides of length \(sideLength)."
	}
}

var triangle = EquilateralTriangle(sideLength: 3.1, name: "A Triangle")
print(triangle.perimeter)
// Prints 9.3
triangle.perimeter = 9.9
print(triangle.sideLength)
// Prints 3.3
```
* If you don't need to compute the property by still need to provide code that is run before and after setting a new value, use `willSet` and `didSet`.
	* The code you provide is run any time the value changes outside of an initializer.
```swift
class TriangleAndSquare {
	var triangle: EquilaternalTriangle {
		willSet {
			square.sideLength = newValue.sideLength
		}
	}
	var square: Square {
		willSet {
			triangle.sideLength = newValue.sideLength
		}
	}
	init(size: Double, name: String) {
		square = Square(sideLength: size, name: name)
		triangle = EquilateralTriangle(sideLength: size, name: name)
	}
}
var triangleAndSquare = TriangleAndSquare(size: 10, name: "Another test shape")
print(triangleAndSquare.square.sideLength)
// Prints "10.0"
print(triangleAndSquare.triangle.sideLength)
// Prints "10.0"
triangleAndSquare.square = Square(sideLength: 50, name: "Larger square")
print(triangleAndSquare.triangle.sideLength)
// Prints "50.0"
```
* When working with optional values, you can write `?` before operations like methods, properties and subscripting.
	* If the value before the `?` is nil, everything after the `?` is ignored and the value of whole expression is `nil`.
	* Otherwise the optional value is unwrapped, and everything after the `?` acts on the unwrapped value.
```swift
let optionalSquare: Square? = Square(:sideLength: 2.5, name: "Optional Square")
let sideLength = optionalSquare?.sideLength
```
# Enumerations and Structures
* Use `enum` to create an enumeration.
* Enumerations can have methods associated with them.
```swift
enum Rank: Int {
	case ace = 1
	cate two, three, four, five, six, seven, eight, nine, ten
	case jack, queeen, king

	func simpleDescription() -> String {
		switch self {
		case .ace:
			return "ace"
		case .jack
			return "jack"
		case .queen
			return "queen"
		case .king
			return "king"
		default:
			return String(self.rawValue)
		}
	}
}
let ace = Rank.ace
let aceRawValue = ace.rawValue
```
* By default, Swift assigns the raw values starting at zero and incrementing by one each time.
	* You can change this behavior by explicitly specifying values.
	* You can also use string or floating-point numbers as the raw type for an enumeration.
* Use `rawValue` to access the raw value of an enumeration case.
* Use `init?(rawValue:)` initializer to make an instance of an enumeration from a raw value.
	* It returns either the enumeration case or nil.
``swift
if let convertedRank = Rank(rawValue: 3) {
	let threeDescription = convertedRank.simpleDescription()
}
```
* The case values of an enumeration are the actual values.
	* In fact, in cases where there isn't a meaningful raw value, you don't have to provide one.
	* Notice the two ways the `hearts` case of the enumeration is referred above.
		* When assigning, a value to the `hearts` constant, the enumeration case `Suit.hearts` is referred to by its full name.
		* Inside the switch, the enumeration case is referred to by the abbreviated form `.hearts` because the value of `self` is already known to be a suit.
```swift
enum Suit {
	case spades, hearts, diamonds, clubs

	func simpleDescription() -> String {
		switch self {
		case .spades
			return "spades"
		case .hearts
			return "hearts"
		case .diamonds
			return "diamonds"
		case .clubs
			return "clubs"
		}
	}

}

let hearts = Suit.hearts
let heartsDescription = hearts.simpleDescription()
```
* If an enumeration has raw values, those values are determined as part of the declaration.
	* This means every instance of a particular enumeration case always has the same raw value.
* Another choice for enumeration cases if to have values associated with the case.
	* This values are determined when you make the instance.
	* They can be different for each instance of an enumeration case.
```swift
enum ServerResponse {
	case result(String, String)
	case failure(String)
}

let success = ServerResponse.result("6:00 am", "8:09 pm")
let failure = ServerResponse.failure("Out of cheese.")

switch success {
	case let .result(sunrise, sunset):
		print("Sunrise is at \(sunrise) and sunset is at \(sunset).")
	case let.failre(message)
		print("Failure ... \(message))
}
```
* Use `struct` to create a structure.
	* Structures support many of the same behaviors as classes, including methods and initializers.
	* Structures are always copied when they are passed around, but classes are passed by reference.
```swift
struct Card {
	var rank: Rank
	var suit: Suit

	func simpleDescription() -> String {
		return "The \(rank.simpleDescription()) of \(suit.simpleDescription())"
let threeOfSpades = Card(rank: .three, suit: .spades)
let threeOfSpadesDescription = threeOfSpades.simpleDescription()
```
# References
* https://docs.swift.org/swift-book/GuidedTour/GuidedTour.html
