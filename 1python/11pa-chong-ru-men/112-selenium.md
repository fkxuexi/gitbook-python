## 1、使用程序来操作浏览器

- 1.pip3 install selenium

- 2.[下载webdriver(chrome的)](http://selenium-python.readthedocs.io/index.html)

- 3.配置环境变量(把下载的chromedriver.exe路径配置到环境变量

```python
from selenium import webdriver;
from selenium.webdriver.common.keys import Keys;


def openChrome(path):
    browser = webdriver.Chrome(path);
    browser.get('www.baidu.com')

# 选取元素，如果是多个元素则使用find_elements_by_*
# find_element_by_id
# find_element_by_name
# find_element_by_xpath
# find_element_by_link_text
# find_element_by_partial_link_text
# find_element_by_tag_name
# find_element_by_class_name
# find_element_by_css_selector
def controllerChrome(path):

    # 添加代理：
    options = webdriver.ChromeOptions();
    options.add_argument('user-agent="Mozilla/5.0 (Linux; Android 4.0.4; Galaxy Nexus Build/IMM76B) '
                         'AppleWebKit/535.19 (KHTML, like Gecko) Chrome/18.0.1025.133 Mobile Safari/535.19"');

    # 添加这个代理之后，界面的效果会类似我们使用F12手机调试的效果
    driver = webdriver.Chrome(path,options = options);
    #driver.get('https://www.python.org');
    driver.get('https://www.baidu.com')
    assert 'Python' in driver.title;

    searchDom = driver.find_element_by_name('q');
    searchDom.send_keys('pycon');
    searchDom.send_keys(Keys.RETURN);
    print(driver.page_source);

# 执行js脚步进行分页，
def downBaiduArticle(path):
    option = webdriver.ChromeOptions();
    option.add_argument('user-agent="Mozilla/5.0 (Linux; Android 4.0.4; Galaxy Nexus Build/IMM76B) '
                        'AppleWebKit/535.19 (KHTML, like Gecko) Chrome/18.0.1025.133 Mobile Safari/535.19"')

    driver = webdriver.Chrome(path,options=option);
    driver.get('https://wenku.baidu.com/view/aa31a84bcf84b9d528ea7a2c.html');
    page = driver.find_elements_by_xpath("//div[@class='page']")
    driver.execute_script('arguments[0].scrollIntoView();', page[-1])
    nextpage = driver.find_element_by_xpath("//a[@data-fun='next']")
    nextpage.click()

if __name__ == '__main__':
    chromeDriverPath = 'C:\Program Files (x86)\Google\Chrome\Application\chromedriver.exe';

    #openChrome(chromeDriverPath);
    downBaiduArticle(chromeDriverPath);

```
如果操作成功，就能成功的打开chrome