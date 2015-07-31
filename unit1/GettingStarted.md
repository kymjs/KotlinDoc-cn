##开始
---

###基础语法  
*译者注* ：在阅读以下内容前，你可能需要先了解一些Kotlin语言的特性：在语句的行尾可以不用加分号(加上也不会错)，声明一个方法需要加上fun关键字，如果函数是重载父类的方法，还必须要加上override关键字，方法的参数是先写形参名后跟冒号再写形参类型。  

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

####3.定义变量  
只能赋值一次的变量(类似Java中final修饰的变量)
```kotlin
val a: Int = 1
val b = 1 // 系统自动推断变量类型为Int
val c: Int // 如果不在声明时初始化则必须提供变量类型
c = 1 // 明确赋值
```
可以多次赋值的变量
```kotlin
var x = 5 // 系统自动推断变量类型为Int
x += 1

####4.使用泛型Array<String>
```kotlin
fun main(args: Array<String>) {
  if (args.size() == 0) return
  print("First argument: ${args[0]}") 
}
```

####5.条件语句
```kotlin
fun max(a: Int, b: Int): Int { 
  if (a > b)
    return a 
  else
    return b 
}

//或者也可以把if语句作为省略方法体的方法
fun max(a: Int, b: Int) = if (a > b) a else b
```

####6.使用nullable值以及空值检测
