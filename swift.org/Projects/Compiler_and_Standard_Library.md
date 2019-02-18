* Main Swift repository contains code for
	* Swift compiler
	* Standard library
	* SourceKit (for IDE integration)
	* Swift regression test suite
	* Implementation level documentation
# Compiler Architecture
* Compiler is responsible for translating Swift source code into efficient and executable machine code.
* Swift compiler front-end also supports a number of tools, including IDE integration with syntax-coloring, code completion and other conveniences.
* Major Components :
	* __Parsing :__
		* Simple, recursive-descent parser implemented in [lib/Pare](https://github.com/apple/swift/tree/master/lib/Parse) with an integrated, hand-coded lexer.
		* Responsible for generating an Abstract Syntax Tree (AST) without any semantic or type information.
		* Responsible for emitting warnings or errors for grammatical problems with input source.
	* __Semantic analysis :__
		* Implemented in [lib/Sema](https://github.com/apple/swift/tree/master/lib/Sema).
		* Responsible for taking the parsed AST and transforming into a well-formed, fully-type-checked form for the AST.
		* Responsbile for emitting warnings or error for semantic problems in the source code.
		* Semantic analysis includes type inference and on success, indicates that it is safe to generate code from the resulting, type-checked AST.
	* __Clang importer :__
		* Implemented in [lib/ClangImporter](https://github.com/apple/swift/tree/master/lib/ClangImporter).
		* Imports Clang modules and maps the C or Objective-C APIs they export into their corresponding Swift APIs.
		* The resulting imported ASTs can be referred to by semantic analysis.
	* __SIL generation :__
		* Swift Intermediate Language (SIL).
		* High level, Swift-specific intermediate language suitable for further analysis and optimization of Swift code.
		* Implemented in [lib/SILGen](https://github.com/apple/swift/tree/master/lib/SILGen).
		* SIL generation phase lowers the type-checked AST into so-called "raw" SIL.
		* Design of SIL is described in [docs/SIL.rst](https://github.com/apple/swift/blob/master/docs/SIL.rst).
	* __SIL guaranteed transformation :__
		* Implemented in [lib/SILOptimizer/Mandator](https://github.com/apple/swift/tree/master/lib/SILOptimizer/Mandatory).
		* Perform additional dataflow diagnostics that affect the correctness of a program (such as use of uninitialized variables).
		* End result of these transformations is "canonical" SIL.
	* __SIL Optimizations :__
		* Implemented in [lib/Analysis](https://github.com/apple/swift/tree/master/lib/SILOptimizer/Analysis), [lib/ARC](https://github.com/apple/swift/tree/master/lib/SILOptimizer/ARC), [lib/LoopTransforms](https://github.com/apple/swift/tree/master/lib/SILOptimizer/LoopTransforms) and [lib/Transforms](https://github.com/apple/swift/tree/master/lib/SILOptimizer/Transforms).
		* Perform additional high-level, Swift-specific optimizations to the program, including (for example) Automatic Reference Counting optimizations, devirtualization and generic specialization.
	* __LLVM IR Generation :__
		* Implemented in [lib/IRGen](https://github.com/apple/swift/tree/master/lib/IRGen).
		* Lowers SIL to LLVM IR, at which point LLVM can continue to optimize it and generate the machine code.
# Standard Library Design
* Swift standard library encompasses a number of data types, protocols and fuctions, including fundamental data types, collections along with protocols that describe them and algorithms that operate on them, characters and strings and low-level primitives (E.g., `UnsafeMutablePointer`).
* Implementation of the standard library resides in the `stdlib/public` subdirectory within the [Swift repository](https://github.com/apple/swift) which is futher subdivided into : 
	* __Standard library core :__
		* Implemented in [stdlib/public/core](https://github.com/apple/swift/tree/master/stdlib/public/core), including definitions of all of the data types, protocols, functions etc.
	* __Runtime__
		* Implemented in [stdlib/public/runtime](https://github.com/apple/swift/tree/master/stdlib/public/runtime).
		* Layered between the compiler and the core standard library.
		* Responsible for implementing many of the dynamic features of the language such as casting, type metadata (to support generics and reflection), and memory management.
		* Written mostly in C++ or Objetive-C.
	* __SDK Overlays :__
		* Implemented in [stdlib/public/SDK](https://github.com/apple/swift/tree/master/stdlib/public/SDK).
		* Specific to Apple platforms.
		* Provide Swift-specific additions and modifications to existing Objective-C frameworks to improve their mapping into Swift.
		* In particular, the `Foundation` overlay provides additional support for interoperability with Objective-C code.
* Swift standard library is written in Swift.
* It is a bit different from normal Swift code because it is the lowest-level Swift code in the stack - responsible for implementing the core data types on which other Swift code is built.
* Some differences include :
	* __Access to compiler builtins :__
		* The `Builtin` module is only generally accessible to the standard library.
		* Provides compiler builtin functions (E.g., to directly create SIL instructions) and data types (E.g., "raw" pointers, primitive LLVM integer types) needed to implement the data types that are fundamental to programming in Swift.
	* __Visibility is often managed by convention :__
		* Standard library declarations need to have greater visibility than one would generally like, due to the way in which the standard library is compiled and optimized.
			* For example, `private` modifiers are never used.
		* It is common to need to make something `public` even when it is not intended as part of the public interface.
			* In such cases, one should use a leading underscore to indicate that the public API is meant to be private.
		* The policy for access control in the stadard library is documented in [docs/AccessControlInStdlib.rst](https://github.com/apple/swift/blob/master/docs/AccessControlInStdlib.rst).
	* __Repetitive code uses gyb :__
		* `gyb` is a simple tool for generating repetitive code from a template.
		* Used to create the definitions of various sized integer types (`Int8`, `Int16`, `Int32`, `Int64` etc.) from a single source.
	* __Testing is tightly coupled with the compiler :__
		* Standard library and compiler evolve together.
		* Changes in core data types can require compiler-side changes and vice versa.
		* Hence standard library test suite is stored within the same directory structure as the compiler, in [test/stdlib](https://github.com/apple/swift/tree/master/test/stdlib) and [validation-test/stdlib](https://github.com/apple/swift/tree/master/validation-test/stdlib).
# References
* https://swift.org/compiler-stdlib/
