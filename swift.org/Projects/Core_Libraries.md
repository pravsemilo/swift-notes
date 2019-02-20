* Provides higher-level functionality than the Swift standard library.
* Provides powerful tools that developers can depend upon across all the plaforms that Swift supports.
* Core Libraries have a goal of providing stable and useful features in the following areas : 
	* Commonly needed types including data, URLs, character sets and specialized collections.
	* Unit testing.
	* Networking primitives.
	* Scheduling and execution of work, including threads, queues and notifications.
	* Persistence, including property lists, archives, JSON and XML parsing.
	* Support for date, time and calendar.
	* Abstraction of OS specific behavior.
	* File system interaction.
	* I18N.
	* User preferences.
# Foundation
* Defines a base layer of functionality that is required for almost all applications.
* Provides primitive classes and introduces several paradigms that define functionality not provided by the language or runtime.
* Swift.org version of Foundation makes use of many of the same underlying libraries (E.g. ICU and CoreFoundation) as Apple's implementation, but has been built to be completely independent of the Objective-C runtime.
	* Because of this it is a substantial reimplementation of the same API using pure Swift code layered on top of common underlying libraries.
* Designed with these goals in mind :
	* Provide a small set of basic utility classes.
	* Make software development easier by introducing consistent conventions.
	* Suport I18N and localization.
	* Provide a level of OS independence to enhance portability.
# libdispatch
* Also called `Grand Central Dispatch (GCD)`.
* Provides comprehensive support for concurrent code execution on multicore hardware.
* Currently available on all Darwin platforms.
* Aim is to make a modern version available on all other platforms.
# XCTest
* Designed to provide a common framework for writing unit tests.
* This version of XCTest uses the same API as the XCTest you are familiar with from Xcode.
# References
* https://swift.org/core-libraries/
