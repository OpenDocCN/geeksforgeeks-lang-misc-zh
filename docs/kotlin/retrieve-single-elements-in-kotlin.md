# 检索柯特林中的单个元素

> 原文:[https://www . geesforgeks . org/retrieve-single-elements-in-kot Lin/](https://www.geeksforgeeks.org/retrieve-single-elements-in-kotlin/)

[科特林](https://www.geeksforgeeks.org/introduction-to-kotlin/)集合允许针对不同条件检索单个元素。这完全取决于使用哪种集合来存储数据。集合的元素可以通过位置、条件、随机化以及列表中该元素的存在来检索。

## 按位置检索–

**element at(index):–**element at()获取元素的索引，并从列表中检索它。列表的索引从 0 开始，一直到 n-1，其中 n 是列表中的元素数。这是检索元素的最简单和最容易的方法，并且只有在预先知道所需元素的位置时才是首选的。
T3【科特林程序的使用元素 At()方法–T5】

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    val list=listOf("GeeksforGeeks","A","Computer","Science","Portal")
    // we know the place of GeeksforGeeks thus we use
    //elementAt() method
    println(list.elementAt(0))
}
```

**输出:**

```
GeeksforGeeks
```

从列表中检索一个元素有很多方法，但是为了避免在检索不存在的元素时出现异常，我们应该使用安全的方法。其中两个方法是:
**elementatoreless(index){ lambda expression }:–**它是对 elementAt()的加法，在找不到索引时执行 lambda expression。
**elementatornal(索引):–**它是对 elementAt()的加法，当找不到索引时返回 Null。
**使用安全转换检索元素的科特林程序–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    val list=listOf("GeeksforGeeks","A","Computer","Science","Portal")
    // we are trying to access the elements out of bounds
    //one will give out null output and other will execute
    //print statement
    println(list.elementAtOrNull(5))
    println(list.elementAtOrElse(5){"Element index not found"})
}
```

**输出:**

```
null
Element index not found
```

我们也可以通过以下两种方法从列表中检索第一个和最后一个元素–
**first():–**用于从列表中检索第一个元素，即索引为 0。
**last():–**用于检索列表的最后一个元素，即索引 n-1，其中 n 是列表的大小。
**使用 first()和 last()方法的 Kotlin 程序–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    val list=listOf("GeeksforGeeks","A","Computer","Science","Portal")
    // accessing the first element
    println(list.first())
    // accessing the last element
    println(list.last())
}
```

**输出:**

```
GeeksforGeeks
Portal
```

## 按条件检索–

使用 first()和 last()方法，我们可以检索匹配给定谓词的元素。

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    val numbers = listOf("Geeks","for","Geek","A","Computer","Science","Portal")
    // retrieve the first element having string length > 5
    println(numbers.first { it.length > 5 })
    // retrieve the last element start with "G"
    println(numbers.last { it.startsWith("G") })
}
```

**输出:**

```
Computer
Geek
```

如果没有找到与谓词匹配的元素，这两个函数都会抛出异常。为了避免异常，我们使用*first or ull()*和*lastorull()*，如果没有找到匹配的元素，它们将返回 **null** 。

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    val numbers = listOf("Geeks","for","Geek","A","Computer","Science","Portal")
    // retrieve the first element having string length > 5
    println(numbers.firstOrNull { it.length > 9 })
    // retrieve the last element start with "G"
    println(numbers.lastOrNull { it.startsWith("B") })
}
```

**输出:**

```
null
null
```

## 随机检索–

如果我们想从列表中检索任意元素，我们可以使用 *random()* 函数。
**random():–**它从集合中返回一个随机元素。
**示例:–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    val strings = listOf("Geeks","for","Geek","A","Computer","Science","Portal")
    //Example of random outputs of letters in list new each time
    println(strings.random())
}
```

**输出:**

```
Computer (output can be same or different)
```

## 检查存在–

**包含(元素):–**用于检查列表中是否有元素。如果元素存在，则返回 true，否则返回 false。
**包含全部(元素[]):–**用于检查所有元素是否在列表中。如果所有元素都在那里，则返回 true，否则返回 false。关键字:–中的
**用于检查所有元素是否在列表中。如果元素存在，则返回真，否则返回假。
**isEmpty():–**用于检查列表是否为空。如果元素不在列表中，则返回 true，否则返回 false。
**不是空的():–**用于检查列表是否为空。如果元素在列表中，则返回 true，否则返回 false。
**检查列表中字符串存在的柯特林程序–**** 

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    val list=listOf("Geeks","for","Geek","A","Computer","Science","Portal")
    //checking the string is in list or not
    println(list.contains("For"))
    println(list.containsAll(listOf("A", "Computer")))
    println(list.isEmpty())
    println(list.isNotEmpty())
}
```

**输出:**

```
false
true
false
true
```