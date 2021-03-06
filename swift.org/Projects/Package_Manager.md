* Swift Package Manager is a tool for managing the distribution of Swift code.
* It is integrated with the Swift build system to automate the process of downloading, compiling and linking dependencies.
* Included in Swift 3.0 and above.
# Conceptual Overview
## Modules
* Swift organizes code into `modules`.
* Each module specifies a namespace and enforces access controls on which parts of that can be used outside of the module.
* A program may import other modules as `dependencies`.
* Aside from handful of system-provided modules, such as Darwin on macOS or Glibc on Linux, most dependencies require code to be downloaded and built in order to be used.
## Packages
* Consists of Swift source files and a manifest file.
* The manifest file, called `Package.swift`, defines the package's name and its contents using the `PackageDescription` module.
* A package has one or more targets.
* Each target specifies a product and may declare one or more dependencies.
## Products
* A target may build either a library or an executable as its product.
* A `library` contains a module that can be imported by other Swift code.
* An `executable` is a program that can be run by the operating system.
## Dependencies
* A target's dependencies are the modules that are required by code in the package.
* A dependency consists of a relative or absolute URL to the source of the package and a set of requirements for the version of the package.
* The role of package manager is to automate the process of downloading and building all of the dependencies for a project.
# References
* https://swift.org/package-manager/
