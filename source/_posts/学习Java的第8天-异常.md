---
title: 学习Java的第八天--异常
date: 2016-10-10 12:10:32
tags: 
		- Java
		- Java基础
---

<h1>异常</h1>

**一、异常的体系：**

| Throwable | 解释 |
| --- | --- |
|  Error （错误）|  错误一般是由于jvm或者是硬件引发的问题，<br>所以我们一般都不会通过代码去处理。|
| Exception (异常) | 异常我们一般都会通过代码去处理的。|
| 运行时异常 | 如果一个方法内部抛出了一个运行时异常，<br>那么方法上可以声明也可以不声明，<br>调用者可以以处理也可以不处理。|
| 编译时异常(非运行时异常、受检异常) | 如果一个方法内部抛出了一个编译时异常对象，<br>那么方法上就必须要声明，而且调用者也必须要处理 |

* [1]运行时异常： RuntimeException以及RuntimeException子类 都是属于运行时异常。

* [2]编译时异常： 除了运行时异常就是编译异常。

**二、异常的处理方式**
	
* 方式一：捕获处理
		
		捕获处理的格式
			
					try{
						
						可能发生异常的代码

					}catch(捕获的异常类型  变量名){
						处理异常的代码
					}
					
		
> 捕获处理要注意的细节：

			1. 如果一个try块中出现了异常的代码，经过处理之后，那么try-catch块外面的代码可以正常执行。
			2. 如果一个try块中出现了异常的代码，那么在try块中出现异常的代码后面 的语句无法执行。
			3. 一个try块后面可以跟多个catch块，也就是一个try块可以捕获多种异常的类型，但是捕获的
			异常类型必须从小到大进行捕获。

* 方式二：抛出处理(throw throws)


> 抛出处理要注意的细节：

			1. 如果一个方法内部抛出了一个编译时异常对象，那么该方法必须要声明抛出。
			2. 如果调用了一个声明抛出编译时异常的方法，那么调用者必须要处理。
			3. 如果一个方法抛出了一个异常对象，那么该方法也会马上停止（一个方法遇到了throw关键字，那么该方法就会马上停止）
			4. 在一种情况下只能抛出一种异常对象。
		
	
>throw 关键字是用于方法体之内抛出异常对象 的，throws是用于方法 声明上声明抛出异常类型的。

<h2><a id ="finally 块"></a>finally 块</h2>

* finally块的使用前提是必须要**存在try块**才能使用。

* finally块的代码在`任何情况`下都会执行的，除了`jvm退出`的情况。

* finally非常适合做`资源释放`的工作，这样子可以保证资源文件在`任何情况`下都会被释放。



**try块的三种组合方式：**


* 第一种： 比较适用于有异常要处理，但是没有资源要释放的。

		 try{

			可能发生异常的代码
	
			}catch(捕获的异常类型 变量名){
				处理异常的代码
			}

* 第二种：比较适用于既有异常要处理又要释放资源的代码。
		
		try{

			可能发生异常的代码
	
			}catch(捕获的异常类型 变量名){
				处理异常的代码
			}finally{ 
				释放资源的代码;
			}

* 第三种： 比较适用于内部抛出的是运行时异常，并且有资源要被释放。

		   try{

			可能发生异常的代码
	
			}finally{ 
				释放资源的代码;
			}

* java释放资源的代码如下：

``` java
import java.io.*;
class Demo6 
{
	public static void main(String[] args) 
	{
		FileReader fileReader = null;
		try{
			//找到目标文件
			File file = new File("f:\\a.txt");
			//建立程序与文件的数据通道
			fileReader = new FileReader(file);
			//读取文件
			char[] buf = new char[1024];
			int length = 0; 
			length = fileReader.read(buf);
			System.out.println("读取到的内容："+ new String(buf,0,length));
		}catch(IOException e){
			System.out.println("读取资源文件失败....");
		}finally{
			try{
				//关闭资源
				fileReader.close();
				System.out.println("释放资源文件成功....");
			}catch(IOException e){
				System.out.println("释放资源文件失败....");
			}
		}

	}
}
```

