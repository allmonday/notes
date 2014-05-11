#URLs and Resources
##Navigating the Internet's Resources
URL靠的是表示资源的位置，而URN 是使用独立的命名，而无视资源的位置。  

* http://www.joes-hardware.com/seasonal/index.html  
* mailto:president@whitehouse.gov
* ftp://ftp.lot-o-books.com/pub/complete-price-list.xls
* rtsp://www.joes-hardware.com:554/interview/cto_video



###The Dark days before URLs
在从前，要是需要传一个xls文件，得连上fpt先，在匿名登录，切到pub目录，binary模式，在开始下载。  
现在，一个浏览器中就能完成这一切。  
URL简化了应用程序对资源的获取。  


##URL syntax
是的，有多种scheme.  
但是，区别不怎么大。  
通常的形式是：  
\<scheme>://\<user>:\<password>@\<host>:\<port>/\<path>;\<params>?\<query>#\<frag>  

component | description | default value
-----|-----|-----
scheme | protocol |
user | username |
password | password |
host | host, IP
port | port number |
path | path.. | 
params | name/value pair, multiple |
query | active application, separated from the rest by ? |
frag | 不是传给server的，而是client内使用,用#分开 |

###Schemes
该使用那种协议呢

###Host and port
* host: 表示主机，可以域名也可以ip
* port: 表示哪个server监听

###Usernames and password
ftp会要求用户名和密码进行登录 ，可以`没有`, `匿名`, `user:password`
###Paths
想象成linux根目录就行了  
###Parameters`;`
除了知道地址，端口，用户名，你还需要些其他的..  
FTP来说，有两种传输方式，文本和二进制，所以需要参数来确定  
参数用 `;`来和剩余部分分割  
ftp://prep.ai.mit.edu/pub/gnu;type=d  
表示type的值为d  
path的每个部分都可以添加参数：  
http://www.joes-hardware.com/hammers;sale=false/index.html;graphics=true

###Query Strings `?`
某人向web database 查询产品库存：    http://www.joes-hardware.com/inventory-check.cgi`?`item=12731  
separated by `&`  http://www.joes-hardware.com/inventory-check.cgi?item=12731&color=blue&size=large  
###Fragments`#`
对一个超大的文本文件，URL会指向这整一个文件，但理想的话最好指向特定的部分~  
fragment 挂在URL的最右面：  
http://www.joes-hardware.com/tools.html#drills  
server那里不会管这些，送过来就好了，定位这事都是交给client做得。  

##URL shortcuts
短地址
###Relative URLs
很简单，用linux地址自动脑补一下就知道了  
####Base URLs
要相对跳转就得有基地址，它来自三个地方：  

* <BASE> HTML tag  
* URL 的地址
* 绝对地址


####Resolving relative references
page 33
###Expandomatic URLs
##Shady Characters
###The URL Character Set
###Encoding Mechanisms
###Character Restrictions
###A Bit More
###A Sea of Schemes
##The Future
##For more info
