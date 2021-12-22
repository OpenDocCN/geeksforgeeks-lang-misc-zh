# Kotlin mutableMapOf()

> 原文:[https://www.geeksforgeeks.org/kotlin-mutablemapof/](https://www.geeksforgeeks.org/kotlin-mutablemapof/)

[Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/)MultipleMap 是一个集合框架的接口，包含键和值形式的对象。它允许用户有效地检索对应于每个键的值。键和值可以是不同的对，如< Int、字符串>、< Char、字符串>等。
为了使用可变地图界面，我们需要使用如下所示的功能

```
mutableMapOf() or mutableMapOf <K, V>()
```

用于声明可变映射接口

```
interface MutableMap<K, V> : Map<K, V> (source)
```

#### 包含条目、键、值的可变函数示例。

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    val items = mutableMapOf("Box" to 12, "Books" to 18, "Table" to 13)

    println("Entries: " + items.entries)       //Printing Entries
    println("Keys:" + items.keys)              //Printing Keys
    println("Values:" + items.values)          //Printing Values
}
```