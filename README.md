企名片
=============

思路
------------

进入开发者模式查看xhr请求，查看请求的响应，里面有一个encrypt_data，是个长字符串，结尾的"="又让人想起base64，实际上这个内容加密确实用到的base64编码。
加密流程：首先对正常数据进行base64加密，然后对加密后的字符串进行js加密，就成了返回响应的encrypt_data。所以关键是
