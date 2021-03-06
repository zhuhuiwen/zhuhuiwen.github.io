---
layout: post
title:  "js基础第一天"
categories: JavaScript
tags:  JavaScript
---

* content
{:toc}

9/27/2016 8:42:09 AM 

## 国庆复习 ##

- css盒子模型
- 浮动
- 定位

# 分类 #

## 三天基础 ##

- 变量
- 补充

### 三天目标 ###

- 掌握js基础语法

## 浏览器组成 ##

- user interface :用户界面
- redering engine   渲染引擎: 解析html、+css
- js interface 解析js




## js组成 ##

- ECMA   语法规范 5天
- DOM 操作页面上的元素  14天
- BOM 操作浏览器的一些功能 1天

## 网页组成 ##

- html  页面内容的显示，结构
- css  页面的样式      样式
- js  页面的交互       行为
	- 结构样式行为分离

## 输入输出语句 ##

1. alert() 弹出警告
2. document.write() 页面输出
3. console.log()  控制台输出
4. prompt() 输入语句
5. confirm()  确认语句
9/27/2016 10:04:02 AM 

## 注释 ##

1. 单行注释  //
2. 多行注释  /**/
3. 文档注释  /**   */
4. 注释的作用:
	- 模块的划分
	- 解释代码

## script ##

- 位置
	-  script书写位置: 推荐写到head或者</body>标签上面
	-  书写js的两种方式
		-  内联式: 直接到html文件中
		-  外联式: script标签引入一个js文件
	- `<script src=""></script>`
		- 注意
			- 如果script指定了src属性，就不要在script里面写内容
			
## 为什么使用变量 ##

1. 变量
	- 可以把变量看成存储数据的容器
2. 变量的声明和赋值[常用]
	- var num=17;//声明并且赋值
3. 注意:
	- num=19;//不声明直接赋值。不会报错，但是不推荐使用
	- var num;只声明，不赋值   undefiend
	- console.log(num)  一个变量，不声明不赋值，会报错，
		- js是一行一行往下执行，一旦发生了错误，就停止执行
			- console.log(num); console.log("1111");

## 变量的命名规范 ##

1. 命名规则(法律)
	- 必须是字母、数字、下划线、$，并且不能以数字开头
	- 不能是关键字和保留字
	- 区分大小写
2. 命名规范(道德) 
	- 有意义
	- 驼峰标志
		- 推荐使用
	- 下划线

## 定义变量时的内存表示 ##

1. 栈
	- 空间比较小，但是存取速度非常快
	- 存取基本数据类型
2. 堆
	- 空间大，存取速度比较慢  
	- 存储复杂数据类型
3. 分析内存
## js是一门弱类型语言 ##
1. js是弱类型语言，js在定义一个变量时候，不会管数据类型
2. 判断数据类型
	- `typeof(num)`
9/27/2016 11:50:21 AM 
9/27/2016 2:40:42 PM 

## 数据类型 ##

1. 简单数据类型
	- Number
	- String
	- Boolean
	- Undefiend
	- Null

2. 复杂数据类型
	- Object
	- Array
	- Date

## Number数值类型 ##

1. 进制问题
	- 二进制: 逢2进1   
	- 八进制: 逢8进1  017 8+7=15 ；8进制是0开头的
	- 十进制: 逢10进1  
	- 十六进制: 逢16进1 0xf
	- 科学计数法
		- 5e+3 //5*10的3次方
2. 浮点数的精度问题
	- var num = 0.1+0.2; num == 0.3; false
	- 注意:
		- 在js里面，计算机计算小数的时候会出现精度丢失的问题
		- 以后做计算的时候，尽量不要用小数进行计算，用整数进行计算
3. 数值的边界
	- Number.MAX_VALUE//数值的最大
	- Number.MIN_VALUE//数值的最小的整数
	- Infinity  无穷大
	- -Infinity 无穷小
4. NaN: Not a Number: 不是一个数字，但是是number类型
	- 判断一个值是不是  不是数值类型
		- isNaN(num)  
			- true   证明这个而不是数字类型
			- false  证明这个是数字类型

## String类型 ##

1. 转义字符
	- \n 换行
	- \t 制表符
	- \" 双引号
	- \' 单引号
2. 字符串的不可变性(指的是在内存中的不可变性)
	- 每一次字符串拼接，都要生成一个新的字符串
	- 所以，以后尽量不要在循环里拼接字符串，容易出现内存泄漏
	- 解决方法，用数组进行拼接
3. 拼接字符串
	- "+" 如果两边只要有一个是字符串，就是字符串拼接的公共
	- + 如果两边都是数值，就是数值相加的功能

## Boolean类型 ##

1. ECMA中所有类型的值都可以转换成布尔类型的值
2. null undefiend 等补充

# 类型转换 #

## 转换成字符串 ##

1. String(num)
2. num.toString()
3. num+" "
	-注意:
		- 数值类型蓝色 ；字符串:黑色；不热:蓝色；undefiend是灰色
		- .toString() undefiend和null来说没有这个方法

## 转换成数值类型 ##

1. Number("111")
2. parseInt(str)
	- 转换原理: 从开头读取数字，只要督导一个非数字，就结束兵返回值
3. parseFloat(str)
	- 跟parseInt一样，但是parseFloat能识别第一个小数点
	- var str = "200px";parseInt(str)   200
4. "111"-0

## 转换成布尔类型 ##

1. Boolean()
	- 能转换成false的几种情况: null、undefiend、0、“”、NaN
2. console.log(!!str)

## webstorm快捷键 ##

1. ctrl+alt+l

# 运算符 #

    2+3=  5  5   
    2+3 = 5  4
    2+2 = 4  3
    2+2 = 4  4

## 自增自建[重点] ##

	- a++ 先返回a，然后让a自增
	- ++a 先自增，再返回结果

    <script>
	    /*答案结果是  5  2  3  4*/
	    // a =22 3         5
	    var a = 1; var b = ++a + ++a; console.log(b);
	    // a = 2   1 +  3  4
	    var a = 1; var b = a++ + ++a; console.log(b);
	    // a = 2   1  2    3
	    var a = 1; var b = a++ + a++; console.log(b);
	    //  a = 3  2 2     4
	    var a = 1; var b = ++a + a++; console.log(b);
    </script>

## 一元运算符 ##

1. 逻辑运算符
	- || 对于来说，只要一个为true，就是true
	- &&，只要有一个是false，就是false
2. 对于逻辑运算符来说，仅仅是判断的时候，会转换成成布尔类型，但是返回的时候，返回的是原来的值
3. 其实|| 和 &&是短路运算符
	- 对于&&来说，只要碰到了false，就短路了
	
注意这个是原理:
	1. &&碰到false会短路，||碰到了true会短路
	2. 如果短路了，返回第一个值，否则返回第二个值
	
4. 举例
	- DOM： 兼容性判断的时候要用到
	- 另一个作用
    		var num = "abc";
    		num = num - 0;
    		num = num||0;
    		console.log(num);// 0 检测功能，提供一个默认值

## 比较运算符 ##

1. ==  比较的是内容
2. === 比较的内容和类型
9/27/2016 5:17:23 PM 

# 程序三种结构 #

## 顺序结构 ##

## 选择结构 ##

1. if else
	- 处理的逻辑比较复杂的时候
2. 三元运算符
	- 对于很简单的if  else可以用三元运算符来替代
3. switch
	- 有很多分支的时候
	- 判断的时候是===
9/27/2016 8:53:05 PM 