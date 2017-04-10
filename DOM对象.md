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
- 

#####4.4Element 方法

- appendChild() 指定元素内追加
- insertBefore()  指定的元素前追加  elementNode.insertBefore(new_node,existing_node)  new_node当前新创建的element，exiting_node已经存在的
- removeChild() 删除指定的元素，elementNode.removeChild(node)父元素删除子元素    element 必须是父元素，node 子元素 例如：childElement.parent.removeChild(childElement);


---

#5.计算器案例分析


```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
<style type="text/css">
	table{
		background-color: #D9E4F1;
	}

	input[type=button]{
		width: 38px;
		height: 28px;
		font-size: 14px;
	}
	input[type=button]:hover{
		background-color: #FFEF8A;
		border-color: #FFDB00;
	}
	
	input[type=text]{
		font-family:"Consolas";
		font-size:24px;
		height:30px;
		padding-bottom:0;
		padding-top:20px;
		text-align:right;
		width:198px;
	}
	
	#equals{
		height: 60px;
		font-size: 20px;
	}
	#zero{
		width: 80px;
		
	}

</style>
</head>
<!-- onload事件，当页面加载成功之后将执行 -->
<body onload= "init()">

<table>
		<tr>
			<td colspan="5">
				<input type="text" id="num" name="num" value="0"/>
			</td>
		</tr>
		<tr>
			<td >
				<input type="button" name="" value="MC"/>
			</td>
			<td >
				<input type="button" name="" value="MR"/>
			</td>
			<td >
				<input type="button" name="" value="MS"/>
			</td>
			<td >
				<input type="button" name="" value="M+"/>
			</td>
			<td >
				<input type="button" name="" value="M-"/>
			</td>
		</tr>
		<tr>
			<td >
				<input type="button" name="" value="←" style="font-size: 18px;"/>
			</td>
			<td >
				<input type="button" name="" value="CE"/>
			</td>
			<td >
				<input type="button" name="" value="C" onclick="clearData()"/>
			</td>
			<td >
				<input type="button" name="" value="±" onclick="getOperator('±')"/>
			</td>
			<td >
				<input type="button" name="" value="√"/>
			</td>
		</tr>
		<tr>
			<td >
				<input type="button" name="" value="7" onclick="getNumber('7')"/>
			</td>
			<td >
				<input type="button" name="" value="8"  onclick="getNumber('8')"/>
			</td>
			<td >
				<input type="button" name="" value="9"  onclick="getNumber('9')"/>
			</td>
			<td >
				<input type="button" name="" value="/"  onclick="getOperator('/')"/>
			</td>
			<td >
				<input type="button" name="" value="%" onclick="getOperator('%')"/>
			</td>
		</tr>
		<tr>
			<td >
				<input type="button" name="" value="4" onclick="getNumber('4')"/>
			</td>
			<td >
				<input type="button" name="" value="5" onclick="getNumber('5')"/>
			</td>
			<td >
				<input type="button" name="" value="6" onclick="getNumber('6')"/>
			</td>
			<td >
				<input type="button" name="" value="*" onclick="getOperator('*')"/>
			</td>
			<td >
				<input type="button" name="" value="1/x" />
			</td>
		</tr>
		<tr>
			<td >
				<input type="button" name="" value="1" onclick="getNumber('1')"/>
			</td>
			<td >
				<input type="button" name="" value="2" onclick="getNumber('2')"/>
			</td>
			<td >
				<input type="button" name="" value="3" onclick="getNumber('3')"/>
			</td>
			<td >
				<input type="button" name="" value="-"  onclick="getOperator('-')"/>
			</td>
			<td rowspan="2">
				<input type="button" id="equals" name="" value="="  onclick="getOperator('=')"/>
			</td>
		</tr>
		<tr>
			<td colspan="2">
				<input type="button" id="zero" name="" value="0"  onclick="getNumber('0')"/>
			</td>
			<td >
				<input type="button" name="" value="."  onclick="getNumber('.')"/>
			</td>
			<td >
				<input type="button" name="" value="+"  onclick="getOperator('+')"/>
			</td>
		</tr>
	
	</table>
	
<script type="text/javascript">
		//全局变量
		var firstNum = "";//操作符之前的
		var secondNum ="";//操作符之后
		var inputTextObj;
		var operator;//操作符
		//初始化方法，获得文本框
	
	function getNumber(num){
		/* 	 if(operator){
			 secondNum += num;
			  inputTextObj.value = firstNum  +secondNum; 
			 }else{ 
			 firstNum += num;
			  inputTextObj.value = firstNum; 
			 } */
		 firstNum += num;
		  inputTextObj = document.getElementById("num");
		inputTextObj.value = firstNum; 
		 operator = undefined;//如果有数字写入，不再纪录操作符
	}
//操作
function  getOperator(ope){
			//operator = ope;
			
			  //操作		
			switch(ope){
			
			
			  		case  '±': 
			  		// 第二个值需要添加符号
			  		 secondNum = -1 * eval(secondNum);
			  		break;
			  		case'+':
			  		firstNum = eval(firstNum +secondNum);
			  		inputTextObj.value =  firstNum+"+";
			  		firstNum +="+";
			  		break;
			  		case '-':
			  
			  		firstNum = eval(firstNum);
			  		inputTextObj.value =  firstNum+"-";
			  		firstNum+="-";
			  		break;
			  		case '*':
			  		firstNum = eval(firstNum);
			  			inputTextObj.value =  firstNum + "*";
			  		firstNum+="*";
			  		break;
			  		case '/':
			  		firstNum = eval(firstNum);
			  			inputTextObj.value =  firstNum + "/";
			  		firstNum+="/";
			  		break;
			  		case '=':
			  		firstNum = eval(firstNum);
			  		inputTextObj.value =  firstNum;
			  		break;
			  	  		default:
			  	  		alert("不支持操作");
			  		break;
			}
			
			//纪录上一次的操作符
			operator = ope;

}


function clearData(){
		firstNum = "";
		inputTextObj.value = "0";
		operator = undefined;
}

</script>


</body>
</html>
```

1. 提供input type = "text" 显示数据
2. 提供 input type ="button" 点击获取数据
3. 

---




#####4.6 DOM事件



---

#####Event 事件








