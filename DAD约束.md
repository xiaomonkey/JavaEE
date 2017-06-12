#DTD

#####1.约束介绍

- xml没有预定义
- 约束，规定xml怎么编写
- struts   &lt;action name="" class = ""&gt;
- spring   &lt; bean id ="" class = ""&gt;
- javaweb &lt;servlet&gt; &lt;servlet-name&gt;
- 约束的重点：可以通过约束文件编写规定的xml文件
- 

#####2.约束的分类

- DTD 约束，老版约束。例如：hibernate DTD约束
- Schema 约束，新版约束 例如：javaweb、spring等
- 

#####3.DTD约束语法

- 文档关联：xml文件中如何使用dtd约束
- 语法：元素、属性、实体、定义（约束中的内容）
- DTD文件扩展名：＊.dtd
- DTD提供3种文档关联：内部关联、外部关联、公共关联
- 内部关联：将dtd内容编写在xml文件中
- 内部关联：&lt;!DOCTYPE 根标签[语法内容]&gt;
- 外部关联：将dtd内容编写在dtd文件中，并存放在本地（操作系统）
- 外部关联：&lt;!DOCTYPE 跟标签 SYSTEM "xxx.dtd"&gt;
- 公共关联：将dtd文件写在dtd文件中，提供路径url存放网上（框架）
- 公共关联：&lt;!DOCTYPE 跟标签 PUBLIC "名称" "位置"&gt;
- 

#####DTD元素

&lt;!ELEMENT 元素名称 元素内容声明&gt; 要点：包含符号和数据类型两部分


元素
- 符号：？－－>0或1
- * -->  >=0  0以上
- + -->  >=1  至少有1个
- () 分组
- ｜ 选择
- 类型：＃PCDATA  (#PCDATA) 用于描述提示字符
- EMPTY  标签体为空
- 

属性(attribute):

- 语法： <! ATTLIST 元素名称 属性类型 约束 属性名称 约束 属性名称 约束 ......>
- 一个标签可以有多个属性<xx yy ="" zz = "">
- 属性类型：

header 1 | header 2
---|---
CDATA | 值为字符串数据（character data）
ID | 值为唯一的id
(en1｜en2｜..) | 此值为枚举列表中的一个值

- 约束
- 

约束 |
---|---
#REQUIRED | 必须填写的内容
#IMPLIED | 可选
#FIXED value | 固定值
defalultvalue | 默认值

#### 实体

- 转译字符 &nbsp；
- 分类：

（1）内部实体：

（2）外部实体：

（3）引用实体：将实体定义在dtd中，在xml中使用

（4）参数实体：

####引用实体
 
 - 引用实体定义：在DTD中定义
 
<! ENTITY 实体名 "实体内容">
- 使用：在xml中使用 &名称； 
- 注意：新版浏览器DTD引用实体支持力度不大，必须使用内部关联DTD使用。
- 

####参数实体

- 将DTD内容抽取，形成 变量，在DTD其它地方可以使用。
- 









