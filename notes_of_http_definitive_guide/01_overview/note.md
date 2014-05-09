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
建立TCP连接有点像给公司办公室打电话，要有主机号码，然后是分机号。  
对应的在TCP里需要一个`IP地址`和一个`TCP端口号`  
看起来顺其自然不是吗，但号码和分机号从哪来的？ 当然是URL了。    

URL | description  
----|-----
`http://192.168.1.4/index.html` | 这个是裸露的URL地址, 端口默认80
`http://allsunday.eicp.net/index.html` | 给对数字无力的人，可以用hostname 
hostname（主机名）可以通过DNS 服务器进行转换，变成那串扰人的URL地址。  


###A Real Example Using Telnet
telnet是一个远程终端，键盘化作TCP端口，显示器化作TCP输出   
telnet一般用来远程会议，但也可以连到TCP服务器  
所以还是netcat更好啦。
##Protocol Version
协议版本 | 描述
------|-------
HTTP/0.9 | MIME，HTTP header, versions number..都不支持，很快就被1.0代替了
HTTP/1.0 | 第一个广泛使用的版本
HTTP/1.0+ | 迅速的扩张对协议提出了新的需求，加入了：keep alive,virtual hosting support,proxy..
HTTP/1.1 | 修补了结构上的瑕疵，支持了更多应用协议，是`当前版本`
HTTP-NG(a.k.a. HTTP/2.0) | next generation 啦
##Architectural Components of the Web
components | description  
---|---
proxies | 中间人，邮递员，媒婆，代理人，摄政王 误） 
caches | 在靠近client的地方放个仓库， 全家自提点
gateways | 连接到其他应用的特殊web服务~
tunnels | 暗地里的HTTP通讯
Agents | 可以自动处理HTTP请求的小聪明的web client (??)
###Proxies
位处client 和 server 之间，行代理人之责，在client看来就像是server般的存在  
一般用作保密， 可过滤request 和 response, 如删除病毒和成人内容（oh,no）等
###Caches
另一种proxy， 他会把常用的文件存起来，下一次对文件的请求就直接丢给你了啦  
其实里面还是蛮复杂的，要如何高效缓存，多久刷新数据，是否是隐私信息等等。  
###Gateways
又来了个中间人.. 不过这位比较多事，不老老实实做传话的，他负责转换协议，比如吧HTTP请求转成FTP之类的。 当然这些事情client是不知道的啦

###Tunnels
保密线路就是了，摸黑地在两个线路之间中继信息. 一般用来：用HTTP传输非HTTP数据，并且不暴露数据（？）
最常见的就是跑SSL- Secure Sockets Layer，允许SSL走防火墙里原本只允许web走的线路。  
HTTP/SSL 要先通过HTTTP建立一个连接（address, port）, 然后就能通信了。
###Agents
client 侧的应用， 根据用户的行为生成HTTP request. 目前我们只讨论browser这一种agent， 当然还存在许多user agent， 像spider啦。
##For More Informationh
###HTTP Protocol Information
原书20-21页ß
HTTP Pocket Reference  
####[w3.org/protocols](http://www.w3org/Protocols/)

