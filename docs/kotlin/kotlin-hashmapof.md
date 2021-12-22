# 科特林哈希 MapOf()

> 哎哎哎:# t0]https://www . geeksforgeeks . org/kot Lin-hashmapof/

在 [Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) 中， *hashMapOf()* 用于在 Kotlin 的数据结构中创建哈希映射。HashMap 是一个存储 HashMap 的类，为了初始化它的对象，我们使用 hashMapOf()。hashMapOf()是 HashMap 类的一个方法，返回 HashMap 的一个实例。它以键值对作为初始化参数，该参数是可选的。

**语法:**

```kt
HashMap hashMapOf(vararg pairs: Pair)  
```

**参数:**
创建空 hashmap 实例时可以为空。否则，它将键值对作为参数。
**Return:**
它根据 hashMapOf()方法中传递的参数返回 kotlin 中 HashMap 类的一个实例。
**哈希映射的初始化:**
哈希映射是通过将 hashMapOf()方法内部的键值对作为参数向上写来初始化的。

**示例:**
在这个示例中，HashMap 的实例化是通过使用 hashMapOf()和在其中传递的参数来完成的。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array) {
    var hashmap:HashMap = hashMapOf(1 to "Geeks", 2 to "For", 3 to "Geeks")
    for (i in hashmap.keys) {
        println("Key = ${i}, value = ${hashmap[i]}")  
    } 
}
```