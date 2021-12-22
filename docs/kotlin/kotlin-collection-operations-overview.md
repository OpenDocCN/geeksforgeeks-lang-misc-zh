# 科特林–收集操作概述

> 原文:[https://www . geesforgeks . org/kot Lin-收集-操作-概述/](https://www.geeksforgeeks.org/kotlin-collection-operations-overview/)

Kotlin 标准库提供了对集合执行操作的广泛功能。它包括简单的操作，如获取或添加元素，也包括更复杂的操作，如搜索、排序、过滤等。

## 成员和扩展功能–

收集操作以两种**和**方式声明:

*   成员职能
*   扩展函数

### 成员职能–

它定义了集合类型所必需的操作。比如 Collection 包含检查其空性的函数**isEmpty()**；列表中包含**获取()**进行索引访问的元素，等等。

我们必须在创建自己的集合接口实现时实现成员函数。为了更容易地创建新的实现，我们可以使用科特林标准库中集合接口的骨架实现，如**抽象列表**、**抽象集**、**抽象映射**，以及它们的可变对应物。

### 扩展功能–

除了成员函数之外的所有操作都被声明为扩展函数。其中一些是过滤、转换、排序和其他收集处理功能。

### 常见操作–

通用操作可用于可变集合(读和写)和只读集合。常见操作分为以下几类:

*   转换
*   过滤
*   加减运算符
*   分组
*   正在检索集合部分
*   检索单个元素
*   排序
*   聚合操作

上面讨论的所有操作都会返回它们的结果，而不会影响集合的原始内容。例如，当我们应用过滤操作时，它会生成一个新的集合，该集合包含与过滤谓词匹配的所有元素。这些操作的结果应该存储在变量中，或者可以传递给其他函数。

**使用过滤操作的柯特林程序–**

```
fun main() {
    val str = mutableListOf("Geeks", "for", "Geeks", "A", "Computer", "Portal")

    // original collection remains same 
    str.filter { it.length > 4 }
    println("Original collection elements still unchanged $str")

    // result is stored in newStr
    val newStr = str.filter { it.length > 4 }
    println("New Collection obtains after filtering $newStr")
}
```

**输出:**

```
Original collection elements still unchanged [Geeks, for, Geeks, A, Computer, Portal]
New Collection obtains after filtering [Geeks, Geeks, Computer, Portal]

```

对于有限的收集操作，我们可以指定目标对象，它是可选的。目标应该是可变的集合，函数向其中添加其结果项，而不是在新对象中返回它们。要对目的地执行这些操作，我们可以在函数名称中使用 To 后缀符号来分隔函数，例如，使用 **filterTo()** 代替 **filter()** 。

**使用目标对象的柯特林程序–**

```
fun main() {

    val str = listOf("Geeks", "for", "Geeks", "A", "Computer", "Portal")

    //destination object
    val filterResults = mutableListOf<String>()
    str.filterTo(filterResults) { it.length > 5 }
    str.filterIndexedTo(filterResults) { index, _ -> index == 0 }

    // filterResults contains results of both operations
    println("Combined Result of both operations $filterResults")
}
```

**输出:**

```
Combined Result of both operations [Computer, Portal, Geeks]
```

如上所述，我们可以将集合操作结果传递给另一个函数，这些函数将目标集合返回，因此我们可以在函数调用的相应参数中创建它:

**在 Hashset 中存储结果的 Kotlin 程序–**

```
fun main() {
    val str = listOf("Geeks", "for", "Geeks", "A", "Computer", "Portal")

    // filter strings right into a new hash set,
    // and eliminating duplicates in the result
    val result = str.mapTo(HashSet()) { it.length }

    // print hashset
    println("Only Distinct item length return by hashset $result")
}
```

**输出:**

```
Only Distinct item length return by hashset [1, 3, 5, 6, 8]
```

## 写操作–

还有一些写操作可以在可变集合的情况下改变集合状态。这些操作包括添加、移除和更新集合中的元素。写操作在“列出特定操作”和“映射特定操作”的写操作和相应部分中列出。

对于特定的操作，有成对的函数用于对集合执行相同的操作:首先，一个函数可以就地应用操作，即在原始集合中执行操作，另一个函数将结果作为新的单独集合返回。

**例如:**在应用 **sort()** 操作时，它就地对可变集合进行排序，因此它的状态会改变，但是在 **sorted()** 操作的情况下，它会创建一个新的集合，该集合包含排序顺序中相同的元素。

**使用 sort()和 sorted()操作的 Kotlin 程序–**

```
fun main() {
    val units = mutableListOf("Ten","Hundred","Thousand","Lakh","Crore")
    // sorted() creates new collection and sort
    val sortedNumbers = units.sorted()

    println(units == sortedNumbers) // false
    // sort() sort in same collection
    units.sort()

    println(units == sortedNumbers) // true
}
```

**输出:**

```
false
true

```