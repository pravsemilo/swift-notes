# Installing Swift
## On macOS
* To make the latest installed toolchain available.
```bash
$ export TOOLCHAINS=swift
```
* To select a different installed toolchain, use its identifier in the `TOOLCHAINS` variable.
```bash
$ /usr/libexec/PlistBuddy -c "Print CFBundleIdentifier:" /Library/Developer/Toolchains/swift-4.0-RELEASE.xctoolchain/Info.plist
org.swift.4020170919

$ export TOOLCHAINS=org.swift.4020170919
```
## On Linux
* Install clang.
```bash
$ sudo apt-get install clang
```
* Add Swift to your `PATH`.
# Using the REPL
* If your run the `swift` command without any arguments, you'll launch the REPL.
* You can also import any available system modules :
	* On macOs
	```swift
	1> import Darwin
	2> arc4random_uniform(10)
	$R0: UInt32 = 4
	```
	* On Linux
	```swift
	1> import Glibc
	2> random() % 10
	$R0: Int32 = 4
	```
# Using the Package Manager
* Provides a convention based system for building libraries and executables, and sharing code across different packages.
* Commands
	* `swift package`
	* `swift run`
	* `swift build`
	* `swift test`
## Creating a Package
* Every package must have a manifest file called `Package.swift` in its root directory.
* You can create a package named `Hello` using :
```bash
$ mkdir Hello
$ cd Hello
$ swift package init
```
* By default this will create a library package directory structure.
```
|-- Package.swift
|-- README.md
|-- Sources
|   |-- Hello
|      |-- Hello.swift
|-- Tests
    |-- HelloTests
    |   |--HelloTests.swift
    |-- LinuxMain.swift
```
* You can use `swift build` to build a package.
	* This will download, resolve and compile dependencies mentioned in the manifest file `Package.swift`.
* To run thes tests for a package, use `swift test`.
## Building an Executable
* A target is considered as an executable if it contains a file named `main.swift`.
* The package manager will comiple that file into a binary executable.
```bash
$ mkdir Hello
$ cd Hello
$ swift package init --type executable	# Run the swift package's init command with executable type.
$ swift run Hello			# Build and run the executable.
```
* If there is only one executable in a package, we can omit its name in `swift run` command.
* You can also compile the package using `swift build` command and then run binary from build directory.
```bash
$ swift build
$ .build/x86_64-apple-macosx10.10/debug/Hello
```
## Working with Multiple Source Files
* Create a new file in `Sources/Hello` directory called `Greeter.swift`.
* Enter the following code.
```swift
func sayHello(name: String) {
	print("Hello, \(name)!")
}
```
* Edit `main.swift` and enter the following content.
```swift
if CommandLine.arguments.count != 2 {
	print("Usage: hello NAME")
} else {
	let name = CommandLine.arguments[1]
	sayHello(name: name)
}
```
* Run `swift run`.
```bash
$ swift run Hello whoami
```
# Using the LLDB Debugger
* You can use the LLDB debugger to run Swift programs step-by-step, set breakpoints, and inspect and modify program state.
* As an example consider the following Swift code.
```swift
func factorial(n: Inst) -> Int {
	if n <= 1 { return n }
	return n * factorial(n: n - 1)
}

let number = 4
print("\(number)! is equal to \(factorial(n: number))")
```
* Create a file name Factorial.swift with the code above.
* Run `swiftc` command passing the file name along with `-g` option to generate debug information.
```bash
$ swift -g Factorial.swift
$ ls
Factorial.dSYM
Factorial.swift
Factorial*
```
* Run it through LLDB debugger.
```bash
$ lldb Factorial
```
* Set a breakpoint on line 2 of the `factorial(n:)` function with the `breakpoint set(b)` command.
```
(lldb) b 2
```
* Run the process with `run (r)` command.
```
(lldb) r
```
* Use the `print (p)` command to inspect the value of `n` parameter.
```
(lldb) p n
(Int) $R0 = 4
```
* `print` command can evaluate Swift expressions as well.
```
(lldb) p n * n
(Int) $R1 = 16
```
* Use the `backtrace (bt)` command to show the frames.
```
(lldb) bt
```
* Use the `continue (c)` command to resume.
```
(lldb) c
```
* Use the `print (p)` command again to inspect the value of `n` parameter.
```
(lldb) p n
(Int) $R2 = 3
```
* Use the `breakpoint disable (br di)` command to disable all breakpoints and `continue (c)` to resume the process.
```
(lldb) br di
(lldb) c
```
# References
* https://swift.org/getting-started/
* [LLDB Tutorial](http://lldb.llvm.org/tutorial.html)
