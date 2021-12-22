# 科特林地图:mapOf()

> 哎哎哎:# t0]https://www . geeksforgeeks . org/kot Lin-map of/

[科特林](https://www.geeksforgeeks.org/introduction-to-kotlin/)地图是一个包含成对物体的集合。Map 以由一个键和值组成的对的形式保存数据。映射键是唯一的，并且映射只为每个键保存一个值。
科特林区分*不可变*和*可变*地图。用 **mapOf()** 创建的不可变映射意味着这些是只读的，而用**mutalemapof()**创建的可变映射意味着我们可以同时执行读写。
**语法:**

```kt
fun <K, V> mapOf(vararg pairs: Pair<K, V>): Map<K, V> 
```

*   该对的第一个值是**键**，第二个值是对应键的**值**。
*   如果多个对具有相同的键，则 map 将返回最后一个对的值。
*   地图条目以指定的顺序遍历。

**mapOf()的 Kotlin 程序**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>)
{
    //declaring a map of integer to string
    val map = mapOf(1 to "Geeks", 2 to "for" , 3 to "Geeks")
    //printing the map
    println( map)
}
```

**输出:**

```kt
{1=Geeks, 2=for, 3=Geeks}
```

### 映射键、值和条目–

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>)
{
    //declaring a map of integer to string
    val map = mapOf(1 to "One", 2 to "Two" , 3 to "Three", 4 to "Four")

    println("Map Entries : "+map)

    println("Map Keys: "+map.keys )

    println("Map Values: "+map.values )
}
```

**输出:**

```kt
Map Entries : {1=One, 2=Two, 3=Three, 4=Four}
Map Keys: [1, 2, 3, 4]
Map Values: [One, Two, Three, Four] 
```

### 地图尺寸–

我们可以用两种方法来确定地图的大小。使用地图的**大小**属性并使用**计数()**方法。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main() {

    val ranks = mapOf(1 to "India",2 to "Australia",3 to "England",4 to "Africa")
    //method 1
    println("The size of the map is: "+ranks.size)
    //method 2
    println("The size of the map is: "+ranks.count())
}
```

**输出:**

```kt
The size of the map is: 4
The size of the map is: 4 
```

### 空地图–

我们可以使用 mapOf()
**示例 2 中的 mapOf()** 创建一个空的可序列化地图

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>)
{
    //here we have created an empty map using mapOf()
    val map1 = mapOf<String , Int>()

    println("Entries: " + map1.entries)  //entries of map

    println("Keys:" + map1.keys)  //keys of map

    println("Values:" + map1.values)  //values of map

}
```

**输出:**

```kt
Entries: []
Keys:[]
Values:[] 
```

### 获取地图的值–

我们可以使用下面程序中讨论的不同方法从地图中检索值。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main() {

    val ranks = mapOf(1 to "India",2 to "Australia",3 to "England",4 to "Africa")

    //method 1
    println("Team having rank #1 is: "+ranks[1])
    //method 2
    println("Team having rank #3 is: "+ranks.getValue(3))
    //method 3
    println("Team having rank #4 is: "+ranks.getOrDefault(4, 0))
    // method  4
    val team = ranks.getOrElse(2 ,{ 0 })
    println(team)
}
```

**输出:**

```kt
Team having rank #1 is: India
Team having rank #3 is: England
Team having rank #4 is: Africa
Australia
```

### 映射包含键或值–

我们可以分别使用 containsKey()和 containsValue()方法来确定一个映射包含一个键或值。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main() {
    val colorsTopToBottom = mapOf("red" to 1, "orange" to 2, "yellow" to 3,
        "green" to 4 , "blue" to 5, "indigo" to 6, "violet" to 7)
    var color = "yellow"
    if (colorsTopToBottom.containsKey(color)) {
        println("Yes, it contains color $color")
    } else {
        println("No, it does not contain color $color")
    }
    val value = 8
    if (colorsTopToBottom.containsValue(value)) {
        println("Yes, it contains value $value")
    } else {
        println("No, it does not contain value $value")
    }
}
```

**输出:**

```kt
Yes, it contains color yellow
No, it does not contain value 8 
```

### 两个值和同一个键–

如果两个**值**具有相同的**关键值**，则地图将包含这些数字的最后一个**值**。
**mapOf()示例 3**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>)
{
    //lets make two values with same key
    val map = mapOf(1 to "geeks1",2 to "for" , 1 to "geeks2")
    // return the map entries
    println("Entries of map : " + map.entries)
}
```

**输出:**

```kt
Entries of map : [1=geeks2, 2=for]
```

**说明:**
这里键值 **1** 已经初始化了两个值:**极客 1 和极客 2** ，但是我们知道 *mapOf()* *对于一个关键项*只能有一个值，因此最后一个值只由地图存储，**极客 1** 被淘汰。