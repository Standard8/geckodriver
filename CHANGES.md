# Change log

All notable changes to this program is documented in this file.

## Unreleased

### Changed
- Accepted capabilities changed to a chromedriver-like dictionary of keys and values; this will cause `firefox_binary`, `firefox_args` and `firefox_profile` to stop working
- Removed `--no-e10s` flag, and geckodriver will from now rely on the Firefox default multiprocessing settings (override using preferences)
- Disable pop-up blocker in the default profile by @juangj

## 0.10.0 (2016-08-02)

### Changed
- Use multi-process Firefox (e10s) by default, added flag `--no-e10s` to disable it and removed `--e10s` flag
- Disable autofilling of forms by default by @mythsunwind
- Replace _argparse_ with _clap_ for arguments parsing

### Fixed
- Attempt to deploy a single file from Travis when making a release
- Grammar fix in README


## 0.9.0 (2016-06-30)

### Added
- Add ability to use `firefox_binary` capability to define location of Firefox to use
- Automatically detect the default Firefox path if one is not given
- Cross-compile to Windows and ARMv7 (HF) in CI
- Add Musl C library-backed static binaries in CI
- Add `-v`, `-vv`, and `--log LEVEL` flags to increase Gecko verbosity
- Add Get Element Property endpoint
- Add new `--version` flag showing copying information and a link to the repository

### Changed
- Now connects to a Marionette on a random port by default
- Update webdriver-rust library dependency
- Migrated to use Travis to deploy new releases
- Reduced amount of logging
- Introduced a changelog (this)


## 0.8.0 (2016-06-07)

### Added
- Allow specifying array of arguments to the Firefox binary through the `firefox_args` capability
- Pass parameters with New Session command

### Changed
- Change product name to _geckodriver_
- Make README more exhaustive
- Quit Firefox when deleting a session
- Update webdriver-rust library
- Update dependencies

### Fixed
- Fix tests
- FIx typo in error message for parsing errors


## 0.7.1 (2016-04-27)

### Added
- Add command line flag for using e10s enabeld Firefox by @martionsideofthemoon
- Allow providing custom profiels

### Changed
- Allow binding to an IPv6 address by @juangj
- By default, connect to host-agnostic localhost by @juangj
- Make `GeckoContextParameters` public
- Update dependencies

### Fixed
- Squash rustc 1.6 warnings by using `std::thread::sleep(dur: Duration)`


## 0.6.2 (2016-01-20)

### Added
- Add LICENSE file from @joshbruning
- Schedule builds in CI on pushes and pull requests

### Changed
- Enable CPOWs in Marionette


## 0.6.0 (2016-01-12)
- Add Get Page Source endpoint

### Changed
- Handle arrays being sent from Marionette
- Correct build steps in README
- Update what properties are read from errors sent by Marionette
- Update dependencies


## 0.5.0 (2015-12-10)

### Added

### Changed
- Update argparse dependency to use Cargo
- Update to the latest version of the Marionette wire protocol
- Update to latest webdriver-rust library
- Update dependencies


## 0.4.2 (2015-10-02)

### Changed
- Skip compiling optional items in hyper


## 0.4.1 (2015-10-02)

### Changed
- Update webdriver-rust library
- Update dependencies


## 0.4.0 (2015-09-28)

### Added
- Add command extensions for switching between content- and chrome contexts
- Add more documentation from @vladikoff

### Changed
- Update Cargo.lock with new dependencies for building
- Update for protocol updates that flatten commands
- Update to new protocol error handling
- Update for Marionette protocol version 3 changes
- Strip any leading and trailing `{}` from the `sessionId` Marionette returns
- Update dependencies

### Fixed
- Fix `GetCSSValue` message to send correct key `propertyName`
- Fix example in documentation from @vladikoff


## 0.3.0 (2015-08-17)

### Added
- Add support for finding elements in subtrees


## 0.2.0 (2015-05-20)

### Added
- Extra debug messages
- Add ability to set WebDriver port
- Add support for getting the active element
- Add support for `GetCookies` and `DeleteCookie`/`DeleteCookies`
- Add preferences that switch off certain features not required for WebDriver tests

### Changed
- Make failing to communicate with Firefox a fatal error that closes the session
- Shut down session only when loosing connection
- Better handling of missing command line flags
- Poll for connection every 100ms rather than every 100s
- Switch to string-based error codes
- Switch webdriver-rust library dependency to be pulled from git
- Update dependencies

### Fixed
- Handle null id for switching to frame more correctly


## 0.1.0 (2015-04-09)

### Added
- Add proxy for converting WebDriver HTTP protocol to Marionette protocol
- Add endpoints for modal dialogue support
- Allow connecting to a running Firefox instance
- Add explicit Cargo.lock file
- Start Firefox when we get a New Session command
- Add flag parsing and address parsing
- Add basic error handling

### Changed
- Update for Rust beta
- Switch to new IO libraries
- Pin webdriver-rust commit so we can upgrade rustc versions independently
- Set preferences when starting Firefox
- Improve some error messages
- Re-enable environment variable based logging

### Fixed
- Fix Get Element Rect command to return floats instead of integers
- Fix passing of web elements to Switch To Frame command
- Fix serialisation of script commands
- Fix assorted bugs found by the Selenium test suite
- Fix conversion of Find Element/Find Elements responses from Marionette to WebDriver
- Fixed build by updating Cargo.lock with new dependencies for building
- Squash compile warnings
