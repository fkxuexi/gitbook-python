#### chardet
 
用来自动获取网页的编码，然后可以利用其解码

pip install chardet
# coding:utf-8
from urllib import request;
import chardet;

if __name__ == '__main__':
    response = request.urlopen("http://www.baidu.com");
    html = response.read();
    charset = chardet.detect(html)['encoding'];
    html = html.decode(charset);
    print(html);