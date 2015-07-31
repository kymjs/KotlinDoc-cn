##开始
---

###基础语法  

####1.定义包声明  
包声明需要写在源文件的顶部，例如：
```java
package my.demo 

import java.util.* 

// ...
```
kotlin源文件不需要相匹配的目录和包，源文件可以放在任何文件目录。
*译者注* ：但是我们在写Android的Activity等类时，清单文件中的声明，必须与实际包路径相匹配  

####2.定义函数方法  
*译者注* ：Kotlin语言声明一个方法需要加上fun关键字，如果函数是重载父类的方法，还必须要加上override关键字。  

例1：方法包含两个Int参数并返回Int类型值
```kotlin
fun sum(a: Int, b: Int): Int { 
	return a + b
}
```

例2：方法体只有一条语句，并且自动推测返回类型
```kotlin
fun sum(a: Int, b: Int) = a + b
```

例3：如果方法是一个public的，则必须明确写出返回类型
```kotlin
public fun sum(a: Int, b: Int): Int = a + b
```

例4：返回一个没有意义的值(类似Java中的void)
```kotlin
fun printSum(a: Int, b: Int): Unit { 
	print(a + b)
}

// 如果是返回Unit类型，则可以省略(对于public方法也是这样)：
public fun printSum(a: Int, b: Int) { 
	print(a + b)
}
```
