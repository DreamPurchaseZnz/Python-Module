# Selenium
## [Installation](http://selenium-python.readthedocs.io/installation.html)
```
Downloading Python bindings for Selenium                ---> pip install selenium
Drivers                                                 ---> Chrome verson correspond to 
                                                             the Chrome driver version
```
* [Drivers List](http://chromedriver.storage.googleapis.com/index.html?/)
* [Correspondings](https://sites.google.com/a/chromium.org/chromedriver/downloads)

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






