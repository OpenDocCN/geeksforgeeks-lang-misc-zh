# 科特林系列订购

> 原文:[https://www.geeksforgeeks.org/kotlin-collections-ordering/](https://www.geeksforgeeks.org/kotlin-collections-ordering/)

在某些集合中，元素的顺序很重要。如果你拿列表来说，如果两个列表有相同的元素，但排序不同，那么它们就永远不会相等。在 Kotlin 中，有不同的元素排序方式。
大多数内置类型具有可比性:
-数值类型遵循数值顺序:1 大于 0；-2.8f 大于-6f，依此类推。
-Char 和 String 使用字典顺序:p 大于 a；天空比空气大。
对于自定义类型，科特林定义了不同类型的订单。它们可以描述如下:

## 自然顺序

它是为所有继承自*可比*接口的类型定义的。要为任何类型定义此顺序，应将其作为*可比*的继承者。这可以使用 *compareTo()* 函数来完成，该函数接受相同类型的其他元素，并以整数值的形式返回更大的值。基于这个整数值，我们可以确定哪个对象更大。
-正值表示接收器对象大于
-负值表示接收器<参数
-零表示两个对象相等。
下面是一个可以用来订购由大部分和小部分组成的物品的类。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
class Items(val big: Int, val small: Int): Comparable {
    override fun compareTo(other: Items): Int {
        if (this.big != other.big) {
            return this.big - other.big
        } else if (this.small != other.small) {
            return this.small - other.small
        } else return 0
    }
}
?fun main() {   
    println(Items(1, 2) > Items(1, 3))
    println(Items(2, 0) > Items(1, 5))
}
```

基本功能有*排序()和*排序。它们以按升序和降序排序的对象集合的形式给出结果。这些可以应用于*可比*事件
的集合

## 定制订购

它们允许您订购任何类型的实例。这对于定义通常不可比较的对象的顺序特别有用。
为了创建自定义订单，我们创建了一个包含*比较()*功能的*比较器*。它采用两个实例，并将它们进行比较，给出整数值作为输出。这个结果也类似于上面的方法。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
val lengthComparator = Comparator { str1: String,
                       str2: String -> str1.length - str2.length }
println(listOf("aaa", "bb", "c").sortedWith(lengthComparator))
```

这里我们用长度来比较，而不是规定的字典顺序。
*比较器*也可以使用标准库中的 *compareBy()* 来定义。该函数采用一个 lambda 函数，该函数产生一个用于比较的值，并将自定义顺序定义为产生的值的自然顺序。
使用*对比(*)、

```kt
println(listOf("aaa", "bb", "c").sortedWith(compareBy { it.length }))
```

基本功能有 *sortedBy()* 和 *sortedByDescending()* 。他们使用定义的选择器函数将集合元素映射到*可比*值，并按照值的自然顺序对集合进行排序。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
val numbers = listOf("one", "two", "three", "four")
val sortedNumbers = numbers.sortedBy { it.length }
println("Sorted by length ascending: $sortedNumbers")
val sortedByLast = numbers.sortedByDescending { it.last() }
println("Sorted by the last letter descending: $sortedByLast")
```

使用 *sortedWith()* ，可以写成:

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
val numbers = listOf("one", "two", "three", "four")
println("Sorted by length ascending: ${numbers.sortedWith(compareBy { it.length }
```

## 随机位

使用*洗牌()*以随机顺序给出包含集合元素的新列表的函数。不需要参数或带有随机对象。

```kt
val numbers = listOf("one", "two", "three", "four")
println(numbers.shuffled())
```

## 倒序

可以使用*反转()*来反转元素。它返回一个新的集合，其中给出了与原始集合相反的集合。由于这个结果基本上是一个副本，所以原件不会被更改。另一个版本是 *asReversed()* ，它提供了反向视图而不是副本，因此是轻量级的。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
val numbers = listOf("one", "two", "three", "four")
println(numbers.reversed())
val numbers = listOf("one", "two", "three", "four")
val reversedNumbers = numbers.asReversed()
println(reversedNumbers)
```