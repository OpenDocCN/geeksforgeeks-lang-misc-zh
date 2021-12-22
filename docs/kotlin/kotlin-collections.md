# 科特林收藏品

> 原文:[https://www.geeksforgeeks.org/kotlin-collections/](https://www.geeksforgeeks.org/kotlin-collections/)

与 [Java Collections](https://www.geeksforgeeks.org/collections-in-java-2/) 类似，Kotlin 也引入了集合的概念。一个**集合**通常包含多个相同类型的对象，集合中的这些对象被称为*元素*或*项目*。Kotlin 标准库提供了一套丰富的工具来管理**集合**。

## **收藏类型**

在科特林，收藏品分为两种形式。

1.  **immutable set**
2.  **immutable set**

### **1。不可变集合**

这意味着它只支持只读功能，不能修改其元素。不可变集合及其对应的方法有:

*   **list** -list Of () and list of < t > ()

**集合**

*   **map** -map Of ()

**列表**–这是一个有序集合，我们可以通过使用索引(定义每个元素位置的整数)来访问*元素*或*项目*。元素可以在列表中重复任意次。我们不能在不可变列表中执行添加或删除操作。**科特林程序演示不可变列表:**

## 科特林

```kt
// An example for immutable list
fun main(args: Array<String>) {
    val immutableList = listOf("Mahipal","Nikhil","Rahul")
    // gives compile time error
    // immutableList.add = "Praveen"
    for(item in immutableList){
        println(item)
    }
}
```