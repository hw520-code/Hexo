---
title: java之运算符、表达式和语句
date: 2020-02-07 16:33:19
tags: Java
categories: java基础
---
# 一、运算符

## 1.1、赋值运算符（“=”）------太简单不深入了
		但是还是提醒一下，左边必须是变量！！！避免0=1；的低级错误！！！
## 1.2、一元运算符
               		+/- ------正（负）号
                		！  ------ NOT，非
                		~   ------代表取补码
                		++ ------ 自增运算符
                		--   ------ 自减运算符

🌂下面补充下补码的知识（百度查的，能看懂）

在计算机系统中，数值一律用补码来表示（存储）。
主要原因：使用补码，可以将符号位和其它位统一处理；同时，减法也可按加法来处理。另外，两个用补码表示的数相加时，如果最高位（符号位）有进位，则进位被舍弃。
其中，正数的补码是它本身，而负整数的补码，将其原码除符号位外的所有位取反（0变1，1变0，符号位为1不变）后加1；
例如：求-5的补码。
-5对应正数5（00000101）→所有位取反（11111010）→加1(11111011)
所以-5的补码是11111011。

## 1.3 算数运算符不多说（+、-、*、/、%），还是太简单了！！！
## 1.4 逻辑运算符（只对布尔类型进行操作并返回布尔类型数据）
&&/& ------ 与
|| / | ------ 或
！ ------ 非

Java中&&和&都是表示与的逻辑运算符，都表示逻辑运输符and，当两边的表达式都为true的时候，整个运算结果才为true，否则为false。
&&的短路功能，当第一个表达式的值为false的时候，则不再计算第二个表达式；&则两个表达式都执行。
&可以用作位运算符，当&两边的表达式不是Boolean类型的时候，&表示按位操作。
还是举一个例子
```java
boolean b1 = 1<0 && 1/0==0;
boolean b2 = 1<0 & 1/0==0;
然后输出，会发现第一个1<0得到false不看后面的条件了
而第二个语句 在判断前面为假了以后 后面也会进行判断 但是后面是一个除0错误，所以会报错，具体参看上面的引用部分，不再多讲

```
# 二、表达式
不想多说，C语言里面接触多了，就总结一点点
##  2.1 算术表达式
a+=b； //a = a + b;
a-=b++; //a = a - b b = b + 1;
但有一说一没必要像这样 早晚把人绕死！！！
## 2.2 关系表达式（不讲！！！）
## 2.3 逻辑表达式 （不讲！！！）
## 2.4 赋值表达式 （“=”不多说）
## 2.5 表达式的类型转换
原则：
（1）占用字节较少的数据类型转换成字节数较多的数据类型；
（2）字符类型会转换成int类型；
（3）int类型会转换成float类型；
（4）若表达式中其中一个类型为double，另一个操作数也会转double；
（5）布尔类型不能转换为其它类型；

```java
public static void main(String[] args) {
		char ch = 'b';
		short a = -2;
		int b = 3;
		float f = 5.3f;
		double d = 6.28;
		System.out.print("(ch/a)-(d/f)-(a+b) = ");
		System.out.println((ch/a)-(d/f)-(a+b));
	}
	//输出 (ch/a)-(d/f)-(a+b) = -51.18490561773532

```
# 三、总结
## 3.1 &和&&以及||和|的关系（上面已经提过了 可以往上翻找找看）
## 3.2 递增递减运算符
++1 1++ --1 1–；
## 3.3 位运算
小技巧：任何数与0000 0001进行或运算后，第一位将变成1；
任何数与1111 1110进行与运算后，第一位将变成0；
然后看到一些题目：（就敲出来给大家看看）
### ①一个三目运算符的简单操作

//一个三目运算符的简单操作
```java
public class ex {
	public static void main(String[] args) {
		boolean ret = ((12345679*9)>97654321*3)?true:false; 
		System.out.println(ret);
	}
}

```
### ②生成一个随机字母

```java
public static void main(String[] args) {
		double rand = Math.random(); //值为[0,1)的随机数
		System.out.println(rand);
		char c1 = (char)(97+(int)(Math.random()*26));
		char c2 = (char)(65+(int)(Math.random()*26));
		System.out.println("小写字母："+c1);
		System.out.println("大写字母："+c2);
	}

```
### ③随机生成一个小写字母并转换为大写

```java
public static void main(String[] args) {
		int num = 97+(int)(Math.random()*26);
		char ch = (num>=97&&num<=122)?(char)(num-32):' ';
		System.out.println("转换前："+(char)num);
		System.out.println("转换后："+ch);
	}

```

