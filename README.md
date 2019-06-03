企名片
=============

思路
------------

进入开发者模式查看xhr请求，查看请求的响应，里面有一个encrypt_data，是个长字符串，结尾的"="又让人想起base64，实际上这个内容加密确实用到的base64编码。
加密流程：首先对正常数据进行base64加密，然后对加密后的字符串进行js加密，就成了返回响应的encrypt_data。所以关键是找到加密的js代码，然后execjs运行得到第一步解密的字符串，再进行base64解码就可以了。

js代码需要调试寻找，不会调试的百度，具体就不多说了，放两张关键的图：

![image](https://github.com/xzh0723/QiMingPian/blob/master/js_1.png)
![image](https://github.com/xzh0723/QiMingPian/blob/master/js_2.png)

注：完整的js代码还需要稍微改造一下，有两个坑： （1）JSON.parse()方法execjs不支持，需要改成 new Buffer(); （2）最后的输出要加toString('base64')，转化为base64字符串。有不会的欢迎issues提问。

成果
============
![image](https://github.com/xzh0723/QiMingPian/blob/master/view.png)
