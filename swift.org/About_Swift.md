* General purpose programming language built using a modern approach to safety, performance and software design patterns.
* Can be used for system programming, mobile and desktop apps and scaling up to cloud services.
* Designed to make writing and maintaining correct programs easier for the developer.
	* Most obvious way to write Swift code must also be :
		* __Safe__
			* Most obvious way to write code should behave in a safe manner.
			* Undefined behavior is enemy of safety.
			* Opting for saftey means Swift will feel strict.
				* Clarity saves time in the long run.
		* __Fast__
			* Intended as a replacement for C-based languages.
			* Performance should be predictable and consistent.
		* __Expressive__
			* Swift benefits from advancements in computer science to offer a syntax that is joy to use.
* Tools are a critical part of the Swift ecosystem.
	* Swift-based playground in Xcode.
	* Web-based REPL when working with Linux server-side code.
# Features
* Make code easier to read and write.
* Give the control needed in a true systems programming language.
* Supports inferred types to make code cleaner and less prone to mistakes.
* Modules eliminates headers and provide namespaces.
* Memory is managed automatically.
* No semicolon required.
* Named parameters brought forward from Objective-C are expressed in a clean syntax that makes APIs in Swift easy to read and maintain.
* Closures unified with function pointers.
* Tuples with multiple return values.
* Generics.
* Fast and concise iteration over a range or collection.
* Structs that support methods, extensions and protocols.
* Functional programming patterns like map, filter etc.
* Powerful error handling built-in.
* Advanced control flow with `do`, `guard`, `defer` and `repeat` keywords.
## Safety
* Safer than C-based languages.
* Variables are always initialized before use.
* Arrays and integers are checked for overflows.
* Syntax is tuned to make is easy to define your intent. For example, variables (`var`) vs constant (`let`).
* Swift objects cannot be `nil`.
* Trying to use a `nil` object will result in compile time error.
* `Optional` - In case where `nil` is appropriate.
	* Swift syntax forces you to safely deal with it using `?` to indicate to compiler that you understand the behavior and will handle it safely.
# Swift.org and Open Source
* On December 3, 2015, Swift language, supporting libraries, debugged and package manager were published under Apache 2.0 license with a Runtime Library Exception.
## Projects
* [Swift Compiler](https://swift.org/compiler-stdlib/) - Command line tool.
* [Standard Library](https://swift.org/compiler-stdlib/) - Bundled as part of language.
* [Core Libraries](https://swift.org/core-libraries/) - Provides higher level functionality.
* [LLDB Debugger](https://swift.org/lldb/) - Includes the Swift REPL.
* [Swift Package Manager](https://swift.org/package-manager/) - For distributing and building Swift source code.
* [XCode Playground Support](https://swift.org/lldb/#xcode-playground-support) - Enable playgrounds in XCode.
# Platform Support
* Swift is now free to be ported across a wide range of platforms, devices and use cases.
* Provide source compatibility for Swift across all platforms, even though the actual implementation may differ across platforms.
	* Apple platforms include the Objective-C runtime to access Apple platform frameworks like UIKit, AppKit etc.
	* On other platforms, Objective-C runtime is not present.
* Swift core libraries project aims to provide portable implementations of fundamental Apple frameworks (such as Foundation) without dependencies on the Objective-C runtime.
# References
* https://swift.org/about/
