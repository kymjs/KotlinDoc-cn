##[第一章](https://github.com/kymjs/KotlinDoc-cn#第一章)
---

###习惯用法(Idioms)
这里是kotlin中习惯用法的一些集合。如果你还有其他的习惯用法，欢迎向我们提供pull request。  

####创建DTO(POJO’s/POCO’s)
```kotlin
data class Customer(val name: String, val email: String)
```
提供了以下功能的Customer类：
