# 科特林|取回收集零件

> 原文:[https://www . geeksforgeeks . org/kot Lin-retrieve-collection-parts/](https://www.geeksforgeeks.org/kotlin-retrieve-collection-parts/)

[科特林](https://www.geeksforgeeks.org/introduction-to-kotlin/)提供了检索采集零件的扩展功能。类外定义的成员函数称为[扩展函数](https://www.geeksforgeeks.org/kotlin-extension-function/)。这些扩展功能可以提供多种方式从列表中选择不同的项目。
四大扩展功能是:

*   薄片
*   拿走和放下
*   分块的
*   有窗的

## 薄片

切片函数的工作方式和其他语言一样，它返回一个带有给定索引的项目列表。这些索引可以作为范围或整数值传递。
**科特林示例演示切片–**

```
fun main(args: Array<String>) {
    val fruits = listOf("apple", "banana", "cherries",
        "dragon_fruit", "egg_fruit", "fig")
    println(fruits.slice(1..4))
    println(fruits.slice(0..4 step 2))
    println(fruits.slice(setOf(1, 2, 4)))
}
```

**输出:**

```
[banana, cherries, dragon_fruit, egg_fruit]
[apple, cherries, egg_fruit]
[banana, cherries, egg_fruit]

```

## 拿走和放下

顾名思义 *take()* 功能可以从一开始就取指定数量的项目。如果我们想从最后抓取物品，我们可以调用 *takeLast()* 函数。
同样， *drop()* 函数从开始处获取除指定数量项目外的所有项目， *dropLast()* 从最后处获取除指定数量项目外的所有项目。

**演示取放的 Kotlin 示例–**

```
fun main(args: Array<String>) {
    val fruits = listOf("apple", "banana", "cherries",
        "dragon_fruit", "egg_fruit", "fig")
    println(fruits.take(3))
    println(fruits.takeLast(3))
    println(fruits.drop(4))
    println(fruits.dropLast(4))
}
```

**输出:**

```
[apple, banana, cherries]
[dragon_fruit, egg_fruit, fig]
[egg_fruit, fig]
[apple, banana]

```

取和放中有四个函数，我们可以使用谓词来定义取和放的项目数。

**科特林计划–**

```
fun main(args: Array<String>) {
    val fruits = listOf("apple", "banana", "cherries",
        "dragon_fruit", "egg_fruit", "fig")

    //takeWhile() takes the items upto but 
    // excluding the first one not matching the predicate.
    println(fruits.takeWhile{!it.startsWith("d")})

    //takeLastWhile() takes a range of items 
    // matching the predicate from the end.
    println(fruits.takeLastWhile{it != "cherries"})

    //dropWhile() returns the items from first
    // one not matching the predicate to the end.
    println(fruits.dropWhile{it.length == 5})

    //dropWhileLast() returns element from the 
    // beginning to the last one not matching the predicate.
    println(fruits.dropLastWhile{it.contains("i")})
}
```

**输出:**

```
[apple, banana, cherries]
[dragon_fruit, egg_fruit, fig]
[banana, cherries, dragon_fruit, egg_fruit, fig]
[apple, banana]

```

## 分块的

分块是一种功能，通过该功能，列表的各个部分被分解，然后组合成指定的块大小。chunk()函数接受单个参数，并返回该块大小的列表。

我们还可以对返回的块应用转换。为此，我们在调用 chunked()时将转换作为 lambda 函数提供。当使用转换调用 **chunked()** 时，块是短命列表，应该在 lambda 表达式中用于其他目的。

**使用 chunk()函数的 Kotlin 程序–**

```
fun main(args: Array<String>) {
    val fruits = listOf("apple", "banana", "cherries",
        "dragon_fruit", "egg_fruit", "fig")
    // chunks into list size of three
    println(fruits.chunked(3))

    // lambda function to sum the elements
    val numbers = (0..11).toList()
    println(numbers.chunked(3) { it.sum() })
}
```

**输出:**

```
[[apple, banana, cherries], [dragon_fruit, egg_fruit, fig]]
[3, 12, 21, 30]

```

## 有窗的

*windowed()* 函数可以获取给定大小的所有可能的项目集合范围。它返回一个元素范围列表，您可以使用特定大小的滑动窗口在集合中看到该列表。
可选两个参数:
**步:**每个窗口第一项之间的距离。默认情况下，该值为 1，因此结果包含从所有元素开始的窗口。
**partialWindows:** 如果为 true，则包括留在末尾的较小尺寸的窗口。

**演示窗口()功能的 Kotlin 程序–**

```
fun main(args: Array<String>) {
    val fruits = listOf("apple", "banana", "cherries","orange")
    println(fruits.windowed(3))
    println(fruits.windowed(3, step = 2, partialWindows = true))
}
```

**输出:**

```
[[apple, banana, cherries], [banana, cherries, orange]]
[[apple, banana, cherries], [cherries, orange]]

```

有一个**zipcwitnext()**函数构建两个元素窗口，也可以用一个变换来调用。
**科特林程序演示 zipcwitnext()–**

```
fun main(args: Array<String>) {
    val fruits = listOf("apple", "banana", "cherries",
        "dragon_fruit", "egg_fruit", "fig")
    println(fruits.zipWithNext())
}
```

**输出:**

```
[(apple, banana), (banana, cherries), (cherries, dragon_fruit), 
(dragon_fruit, egg_fruit), (egg_fruit, fig)]

```