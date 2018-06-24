# Selenium
## [Installation](http://selenium-python.readthedocs.io/installation.html)
```
Downloading Python bindings for Selenium                ---> pip install selenium
Drivers                                                 ---> Chrome verson correspond to 
                                                             the Chrome driver version
```
* [Drivers List](http://chromedriver.storage.googleapis.com/index.html?/)
* [Correspondings](https://sites.google.com/a/chromium.org/chromedriver/downloads)
```
Latest Release: ChromeDriver 2.40
Supports Chrome v66-68

Changes include:
Fixed Chromedriver hang on open when user-data-dir is specified and exists
ChromeDriver supports IPv6 on requests
Fixed Chromedriver couldn't find the Android file using valid file path
/session/:sessionId/send_command and /session/:sessionId/send_command_and_get_result changed to proper extension commands

ChromeDriver 2.39

Supports Chrome v66-68

Changes include:
Fixed ChromeDriver for Android does not provide useful error message for old adb version
Fixed ChromeDriver tests that close Windows are flaky
Fixed Click on component into an Iframe (with container padding > 0) is not working
Fixed ChromeDriver remote debug port reservation race conditions
Fixed Get Alert Text is not returning spec compliant error codes
Fixed Clean up state of androidUseRunningApp feature
Fixed Minimize/Maximize window need a w3c compliant endpoints
ChromeDriver 2.38

Supports Chrome v65-67 

Changes include:
Fixed Chromedriver crash/lose connection when navigate to gmail 
Fixed unknown session ID and cannot determine loading status
Resolved Chromedriver doesn't wait until iframe content loads after switching into iframe
Fixed element is not clickable at point.

ChromeDriver 2.37

Supports Chrome v64-66

Changes include:
Fixed an issue with handling iframe on Chrome v66
Implemented various window command endpoints from w3c spec
Implemented get element rect endpoint from w3c spec
Fixed the parsing of extensionLoadTimeout option to allow value of 0
ChromeDriver 2.36

Supports Chrome v63-65

Changes include:
Allowed access to chrome extension within iframe
Added command-line option to log INFO level to stderr
Fixed ChromeDriver hang when switching to new window whose document is being overwritten
Added option to control the wait for extension background pages
Fixed abstract UNIX socket name
Fixed loading extension if background page name starts with '/'
ChromeDriver more extensible on Android by allowing to set the exec name and device socket as capabilities
Pixel 2 and Pixel 2 XL are now working in Mobile Emulation
Chromedriver supports OOPIF

ChromeDriver 2.35

Supports Chrome v62-64

Changes include:
Supports persistent connections between client application and ChromeDriver.
Adds more devices types for mobile emulation.
Fixes a bug in get local storage command.
Fixes a compatibility bug that causes JavaScript code execution to fail on some versions of Chrome.
Uses absolute time in log file.

ChromeDriver 2.34

Supports Chrome v61-63

Changes include:
Supports new navigation model in Chrome v63+.
Fixes a bug where touch in mobile emulation doesn't work.
Fixes a bug in emulating Android devices.
Removed Timeline as a supported perf log domain type (no longer supported in Chrome).
ChromeDriver 2.33

Supports Chrome v60-62

Changes include:
Fixes a bug where Chromedriver crashes while creating DNS resolver.
Fixes a bug where Chromedriver fails to click in mobile emulation mode on Chrome 61+.
Fixes a bug which caused Resizing/Positioning Window commands to fail on Chrome 62+.
Fixes a bug where Chromedriver fails to connect to webview on Android 8.0.0.
Updates to excludeSwitches capability that now allows to exclude --load-extension switch.
Updates to AddCookie command as per new w3c spec.
Updates to FindElement command as per new w3c spec.
ChromeDriver 2.32

Changes include:
Fixes a bug where Chromedriver fails to click due to page scrolling changes in Chrome 61+.
Fixes a bug where Chromedriver fails to delete cookies in Chrome 62+.
Implemented spec-compliant new session handshake.
Fixes a bug where Chromedriver fails to retrieve default prompt text in Chrome 62+.
Changes to the way automation extension is loaded on Mac and Windows.
The latest WebDriver atoms have been imported.
Supports new spec compliant endpoints for executing scripts.
Fixes a bug where Chromedriver fails to send characters 3 and # keys on Mac Chrome 62+.
Removed dependency of GLIBC 2.18.
Updates to capabilities processing as per new w3c spec.
Ensures sending keys to non-prompt dialog returns correct errors as per new w3c spec.
Ensure that file exists while sending keys to file input field.

ChromeDriver 2.31

Changes include:
Fixes a bug which caused SendKeys to fail on headless Chrome.
Support for Get Named Cookie WebDriver command.
Fixes a bug where Chromedriver sets incorrect path while adding cookie.
Fixes a bug where Chromedriver inconsistently fails to retrieve cookies.
Ensures that element is attached to page's DOM for switchToFrame command.
Fixes a bug where Chromedriver fails to handle ECMAScript strings.
Support for vendor-prefixed chromeOptions capability.
Fixes a bug which caused ChromeDriver to timeout when a page sets window.location.
Supports long command line arguments on Android Chrome.

ChromeDriver 2.30

Changes include:
Fixes a bug where Chromedriver fails to delete temporary directories while exiting.
The list of mobile device names has been updated to match those in DevTools.
Fixes stack overflow errors in JavaScript code used by ChromeDriver.
Accepts empty Blink revision to work with Chrome 60+ on Chrome OS platform.
Fixes a bug which causes ChromeDriver to crash on using console.time from Chrome 58+.
Updates to AddCookie implementation.
Allows access to chrome extension within iframe.
Chromedriver now uses DevTools commands to perform window management operations.
Sending text to alert/confirm dialog will now return error.
Various updates to work with Chrome 58+.

ChromeDriver 2.29

Changes include:
Fixes a bug which caused ExecuteScript to fail when Object.prototype is modified.
Fixes a bug that interferes with handling the alert dialog on page unload.
Support for making the window tab visible on switching to windows.

ChromeDriver 2.28

Changes include:
Fixes a bug which blocked ChromeDriver automation extension from loading and thereby causing window resizing/positioning & screenshot functionalities to break.
Fixes a bug where NetLog json files were being truncated.
Fixes a bug which caused ChromeDriver to timeout and/or hang randomly while a dialog is showing.
Fixes a bug which caused FindElements to fail in some scenarios.
Various updates to work with Chrome 57+ .

ChromeDriver 2.27

This release fixes a bug which caused ChromeDriver to fail on pages with SharedWorkers.
ChromeDriver 2.26
Changes include:
Fixes a bug which caused SendKeys to fail to send a space character.
Support for emulating different network connections (e.g. offline, 2G, WiFi).
Support for automatically handling unexpected alerts.
The latest WebDriver atoms have been imported.
Prevents random error when accepting a dialog.
ChromeDriver 2.25
Changes include:
Fixes a bug which causes ChromeDriver to crash during Runtime.consoleAPICalled events from Chrome 54+
Prevents timeouts when fetching logs while a dialog is showing
ChromeDriver 2.24
Changes include:
Fixes for SendKeys errors, particularly with Chrome 53+
Fixes for calls to GetLog, both to reduce timeouts, and support changes in Chrome 53+
Updates to support recent remote debugging protocol changes in Chrome
ChromeDriver 2.23
Changes include:
A fix for ChromeDriver on Android 6.0 Marshmallow, which sometimes causes session initialization failures
A fix for a bug where console log messages were not being seen by ChromeDriver
ChromeDriver 2.22

```



## Get started


## Navigation



## Locating Elements



## Waits



## Page Objects



## WebDriver API
```
webdriver.Firefox
webdriver.FirefoxProfile
webdriver.Chrome
webdriver.ChromeOptions
webdriver.Ie
webdriver.Opera
webdriver.PhantomJS
webdriver.Remote
webdriver.DesiredCapabilities
webdriver.ActionChains
webdriver.TouchActions
webdriver.Proxy
```
```
class selenium.webdriver.chrome.webdriver.WebDriver(
executable_path='chromedriver', 
port=0, 
options=None, 
service_args=None, 
desired_capabilities=None, 
service_log_path=None, 
chrome_options=None
)
```
Methods
```
add_cookie
back
close
create_web_element
delete_all_cookies
execute
execute_async_script
execute_script                    ---> java script
file_detector_context
find_element
find_element_by_class_name
find_element_by_css_selector
find_element_by_id
find_element_by_link_text
find_element_by_name
find_element_by_partial_link_text
find_element_by_tag_name
...

```



### Actions
```
click
click_and_hold
context_click
double_click
drag_and_drop
drag_and_drop_by_offset
key_down
key_up
move_by_offset
move_to_element
move_to_element_with_offset
pause
perform
release
reset_actions
send_keys
send_keys_to_element
```






