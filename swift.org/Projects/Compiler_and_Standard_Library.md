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
	* _Parsing : _
		* Simple, recursive-descent parser implemented in [lib/Pare](https://github.com/apple/swift/tree/master/lib/Parse) with an integrated, hand-coded lexer.
		* Responsible for generating an Abstract Syntax Tree (AST) without any semantic or type information.
		* Responsible for emitting warnings or errors for grammatical problems with input source.
	* _Semantic analysis : _
		* Implemented in [lib/Sema](https://github.com/apple/swift/tree/master/lib/Sema).
		* Responsible for taking the parsed AST and transforming into a well-formed, fully-type-checked form for the AST.
		* Responsbile for emitting warnings or error for semantic problems in the source code.
		* Semantic analysis includes type inference and on success, indicates that it is safe to generate code from the resulting, type-checked AST.
	* _Clang importer : _
		* Implemented in [lib/ClangImporter](https://github.com/apple/swift/tree/master/lib/ClangImporter).
		* Imports Clang modules and maps the C or Objective-C APIs they export into their corresponding Swift APIs.
		* The resulting imported ASTs can be referred to by semantic analysis.
	* _SIL generation : _
		* Swift Intermediate Language (SIL).
		* High level, Swift-specific intermediate language suitable for further analysis and optimization of Swift code.
		* Implemented in [lib/SILGen](https://github.com/apple/swift/tree/master/lib/SILGen).
		* SIL generation phase lowers the type-checked AST into so-called "raw" SIL.
		* Design of SIL is described in [docs/SIL.rst](https://github.com/apple/swift/blob/master/docs/SIL.rst).
	* _SIL guaranteed transformation : _
		* Implemented in [lib/SILOptimizer/Mandator](https://github.com/apple/swift/tree/master/lib/SILOptimizer/Mandatory).
		* Perform additional dataflow diagnostics that affect the correctness of a program (such as use of uninitialized variables).
		* End result of these transformations is "canonical" SIL.
	* _SIL Optimizations : _
		* Implemented in [lib/Analysis](https://github.com/apple/swift/tree/master/lib/SILOptimizer/Analysis), [lib/ARC](https://github.com/apple/swift/tree/master/lib/SILOptimizer/ARC), [lib/LoopTransforms](https://github.com/apple/swift/tree/master/lib/SILOptimizer/LoopTransforms) and [lib/Transforms](https://github.com/apple/swift/tree/master/lib/SILOptimizer/Transforms).
		* Perform additional high-level, Swift-specific optimizations to the program, including (for example) Automatic Reference Counting optimizations, devirtualization and generic specialization.
	* _LLVM IR Generation : _
		* Implemented in [lib/IRGen](https://github.com/apple/swift/tree/master/lib/IRGen).
		* Lowers SIL to LLVM IR, at which point LLVM can continue to optimize it and generate the machine code.
# Standard Library Design
* Swift standard library encompasses a number of data types, protocols and fuctions, including fundamental data types, collections along with protocols that describe them and algorithms that operate on them, characters and strings and low-level primitives (E.g., `UnsafeMutablePointer`).
* Implementation of the standard library resides in the `stdlib/public` subdirectory within the [Swift repository](https://github.com/apple/swift) which is futher subdivided into : 
# References
* https://swift.org/compiler-stdlib/
