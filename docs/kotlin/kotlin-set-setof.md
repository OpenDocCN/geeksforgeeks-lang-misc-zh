# 科特林集:setf()

> 原文:[https://www.geeksforgeeks.org/kotlin-set-setof/](https://www.geeksforgeeks.org/kotlin-set-setof/)

[Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) Set 接口是一个通用的无序元素集合，不包含重复的元素。Kotlin 支持**两种**类型的集合可变和不可变。
**setOf()** 为*不可变*表示只支持只读功能，**可变**为*可变*表示支持读写两种功能。

**语法:**

```kt
fun <T> setOf( vararg elements: T): Set<T>
```

**描述:**

*   这个函数返回给定元素的一个新的只读集合。
*   根据元素的存储方式，对其进行迭代。

**科特林程序的** ***setOf()*** **功能:**

## 我的锅

```kt
fun main(args: Array<String>)
{
    //declaring a set of strings
    val seta = setOf("Geeks" , "for", "geeks")
    //declaring a set of characters
    val setb = setOf( "G" , "f" , "g" )
    //declaring a set of integers
    val setc = setOf( 1 ,2 , 3 , 4 )

    //traversing through a set of strings
    for(item in seta)
        print( item )
    println()
    //traversing through a set of characters
    for(item in setb)
        print( item )
    println()
    //traversing through a set of integers
    for(item in setc)
        print( "$item ")
}
```