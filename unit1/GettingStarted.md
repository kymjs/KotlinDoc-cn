##[第一章](https://github.com/kymjs/KotlinDoc-cn)
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
```

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
引用或函数返回值如果可能为null值，则必须显式标记nullable。
(*译者注* ：在类型后面跟一个问号表示这个对象可能为空，跟两个感叹号表示这个类型一定不为空)
```kotlin
fun main(args: Array<String>) { 
  if (args.size() < 2) {
    print("Two integers expected")
    return
  }

  val x = parseInt(args[0])
  val y = parseInt(args[1])

  //必须做判断，因为x或y有可能为空
  if (x != null && y != null) {
    // x 和 y 在已经检测不为null时，系统会自动将其转换为非空类型
    check print(x * y)
  } 
}

/**
 * 如果str不能转为Int类型，则返回null
 */
fun parseInt(str: String): Int? { 
  // (代码略)
}
```

####7.类型检测并自动转换
is关键字的用法(类似于Java中的instanceof关键字)  
例1  
```kotlin
fun getStringLength(obj: Any): Int? {
  if (obj is String) {
    // 做过类型判断以后，obj会被系统自动转换为String类型
    return obj.length 
  }

  //在这里还有一种方法，与Java中instanceof不同，使用!is
  // if (obj !is String){
  //   // XXX
  // }

  // 这里的obj仍然是Any类型的引用
  return null
}
```

例2
```kotlin
fun getStringLength(obj: Any): Int? {
  // 在左侧obj已经被判断为String类型，所以在&&的右侧可以直接将obj当成String类型来使用
  if (obj is String && obj.length > 0) {
    return obj.length 
  }
  return null
}
```

####8.循环的使用
例1：for循环
```kotlin
fun main(args: Array<String>) { 
  for (arg in args)
    print(arg) 
}

//或者也可以
for (i in args.indices) 
  print(args[i])
```

例2：while循环
```kotlin
fun main(args: Array<String>) { 
  var i = 0
  while (i < args.size())
    print(args[i++]) 
}
```

####9.when表达式
（类似于Java中的switch）  
```kotlin
fun cases(obj: Any) { 
  when (obj) {
    1       -> print("第一项")
    "hello" -> print("这个是字符串hello")
    is Long -> print("这是一个Long类型数据")
    !is String -> print("这不是String类型的数据")
    else    -> print("else类似于Java中的default")
  }
}
```

####10.in关键字的使用
如果一个数字是在某一个区间内，可以使用in关键字  
```kotlin
//打印y次OK
if (x in 1..y-1) 
  print("OK")

//如果x不存在于array中，则输出Out
if (x !in 0..array.lastIndex) 
  print("Out")

//打印1到5
for (x in 1..5) 
  print(x)

//遍历集合(类似于Java中的for(String name : names))
for (name in names)
  println(name)

//如果names集合中包含text对象则打印yes
if (text in names)
  print("yes")
```  