#http

###http 请求

- http 请求包括3部分：请求行、请求头、请求体
- 浏览器将自动生成3部分内容发送给服务器


#####请求行
    
    请求的第一行
    	GET http://localhost:8081/ HTTP/1.1
    格式：请求方式、请求路径、协议／版本
    请求方式：7种，GET、POST、DELETE、option、put、head、trace
    常用2种：GET、POST
    
    GET请求
    
    GET请求将请求内容追加在请求行的请求路径上
    请求URL长度是有限的，GET请求追加的内容是有限的。一般：1024字节（1k）
    
    POST请求
    
    将请求内容存放在请求体中
    存放在请求体中，POST可以服务器发任意多的数据


#####请求头

    Accept:text/html,image/*      --支持数据格式
    
    Accept:Charset:ISO-8859-1     --字符集
    
    Accept-Ecoding:gzip           --支持压缩格式
    
    Accept-Language:zh-cn         --语言环境
    
    Host:www.baidu.com:80        --访问主机
    
    If-Modified-Since: Tue,11Jui 2000 18:23:51 GMT  -- 缓存时间
    
    Referer:http://www.baidu.com/index.jsp          -- 来自哪个页面、防盗链，如果没有通过超链接访问2.html返回null
    
    User-Agent:Mozilla/4.0(compatible;MSIE 5.5; Windows NT 5.0) -- 用户数据
    
    Cookie    --表示cookie技术
    
    Connection:close/Keep-Alive      --链接状态
    
    Date:Tue,11 Jui 2000 18:23:51 GMT  --时间
    
MIME类型：多用途互联网邮件扩展类型

    格式：大类型／小类型；参数
    大类型：分7类，表示互联网所有资源
    
    Text：用于标准化表示文本信息，文本消息可以是多种字符集或者多种格式；
    
    Multipart：用于连接消息体的多个部分构成一个消息，这些类型可以是不同类型的数据。
    
    Application：用于传输应用程序的数据或者二进制数据；
    
    Message：用于包装一个E-mail 消息；
    
    Image： 用于传输静态图片数据；
    
    Video： 用于传输动态影像数据，可以是与音频编辑在一起的视频数据格式。
    
    Audio：用于传输音频或者音声数据
    
    
Content-Encoding 压缩格式，GZIP 格式

Content_Type 设置页面数据类型，使用MIME类型。格式 大类型／小类型［；参数］例如：-->text/html;charset=UTF-8

Refresh 刷新

格式1：refresh ：3 表示3秒钟刷新当前页面一次。
格式2: refresh ：3；url＝  表示3秒钟刷新制定的url


Content-disposition,用于文件的下载，值大部分是固定的"attachment；filename.png",set-cookie 与请求头 cookie 一起使用

    

###http协议响应

分为3部分：响应行、响应头、响应体

#####相应行

    服务器 响应  浏览器  状态信息描述
    例如：http/1.1 200 OK
    格式：协议／版本  状态码  状态码对应的描述信息

#####状态码
    1xx：服务器响应浏览器，数据正在发送中，一般使用很少
    
    2xx：服务器相应浏览器已经过正常结束。常用：200 表示正常
    
    3xx：服务器响应浏览器，请求还没有完成，需要浏览器进一步操作，来完成整个请求。
    常见状态码：
    302（307）：与相应头结合完成页面重新跳转
    304:页面读取缓存
    
    4xx：服务器响应浏览器，浏览器操作异常
        常见：404 页面找不到（一般请求页面找不到表示用户URl写错）
        
#####响应体
服务器发送给浏览器的内容

    提供字符流：PrintWriter getWriter() －－>提供了write() 和 print()
    提供字节流：ServletOutputStream getOutputStream()-->提供了write()和print()
    注意：所有的print()底层都是write()-->流最后只使用一个write(int)
    
```
 public void print(String s){
  if(s==null){
        s= "null";
  }
  
    write(s);
 }
```

    流的使用，一般情况下：如果发送的是中文数据使用字符流
    如果发送二进制数据（字节）等，使用字节流。例如：下载
    
    一般情况，如果使用流。必须关闭流。但servlet中如果使用可以不关闭。
    如果没有关闭流，tomcat在请求结束时，将自动关闭。



    
        
    
    
    
    


    
    
    