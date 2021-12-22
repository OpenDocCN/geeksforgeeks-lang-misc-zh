# 类型别名与内联类

> 原文:[https://www . geesforgeks . org/type-alias-vs-inline-class/](https://www.geeksforgeeks.org/type-aliases-vs-inline-classes/)

[Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) 是一种编程语言，它将现代编程语言的所有力量都带到了安卓开发中。在本文中，我们将讨论它的两个很酷的特性，即类型别名和内联类。

## 类型别名

假设您正在创建一个项目，其中您定义了两个同名但不同包的类。在需要的时候，你需要对第二个使用全包名点类名格式。例如，您有一个名为“geek”的类，一个在“com.gfg.apps”包中，另一个在“com.gfgpractice.apps”包中，您可以使用简单导入来使用其中的一个，如果您想使用第二个，您必须使用完整的包名，如“com.gfgpractice.apps.geek”。
这里，**类型别名**进入图片，类型别名提供了一种方法来为我们复杂或太长的类名定义一个替代名称。类型别名不会引入新类型。它们与相应的底层类型相同。
在上面的场景中，我们可以做到:

```kt
typealias geek = com.gfg.apps.geek 
```

并在任何我们想用的地方使用 *geek* 这个名字，而不是“com.gfg.apps.geek”，而无需每次使用时都定义它的较长版本。
**科特林示例演示类型别名–**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// here we define a type alias named key_values
// which will take two parameters int and string
typealias Key_values = Pair<Int, String>
fun main() {
    // we are setting two games but we don't
    // have to define Pair each time while using it
    val game1 = Key_values( 1, "Cricket")
    //instead we can directly use our type alias Key_values.
    val game2 = Key_values(2, "Football")

    println(game1)
    println(game2)
}
```

**输出:**

```kt
(1, Cricket)
(2, Football)
```

## 内联类

内联类添加了类型别名的功能，这些类型别名具有基元数据类型的值域。在某些情况下，需要为特定类型创建一个包装器，这将导致在运行时进行额外的堆分配。为了解决这个问题，引入了内联类的概念。在这个概念中，类的数据被“内联”到它的用法中。
**注意:**内联类引入了一个真正的新类型，这与类型别名相反，后者只引入了一个现有类型的替代名称(别名)。
**科特林程序演示内联类–**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
interface Print {
    fun geekPrint(): String
}

inline class Value(val s: String) : Print {
    override fun geekPrint(): String = "Hello $s!"
}   

fun main() {
    val name = Value("World")
    println(name.geekPrint())
}
```

**输出:**

```kt
Hello World!
```