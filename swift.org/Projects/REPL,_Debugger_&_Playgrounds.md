* Swift.org community makes use of LLDB debugger to provide a REPL and debugging environment.
* Swift is tightly coupled to the version of Swift compiler embedded in the debugger.
	* Tight integration of compiler and debugger enables accurate inspectio of Swift types.
	* Also enables full-featured expression evaluation in the context of a rapidly evolving language.
* Developers must use a matched pair of compiler and debugger built using the same sources.
# Why Combine the REPL and Debugger?
* __Integrated debugging__
	* REPL is also a full featured debugger.
* __Recovering from failure__
	* REPL supports investigating failures with the full debugger or unwinding for immediate recovery.
* __Robust expression evaluation__
* __Consistent result formatting__
	* Strategy used for textually representing values in the REPL is shared by the debugger.
# Xcode Playground Support
* Prior to Swift 3.0 and Xcode 8, playgroud used the version of Swift included in Xcode.
* Xcode Playgournd Support enables building a Swift toolchain that includes everything necessary to integrate with Xcode 8 playground.
* The projects builds two frameworks :
	* __PlaygroundSupport__
		* Defines API that may be explicitly referred to by playground code to communicate with Xcode.
	* __PlaygroundLogger__
		* Used implicitly to record values of interest on a line-by-line basis and communicate them to Xcode.
		* Calls are automatically injected to playground code so that no explicit reference is required.
# References
* https://swift.org/lldb/
