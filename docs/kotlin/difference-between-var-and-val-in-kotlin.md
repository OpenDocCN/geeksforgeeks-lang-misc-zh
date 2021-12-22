# 科特林中 var 和 val 的区别

> 原文:[https://www . geesforgeks . org/var 和 val-in-kotlin 之间的差异/](https://www.geeksforgeeks.org/difference-between-var-and-val-in-kotlin/)

**var** 和 **val** 在 Kotlin 语言中都是用来声明变量的。然而，它们之间有一些关键的区别:

### 风险值(可变)

这是一个通用变量。使用 var 声明的变量值可以在整个程序中随时更改。var 也称为**可变**和**非最终变量**，因为它们的值可以随时更改。
**例:**

```kt
fun main()
 {
   var marks = 10
   println("Previous marks is " + marks)
   marks = 30
   println("New marks " + marks)
 }
```

**输出:**

```kt
Previous marks is 10
New marks 30
```

### 价值

使用 val 存储的对象不能更改，不能重新分配，就像 java 中的 **final** 关键字一样。瓦尔是**不可改变的**。一旦赋值，val 就变成只读的，但是 val 对象的属性可以改变，但是对象本身是只读的。

**例 1:**

```kt
fun main()
{
    val marks = 10 
    println("Previous marks is " + marks)
    marks = 30 
    println("new marks " + marks)
}
```

输出:

```kt
Val cannot be reassigned

```

**例 2:**

```kt
// Changing values of val object
fun main()
{
    val book = Book("Java", 1000)
    println(book)
    book.name = "Kotlin" 
    println(book)
}
data class Book(var name : String = "",
                var price : Int = 0)
```

输出:

```kt
Book(name=Java, price=1000)
Book(name=Kotlin, price=1000)

```