# Kotlin mutalesetof()方法

> 原文:[https://www.geeksforgeeks.org/kotlin-mutablesetof-method/](https://www.geeksforgeeks.org/kotlin-mutablesetof-method/)

[Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) Set 接口是一个通用的无序元素集合，不包含重复的元素。Kotlin 支持**两种**类型的集合可变和不可变。
**setOf()** 为*不可变*表示只支持只读功能，**可变**为*可变*表示支持读写两种功能。

**语法:**

```
fun <T> mutableSetOf( vararg elements: T): MutableSet<T>
```

**描述:**

*   这个函数返回一组给定的元素，这些元素可以被读取和写入。
*   返回的集合保留元素迭代顺序。

**科特林程序的*****mutalesetof()*****功能:**

## 我的锅

```
fun main(args: Array<String>)
{
    //declaring a mutable set of integers
    val mutableSetA = mutableSetOf<Int>( 1 , 2 , 3 , 4 , 3);
    println(mutableSetA)

    //declaring a mutable set of strings
    val mutableSetB = mutableSetOf<String>("Geeks","for" , "geeks");
    println(mutableSetB)

    //declaring an empty mutable set of integers
    val mutableSetC = mutableSetOf<Int>()
    println(mutableSetC)
}
```