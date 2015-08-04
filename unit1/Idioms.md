##[第一章](https://github.com/kymjs/KotlinDoc-cn#第一章)
---

###常用语法(Idioms)
这里是kotlin中习惯用法的一些集合。如果你还有其他的习惯用法，欢迎向我们提供pull request。  

####创建DTO(POJO’s/POCO’s)
```kotlin
data class Customer(val name: String, val email: String)
```
默认提供了以下功能的Customer类：
— getters (and setters in case of var’s) for all properties — equals()
— hashCode()
— toString()
— copy()
— component1() , component2() , ..., for all properties 

####声明一个常量  
```kotlin
val a = foo()
```

####为函数参数设置默认值  
```kotlin
fun foo(a: Int = 0, b: String = ""){ ... }
```

####列表过滤器
```kotlin
val positives = list.filter { x -> x > 0 }

//或者
val positives = list.filter { it > 0 }
```

####字符串插入
//译者注：name是一个String变量
println("他的名字是：$name")

####对象检测
```kotlin
when (x) {
  is Foo -> ...
  is Bar -> ...
  else -> ... 
}
```

####遍历一个map或list
```kotlin
//k和v可以是任何值
for ((k, v) in map) { 
  println("$k -> $v")
}
```

####使用区间(using ranges)
```kotlin
for (i in 1..100) { ... } 
for (x in 2..10) { ... }
```

####只读的map或list
```kotlin
val list = listOf("a", "b", "c")

val map = mapOf("a" to 1, "b" to 2, "c" to 3)
```

####扩展函数
```kotlin
//译者注：为String类添加spaceToCamelCase()方法，String所有子类都可以调用这个方法
fun String.spaceToCamelCase() { ... }
"Convert this to camelcase".spaceToCamelCase()
```

####创建一个单元素类(singleton)
```kotlin
object Resource {
  val name = "Name"
}
```

####空指针安全操作
```kotlin
//如果files不为空，则打印files.size，否则什么都不做
val files = File("Test").listFiles() 
println(files?.size)

//如果files为空了，则打印empty，否则打印files.size
val files = File("Test").listFiles() 
println(files?.size ?: "empty")

//如果data["email"]为空才执行'?:'后面的语句
val data = ...
val email = data["email"] ?: throw IllegalStateException("Email is missing!")

//如果不为空才执行某些操作
val data = ...
data?.let {
... //做某些操作
}
```

####使用when声明返回
```kotlin
fun transform(color: String): Int { 
  return when (color) {
    "Red" -> 0
    "Green" -> 1
    "Blue" -> 2
    else -> throw IllegalArgumentException("Invalid color param value")
  } 
}
```

####使用try...catch...块返回
```kotlin
fun test() {
  val result = try {
    count()
  } catch (e: ArithmeticException) {
    throw IllegalStateException(e) }
      // Working with result
}
```

####使用if返回值
```kotlin
fun foo(param: Int) {
  val result = if (param == 1) {
    "one"
  } else if (param == 2) { 
    "two"
  } else { 
    "three"
  } 
}
```

####单表达式函数(单语句函数)(Single-expression functions)
```kotlin
fun theAnswer() = 42

//上面的单表达式函数等价于下面的函数
fun theAnswer(): Int { 
  return 42
}

//同样的，可以结合其他常用语法，例如：
fun transform(color: String): Int = when (color) { 
  "Red" -> 0
  "Green" -> 1
  "Blue" -> 2
  else -> throw IllegalArgumentException("Invalid color param value")
}
```
