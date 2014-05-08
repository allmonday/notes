# Overview of HTTP


## Web Clients and Servers
HTTP server存储互联网的数据，并把数据提供给HTTP client， client 发送请求， server返回请求的数据  
server 和client 是互联网的基本组成
## Resources
最简单的资源是静态文件，可以是文本，html，word，pdf或其他。  
资源也可以是由程序产生，这些动态文件因用户身份，请求内容，时间的不同而不同，可以显示摄像头实况，交易股票或网上购物
## Media Types
互联网会给传输的对象打上标签： MIME type（Multipurpose Internet Mail Extensions），这货最早是用来在不同邮件系统中传输邮件，因为它运行的很好所以HTTP就采用它描述和标记多媒体内容。  
浏览器从服务器获得对象后，会查看它的MIME 类型来决定如何处理。 这样的类型有上百种： 图像，html，音频，软件插件等等。  
`Content-Type: image/jpeg`  
`Content-Type: 12984`  

* html 文件： text/html
* 二进制文件： text/plain
* JPEG图片： image/gif
* Apple Quick Time: video/quicktime
* PPT: application/vnd.ms-powerpoint

## URIs
每个服务器都有个名字（废话），被称为URI (uniform resource identifier)，就像邮件地址一样。  
把URI给服务器后，HTTP就找到了文件。 URI有两部分： URLs 和 URNs
### URLs  
uniform resource locator 是资源id的最常用格式  
`http://www.joes-hardware.com/specials/saw-blade.git`  
http protocol - .com - resources
  
URI | Description  
----|----
http://www.joes-hardware.com/inventory-check.cgi?item=12731 | 运行程序查询12731股票
ftp://joe:tools4u@ftp.joes-hardware.com/locking- pliers.gif | 加密FTP协议  
如今，大多URI都是URL
### URNs
uniform resource name, URNs允许资源由多个网络协议获取。  
`urn:ietf:rfc:2141`  
反正是不温不火就是了
## Transactions
HTTP 传输由 request 和 response 组成， 传输由HTTP message通信。
## Methods
HTTP支持多种请求命令-method， method告诉服务器该执行什么操作：

http method | Description
----- | -----
`GET` | send named resource from server to client
PUT | Store data from client into a named server resource
DELETE | Delete the named resource from a server
`POST` | Send client data into a server gateway application
HEAD | Send just the HTTP headers from the response for the named resource  

有关GET和POST的区别，参考链接：
[简明魔法手册](http://www.nowamagic.net/librarys/veda/detail/1919)
## Status Codes
HTTP status code | description  
-----|-----
200 | OK, return correctly.
302 | Redirect, 转到其他地方找资源去了
404 | 抱歉，资源没找到

## Web Pages Can Consist of Multiple Objects
其实就是字面意思
## Messages
HTTP request 和 response 报文。
HTTP messages是简单线性的字符串，文本，而不是二进制文件，方便人类读写.  

part | request | response  
----|----|------
start line |GET /test/hi-there.txt HTTP/1.0  | HTTP/1.0 200 OK
Headers | Accept: text/*  Accept-Language:en, fr| Content-Type: text/plain, Content-length:19
Body | | Hi! I'm a message  

## Connections
###TCP/IP
* 零错误传送
* 有序发送
* 非限定数据流（尺寸自由）

消除了个体之间的差异，有了共同的语言。  
一旦TCP连接建立后， 数据交换就很可靠了。  
HTTP 使用 TCP 传送数据， 而TCP用的是IP  

1. HTTP  
2. TCP  
3. IP  4. 
4. Netword-specific link interface  
5. Physical network hard6.   

###Connections, IP Addresses, and Port Numbers
###A Real Example Using Telnet
##Protocol Version
##Architectural Components of the Web
###Proxies
###Caches
###Gateways
###Tunnels
###Agents
##For More Informationh
###HTTP Protocol Information
####Http Pocket Reference
####[w3.org/protocols](http://www.w3org/Protocols/)

