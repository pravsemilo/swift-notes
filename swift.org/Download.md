# Using Downloads
## Apple Platform
* Xcode includes a release of Swift supported by Apple.
### Installation
1. Download the latest package release.
1. Run the package installer,
	* This will install Xcode toolchain into `/Library/Developer/Toolchains/`.
	* An Xcode toolchain (.xctoolchain) includes a copy of compiler, lldb and other related developer tools.
1. Open Xcode's `Preferences`, navigate to `Components > Toolchains` and select the installed Swift toolchain.
1. Selecting a Swift toolchain affects the Xcode IDE only.
	* To use Swift toolchain with CLI :
		* `xcrun --toolchain swift`
		* `xcodebuild --toolchain swift`
		* Add Swift toolchain to your path.
		```bash
		$ export PATH=/Library/Developer/Toolchains/swift-latest.xctoolchain/usr/bin:${PATH}
		```
## Linux
* Packages for Linux are tar archives including a copy of Swift compiler, lldb and related tools.
* You can install them anywhere as long as they are in your `PATH`.
### Installation
1. Install required dependencies.
```bash
$ sudo apt-get install clang libicu-dev
```
2. Download the latest binary release.
3. Extract the archive.
4. Add the Swift toolchain to your path.
# References
* https://swift.org/download/
