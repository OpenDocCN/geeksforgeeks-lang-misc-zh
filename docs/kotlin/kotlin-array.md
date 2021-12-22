# 科特林阵

> 原文:[https://www.geeksforgeeks.org/kotlin-array/](https://www.geeksforgeeks.org/kotlin-array/)

[数组](https://www.geeksforgeeks.org/introduction-to-arrays/)是几乎所有编程语言中最基本的数据结构之一。数组背后的思想是在单个变量名下存储多个相同数据类型的项目，如*整数*或*字符串*。
数组用于在编程中组织数据，以便可以轻松地对一组相关的值进行排序或搜索。
以下是数组的一些基本属性–

*   它们存储在连续的内存位置。
*   可以通过索引(数组[1]、数组[0]等)以编程方式访问它们。)
*   它们是可变的。
*   它们的大小是固定的。

要了解更多关于数组数据结构的信息，请查看[数组教程](https://www.geeksforgeeks.org/array-data-structure/)。

### 创建阵列–

在 Kotlin 中，数组不是一种本机数据类型，而是由数组类表示的相似项的可变集合。
在柯特林中有两种方式定义数组。

**使用`arrayOf()`功能–**

我们可以使用库函数 **`arrayOf()`** 通过将元素的值传递给函数来创建一个数组。
**语法:**

```kt
val num = arrayOf(1, 2, 3, 4)   //implicit type declaration
val num = arrayOf<Int>(1, 2, 3) //explicit type declaration

```

**使用 arrayOf()和 arrayOf < Int >函数创建数组的 Kotlin 程序-**

```kt
fun main()
{
    // declaring an array using arrayOf()
    val arrayname = arrayOf(1, 2, 3, 4, 5)
    for (i in 0..arrayname.size-1)
    {
        print(" "+arrayname[i])
    }
    println()
    // declaring an array using arrayOf<Int>
    val arrayname2 = arrayOf<Int>(10, 20, 30, 40, 50)
    for (i in 0..arrayname2.size-1)
    {
        print(" "+arrayname2[i])
    }
}
```

**输出:**

```kt
 1 2 3 4 5
 10 20 30 40 50

```

**使用数组构造函数–**

因为 Array 是 Kotlin 中的一个类，所以我们也可以使用 Array 构造函数来创建一个数组。
施工方取**两个**参数:

1.  数组的大小，以及
2.  接受给定元素的索引并返回该元素初始值的函数。

**语法:**

```kt
 val num = Array(3, {i-> i*1})
```

在上面的例子中，我们将数组的大小传递为 3 和一个[λ表达式](https://www.geeksforgeeks.org/kotlin-lambdas-expressions-and-anonymous-functions/)，该表达式将元素值从 0 初始化为 9。

**使用构造函数创建数组的 Kotlin 程序–**

```kt
fun main()
{
    val arrayname = Array(5, { i -> i * 1 })
    for (i in 0..arrayname.size-1)
    {
        println(arrayname[i])
    }
}
```

**输出:**

```kt
0
1
2
3
4

```

除此之外，Kotlin 还有一些**内置的**工厂方法来创建原始数据类型的数组，比如 byteArray、intArray、shortArray 等。这些类不扩展数组类；但是，它们实现相同的方法和属性。

例如，创建整数数组的工厂方法是:

```kt
val num = intArrayOf(1, 2, 3, 4)

```

其他可用于创建阵列的工厂方法:

*   字节数组()
*   charArrayOf()
*   shortArrayOf()
*   longArrayOf()

### 访问和修改阵列–

到目前为止，我们已经看到了如何在 Kotlin 中创建和初始化数组。现在，让我们看看如何访问和修改它们。
同样，有两种**方法可以做到这一点:**

****使用`get()`和`set()`方法–****

**如你所知，科特林的一个阵基本上就是一个**级**。因此，我们可以通过类对象的成员函数来访问它的数据。`get()`和`set()`功能被称为成员功能。**

**`get()`方法采用单个参数——元素的索引，并返回该项在该索引处的值。
**语法:****

```kt
val x = num.get(0) 
```

**`set()`方法取 2 个参数:元素的索引和要插入的值。
**语法:****

```kt
num.set(1, 3) 
```

**上面的代码将数组中第二个元素的值设置为 3**

****使用索引运算符[]–****

 ****`[ ]`** 运算符可用于访问和修改数组。
要访问数组元素，语法应该是:

```kt
val x = num[1]

```

这将把 *num* 中第二个元素的值赋给 *x* 。

要修改数组元素，我们应该执行以下操作:

```kt
num[2] = 5;

```

这会将 num 数组中第三个元素的值更改为 5。

**注:**内部，索引运算符 or [ ]实际上是一个重载运算符(参见运算符重载)，仅代表对`get()`和`set()`成员函数的调用。

下面是一个 Kotlin 数组操作的工作示例，其中我们创建一个数组，修改它的值，并访问一个特定的元素:

```kt
fun main()
{   // declare an array using arrayOf()
    val num = arrayOf(1, 2, 3, 4, 5)

    num.set(0, 10)  // set the first element equal to 10
    num.set(1, 6)   // set the secondelement equal to 6

    println(num.get(0)) // print the first element using get()
    println(num[1]) // print the second element using []
}
```

**输出:**

```kt
10
6

```

### 遍历数组–

数组的一个重要属性是它可以通过编程方式遍历，并且数组中的每个元素都可以单独操作。Kotlin 支持一些强大的遍历数组的方法。

在遍历数组时，最简单也是最常用的习惯用法是使用 [for-loop](https://www.geeksforgeeks.org/kotlin-for-loop/) 。
**语法:**

```kt
for(i in num.indices){
      println(num[i])
  }

```

**用于循环的数组遍历的柯特林程序-**

```kt
// Traversing an array
fun main()
{
    val num = arrayOf<Int>(1, 2, 3, 4, 5)
    num.set(0, 10)
    num.set(1, 6)
    for (i in num.indices)
    {
        println(num[i])
    }
}
```

**输出:**

```kt
10
6
3
4
5

```

或者，我们可以使用范围来达到相同的效果。在柯特林中，**范围**是两个值(开始和结束)之间的间隔，可以使用**(..)**操作员。然后可以使用关键字中的**遍历该范围。
**范围语法:****

```kt
for (i in 0..10){
    println(i)
}

```

数组中元素的范围定义为从 0 到 size-1。因此，为了使用 range 遍历数组，我们对数组名运行一个从 0 到 size-1 的循环。
**科特林程序的数组遍历使用范围-**

```kt
// Traversing an array
fun main()
{
    val arrayname = arrayOf<Int>(1, 2, 3, 4, 5)
    for (i in 0..arrayname.size-1)
    {
        println(arrayname[i])
    }
}
```

**输出:**

```kt
1
2
3
4
5

```

另一种可以说不那么繁琐的方法是使用 [foreach](https://www.geeksforgeeks.org/for-each-loop-in-java/) 循环。

**语法:**

```kt
arrayname.forEach({index->println(index)})

```

**使用 foreach 循环遍历数组的 Kotlin 程序-**

```kt
// Traversing an array
fun main()
{
    val arrayname = arrayOf<Int>(1, 2, 3, 4, 5)
    arrayname.forEach({ index -> println(index) })
}
```

**输出:**

```kt
1
2
3
4
5

```**