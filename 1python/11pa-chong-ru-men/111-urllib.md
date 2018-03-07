```python
# coding:utf-8
from urllib import request;
import chardet;

if __name__ == '__main__':
response = request.urlopen("http://www.baidu.com");
html = response.read();
charset = chardet.detect(html)['encoding'];
html = html.decode(charset);
print(html);
```