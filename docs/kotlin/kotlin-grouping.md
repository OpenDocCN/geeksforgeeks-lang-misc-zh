# 科特林分组

> 原文:[https://www.geeksforgeeks.org/kotlin-grouping/](https://www.geeksforgeeks.org/kotlin-grouping/)

Kotlin 标准库在扩展函数的帮助下帮助对集合元素进行分组。分组意味着按类别收集项目。这里，我们有一个 **groupBy()** 函数，它接受 lambda 函数并返回一个映射。在这个映射中，每个键都是 lambda 的结果，对应的值是元素列表。
我们也可以使用带有第二个 lambda 表达式的 **groupBy()** 函数，也叫值变换函数。如果我们使用两个 lambda 函数，那么产生的 **keySelector** 的键被映射到值转换函数的结果，而不是原始元素。

**使用 groupBy()函数演示的 Kotlin 程序–**

```kt
fun main(args: Array<String>) {
    val fruits = listOf("apple", "apricot", "banana",
        "cherries", "berries", "cucumber")
    println(fruits.groupBy { it.first().toUpperCase() })
    println(fruits.groupBy(keySelector = { it.first() },
        valueTransform = { it.toUpperCase() }))
}
```

**输出:**

```kt
{A=[apple, apricot], B=[banana, berries], C=[cherries, cucumber]}
{a=[APPLE, APRICOT], b=[BANANA, BERRIES], c=[CHERRIES, CUCUMBER]}

```

如果我们想对组元素应用一些操作，那么可以借助 **groupingBy()** 函数一次对所有组应用该函数来完成。将返回分组类型的实例。

我们可以对组执行以下操作:

*   **eachcount():** 统计各组的项目。
*   **fold()和 reduce():** 分别对每组执行这些操作并返回结果。
*   **aggregate():** 这是一种通用的分组方式，即随后对每个组中的所有元素应用特定的操作并返回结果。因此，它用于实现自定义操作。

**演示 groupingBy()功能的 Kotlin 程序–**

```kt
fun main(args: Array<String>) {
    val fruits = listOf("apple", "apricot", "banana",
        "cherries", "berries", "cucumber")
    println(fruits.groupingBy { it.first() }.eachCount())
}
```

**输出:**

```kt
{a=2, b=2, c=2}

```