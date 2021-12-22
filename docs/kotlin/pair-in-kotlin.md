# 科特林配对

> 原文:[https://www.geeksforgeeks.org/pair-in-kotlin/](https://www.geeksforgeeks.org/pair-in-kotlin/)

在编程中，我们调用[函数](https://www.geeksforgeeks.org/kotlin-functions/)来执行特定的任务。关于函数最好的一点是我们可以调用它任何次数，并且它在计算后返回一些值，即如果我们有 **add()** 函数，那么它总是返回输入的两个数字的总和。

但是，函数有一些限制，比如函数一次只返回一个值。如果需要返回多个不同数据类型的值，那么我们可以创建一个类，并声明我们希望从函数返回的所有变量，然后创建该类的一个对象，并轻松地将所有返回值收集在一个列表中。**主要问题**是，如果程序中有这么多函数一次返回多个值，那么我们必须为所有这些函数创建一个单独的类，并最终使用该类。这个过程增加了程序的冗长性和复杂性。

为了处理这类问题，柯特林引入了**对**和**三重**的概念。

### 什么是配对？–

Kotlin 语言提供了一种简单的数据类型，可以在单个实例中存储两个值。这可以使用称为**对**的数据类来完成。这是一个简单的[泛型类](https://www.geeksforgeeks.org/kotlin-generics/)，可以存储相同或不同数据类型的两个值，两个值之间可以有也可以没有关系。两个**配对**对象之间的比较是基于**值**进行的，即如果两个配对对象的值相等，则两个配对对象相等。

**等级定义–**

```
data class Pair<out A, out B> : Serializable

```

有两个**参数:
T3】A–**类型的第一个值
T6】B–类型的第二个值

### 构造器–

在 Kotlin 中，[构造函数](https://www.geeksforgeeks.org/kotlin-constructor/)是一个特殊的成员函数，在创建类的对象时调用，主要用于初始化变量或属性。要创建配对的新实例，我们使用:

```
Pair(first: A, second: B)
```

**使用构造函数创建配对的 Kotlin 示例–**

```
fun main() {
    val (x, y) = Pair(1, "Geeks")
    println(x)
    println(y)
}
```

**输出:**

```
1
Geeks

```

### 属性–

我们可以在单个变量中接收对的值，或者我们可以使用 f **第一**和**第二**属性来提取值。
**第一个**:该字段存储配对的第一个值。
**秒**:该字段存储配对的第二个值。

**使用属性–**检索配对值的科特林程序

```
fun main() {
    // declare pair
    var pair = Pair("Hello Geeks", "This is Kotlin tutorial")
    println(pair.first)
    println(pair.second)
}
```

**输出:**

```
Hello Geeks
This is Kotlin tutorial

```

### 功能–

**toString():** 该函数返回配对的等效字符串。

```
fun toString(): String

```

**使用功能的柯特林程序–**

```
fun main() {
    val obj = Pair(5,5)
    println("String representation is "+obj.toString())
    val pair = Pair("Geeks", listOf("Praveen", "Gaurav", "Abhi"))
    print("Another string representation is "+pair.toString())
}
```

**输出:**

```
String representation is (5, 5)
Another string representation is (Geeks, [Praveen, Gaurav, Abhi])

```

### 扩展功能–

正如我们在之前的文章中了解到的那样，[扩展函数](https://www.geeksforgeeks.org/kotlin-extension-function/)能够在不继承现有类的情况下，向它们添加更多的功能。
**toList():** 这个函数返回给定对的列表等价物。

```
fun <T>Pair<T, T>.toList(): List

```

**使用扩展功能的柯特林程序–**

```
fun main() {
    // first pair
    var obj = Pair(1,2)
    val list1: List<Any> = obj.toList()
    println(list1)
    // second pair
    var obj2 = Pair("Hello","Geeks")
    val list2: List<Any> = obj2.toList()
    println(list2)
}
```

**输出**

```
[1, 2]
[Hello, Geeks]

```