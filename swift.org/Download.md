# Using Downloads
## Apple Platform
* Xcode includes a release of Swift supported by Apple.
### Installation
* Download the latest package release.
* Run the package installer,
	* This will install Xcode toolchain into `/Library/Developer/Toolchains/`.
	* An Xcode toolchain (.xctoolchain) includes a copy of compiler, lldb and other related developer tools.
* Open Xcode's `Preferences`, navigate to `Components > Toolchains` and select the installed Swift toolchain.
* Selecting a Swift toolchain affects the Xcode IDE only.
	* To use Swift toolchain with CLI :
		* `xcrun --tolchain swift`
		* `xcodebuild --toolchain swift`
		* Add Swift toolchain to your path.
		```bash
		$ export PATH=/Library/Developer/Toolchains/swift-latest.xctoolchain/usr/bin:${PATH}
		```
## Linux
* Packages for Linux are tar archives including a copy of Swift compiler, lldb and related tools.
* You can install them anywhere as long as they are in your `PATH`.
* Dependencies
```bash
$ sudo apt-get install clang libicu-dev
```
# References
* https://swift.org/download/
