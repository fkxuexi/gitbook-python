## 1、使用程序来操作浏览器

- 1.pip3 install selenium

- 2.[下载webdriver(chrome的)](http://selenium-python.readthedocs.io/index.html)

- 3.配置环境变量(把下载的chromedriver.exe路径配置到环境变量

```python
from selenium import webdriver
// 这种方式不用配置环境变量
browser = webdriver.Chrome("C:\Program Files (x86)\Google\Chrome\Application\chromedriver.exe")
browser.get('http://www.baidu.com/')
```
如果操作成功，就能成功的打开chrome