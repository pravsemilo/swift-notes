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
# References
* https://swift.org/getting-started/
