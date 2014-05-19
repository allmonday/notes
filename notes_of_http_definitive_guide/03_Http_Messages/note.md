#HTTP Messages
如果HTTP是互联网的快递员，那么HTTP报文就是发送的快件。  
在这里我们会讲述HTTP信息是如何被创建的， 以及怎么理解她。  

- 信息怎样传送
- 三要素： start line, header ,entity body
- request, response
- 怎样支持不同的method
- 不同的status code
- http header做什么
 

##The Flow of Messages
http message 是一块块数据， 他们由元数据来描述自己， inbound, outbound, upstream 和 downstream 用来描述数据的发送方向  
###Messages commute inbound to the origin server
inbound , to server :发送到服务器  
outbound , to user agent : 返回客户端  

###Messages flow downstream
request -> flowing downstream  
response -> flowing downstream  
##The Parts of a Message
three parts:  

- start line: describing message
- header: containing attributes
- optional body: containing data

他们由行分割，每一行由两个字符的结束序列结束- carriage return & line-feed : CRLF.  
好的应用应该能接受两者之一的表示。  
body可以包含文本或者二进制数据，或者


###Message syntax
他们只有两类， request和 response.  
request 向服务器发出需求  
response 返回内容  
以 获取__GIF__为例：  

```
<method><request-URL><version>  
<headers>
<entity-body>

startline: GET /special/saw-blade.git HTTP/1.0
header: Host: www.joe-hardware.com

<version><status><reason-phrase>
<headers>
<entity-body>

startline: HTTP/1.0 200 OK
Header:Content-Type: image/gif
       Content-Length: 8572
```


name | description
----|-----
method | action: GET, HEAD, POST..
request-URL | ..
version  | HTTP/<major>.<minor>
status-code | success, error, etc
reason-phrase | human-readable,  HTTP/1.0 200 NOT OK ，NOT OK不重要
header | 字典描述 Accept: text/*
entity-body | $%^&*()%^&%^&*
###Start lines
####request line
所有的fields由空格分割。  
GET /special/saw-blade.git HTTP/1.0
####response line
先于HTTP/1.0是不需要包含response line （？）
####methods
common method | description | messsage body?
-----|-----|-----
GET | get document from server | No
HEAD | get just **headers** for a document from the server | NO
POST | send data to the server for processing | Yes
PUT | Store the body of the request on the server | Yes
TRACE | trace the message through proxy server to the server | No
OPTION | determin what methods can operate on a server | No
DELETE |  remove a document from the server | No

这些以外的可以由服务器自定义实现，称为extension methods
####status codes

overall range | defined range | category
-----|-----|-----
100-199 | 100-101 | informational
200-299 | 200-206 | successful
300-399 | 300-305 | redirection
400-499 | 400-415 | Client error
500-599 | 500-505 | Servor error

status | reason phrase | meaning
----|----|----
200 | Ok | success
401 | unauthorized | 请键入用户名和账号
404 | Not found | 找不到请求的URL
####reason phrases
无关紧要的小注释
####version numbers
要向下兼容哦哦

###Headers
####Header classifications

- general headers
- request headers
- response headers
- entity header
- extension headers


####Header continuation lines
###Entity Bodies
###Version 0.9 Message

##Methods
GET, HEAD 需要被实现  
有些method有严格的限制， 如DELETE就不能允许所有的用户删除数据。  

###safe method
###GET
###HEAD
###PUT
###POST
###TRACE
###OPTION
###DELETE
###Extension method

