#DOM 对象


#####4.1介绍

- DOM:Document object Model 文档对象模型，用于修改 （及可以对文档中的内容进行CRUD操作）
- 文档：结构化文档。例如：html、xml等
- DOM规范：html dom、xml dom等
- 操作，将html页面加载内容（浏览器），浏览器将整个文档生成一个对象 document，将采用dom树的方式对html内容进行展现
- 树 --数据结构,如下代码所示（二杈树）
- 二杈树，2个分支，最大2个分支，完全二叉树：每一个分支都是2分支，出了叶子

```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
	
</body>
</html>
```


#####4.2 document 获取

- 获取方式：window.document,浏览器将文档加载成功之后，自动生成dom树，并将封装好的对象赋值给window.document
- window 对象的属性，可以直接访问，以及document操作


#####4.3 Element 获取


- document.getElementById("id属性的值") ,  通过id属性值获得元素，id属性值必须在整个文档中是唯一的。
- document.getElementsByName("name 属性值"),通过标签name属性获得元素们，name属性值可以重复。
- document.getElementsByClassName("class 属性值")通过标签class属性获得元素们
- document.getElementsByTagName("标签名称")通过标签名来获得元素们



