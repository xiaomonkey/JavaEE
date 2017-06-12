 #Servlet
 
    什么是Servlet？
    
    1.java编写的服务器程序，服务器叫做server＋applet＝servlet
    
    applet： java 提供浏览器应用小程序，类似flash。
    
    2.java定义规范（接口），必须实现接口：javax.servlet.Servlet接口
    
    Servlet 接口实现类：javax.servlet.GenericServlet，通用servlet实现
    
    GenericServlet类子类：javax.servlet.http.HttpServlet类，基于http协议实现。
    
    3.servlet是服务器端程序，如果要使用浏览器必须是servlet配置一个访问的路径URI。 
 
 ---   
#####Response对象

    response 中使用流向浏览器发送数据，首先数据将写入数据流的缓存中，但是缓存大小8k时，将自动刷新到浏览器

- isCommited() 缓存是否刷新过    
- flushBuffer()手动的刷新，输出缓存
- resetBuffer() 清空缓存
- getBufferSize()获得大小
- 
- 

---


#####request对象

    回顾http协议请求
    包含：请求头，请求行，请求体
    
    oracle根据http协议，定义request相应规范（接口），tomcat实现request规范
    
    接口：javax.servlet.ServletRequest、javax.servlet.http.HttpServletRequest
    
    浏览器发送请求，tomcat将创建request和response对象，传递doGet()/doPost(),方法可以是具体的对象



请求行

- HttpServletRequest 接口提供getMethod()，获得get/post请求方式
- 


请求头







请求体


#####request属性操作

- request属性操作，服务器内部事情，浏览器是不知晓的
- Servlet3作用域对象：ServletContext、ServletRequest、HttpSession，3个对象都提供了xxxAttribute（set、get、remove）
- 如果使用request属性，必须和请求转发结合使用
- request属性特点：在一次请求中共享数据。一次请求可以涉及页面的个数：默认情况是1个，使用请求转发可以是多个
 

####RequestDispatcher 请求调度对象

- 请求调度：从当前的servlet，调度另一个servlet（资源、html、jsp等），在服务器内部，从一个servlet去执行另一个servlet，浏览器不知道的。
- 获取


    
    ServletRequest.getRequestDispatcher(String path) 获得请求调度对象，如果是／开头，表示web项目根

    ServletContext.getRequestDispatcher(String path) 获得请求调度对象，必须以／开头，表示web项目的根
    
    ServletContext.getNamedDispatcher(String ) (了解)
    
    api
    
    forward(ServletRequest rerquest,ServletResponse response) 
        A转发到B，只输出B的内容到浏览器。
        请求转发只会输出最后的一个servlet的内容
        
        如果iscomitted= true,再进行forward将抛异常，一般情况下如果输出少量数据，认为isComitted＝false
    ＊应用场景：
    请求转发：第一个 servlet处理数据，第二个servler显示数据－－mvc设计模式
    思想：处理与显示想分离
    
    include(ServletRequest request,ServeltResponse response) 请求包含
        A包含B，先输出A的内容到浏览器，再输出B的内容到浏览器
        请求包涵会输出所有的servlet汇总后的内容
    









    
    
    
    

    
    


    
    
    