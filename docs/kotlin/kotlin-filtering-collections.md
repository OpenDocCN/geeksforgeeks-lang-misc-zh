# 科特林|过滤收藏

> 原文:[https://www.geeksforgeeks.org/kotlin-filtering-collections/](https://www.geeksforgeeks.org/kotlin-filtering-collections/)

在 [Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) 、*过滤*是采集处理的突出任务。过滤条件由谓词定义–lambda 函数接受一个集合元素，当给定元素匹配谓词时返回**真**，而**假**表示它不匹配谓词。

*   有一些标准库包含许多函数，允许您在一次调用中过滤集合。
*   这些函数不会改变原始集合的内容，也不可用于不可变和可变集合。
*   我们可以将其分配给一个变量，或者在过滤后链接函数来操作过滤结果。

## 通过谓词过滤–

*   基本功能是**过滤()**用于过滤。
*   用谓词调用 **filter()** 函数时，返回与谓词匹配的集合元素。
*   对于**列表**和**集合**，得到的集合也是**列表**，但是对于**地图**会返回地图。

**使用列表和地图集合过滤功能的科特林程序–**

```kt
fun main(args: Array<String>)
{
    //declaring a list of elements
    val list = listOf("geeks","for","geeks","hello","world")

    //filtering all words with length > 4
    val longerThan4 = list.filter { it.length > 4 }
    println(longerThan4)

    //declaring a map of string to integers
    val numbersMap = mapOf("key13" to 10, "key25" to 20,
        "key34" to 30, "key45" to 40, "key55" to 50 )

    //filtering the map with some predicates
    val filteredMap = numbersMap.filter { (key, value) ->
        key.endsWith("5") && value > 20}
    println(filteredMap)
}
```

**输出:**

```kt
[geeks, geeks, hello, world]
{key45=40, key55=50}

```

## 过滤器的变化()

*   如果我们想使用*元素索引或位置*进行过滤，我们必须使用**过滤器索引()**。
*   **filterIndexed()** 函数接受一个带有两个参数的谓词:**索引**和元素的**值。**
*   我们可以使用**过滤器 Not()** 按照**负条件**过滤集合。

**使用 filterIndexed()和 filterNot()函数的 Kotlin 程序–**

```kt
fun main(args: Array<String>) {
    val words = listOf("geek","for","geeks","all","world")

    //filtering a list by : words having length < 6 and index != 0
    val filteredIndex = words.filterIndexed { index, s ->
        (index != 0) && (s.length < 6)  }

    //filtering words having length >=3 using filterNot
    val filteredNot = words.filterNot { it.length <= 3 }

    println(filteredIndex)
    println(filteredNot)
}
```

**输出:**

```kt
[for, geeks, all, world]
[geek, geeks, world]

```

## 分区–

还有另一个过滤功能 **partition()** 通过谓词过滤一个集合，将所有与谓词不匹配的元素分离出来，放在不同的列表中。
基本上返回**列表**的**对**:第一个列表包含匹配谓词的元素，第二个列表包含原始集合中所有不匹配谓词的元素。

**使用分区的柯特林程序–**

```kt
fun main(args: Array<String>) {

    val words = listOf("geek","for","geeks","hello","world")

    //partitioning the words by length > 4 and length <= 4
    val (first, second) = words.partition { it.length > 4 }

    println(first)
    println(second)
}
```

**输出:**

```kt
[geeks, hello, world]
[geek, for]

```

## 测试谓词–

针对集合元素测试谓词的一些函数如下:

*   **any()** :如果*至少有一个元素*与给定的谓词匹配，则返回 **true** 。
*   **none()** :如果*没有一个元素*与给定的谓词匹配，则返回 **true** 。
*   **all()** :如果集合中的*所有元素*都匹配给定的谓词，则返回 **true** 。

**注意:** **all()** 在空集合上用任何有效谓词调用时返回 **true** 。这就是所谓的**空洞的真相**。
我们可以使用 **any()** 和 **none()** 不带谓词，它只是检查集合的**是否为空**，即 **any()** 如果集合有元素则返回 **true** ，如果集合为空则返回**false**；**无()**与任何()正好相反。

**使用任意()、无()和所有()函数的柯特林程序–**

```kt
fun main(args: Array<String>) {
    val words = listOf("geeks","for","geeeks","helo","world")

    //checking if atleast one word ends with s or not
    println("Any element matches? "+words.any { it.endsWith("s") })

    //checking if no word ends with a or not
    println("No element matches? "+words.none { it.endsWith("a") })

    println("All element match? "+words.all { it.endsWith("d") })
    //checking if all words end with d or not

    //when predicate is empty, it checks for emptiness
    println(words.any())
    println(words.none())

    //all function on an empty list
    println(emptyList<Int>().all { it > 5 })   // vacuous truth

    val empty = emptyList<String>()

    //any function on an empty list returns false
    println(empty.any())
    //none function on an empty list returns true
    println(empty.none())
}
```

**输出:**

```kt
Any element matches? true
No element matches? true
All element match? false
true
false
true
false
true

```