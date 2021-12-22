# 科特林代表团

> 原文:[https://www.geeksforgeeks.org/delegation-in-kotlin/](https://www.geeksforgeeks.org/delegation-in-kotlin/)

**委托**控制任何对象从一个实例到另一个实例的权力/权限分配。对于类和函数实现，委托可以用于它们之间的静态和可变关系。在委托技术的帮助下，类和函数中的继承实现可以被改变，面向对象编程语言天生支持它，而不需要任何样板代码。委托是在**的帮助下通过**关键字在科特林中使用的。

Kotlin 中存在两种类型的委托:
**显式委托:**受所有面向对象语言的支持，它是通过将委托(要实现的对象)传递给委托对象(将实现委托对象的对象)来完成的。
**隐式委托:**需要语言级支持委托模式。

让我们借助示例 :
**示例 1:** 来讨论代表团的概念

我们知道，在 Kotlin 中，继承为我们提供了不可变的对象之间的永久静态关系，而委托是可变的，这一事实使得**委托**成为一个极其强大的选择。在本例中，使用 Newfeature 类，我们可以通过委托其所有公共成员(即 mymessage 和 messageline)来实现具有新功能的委托基类，并且我们正在“by”关键字的帮助下使用该实现。

## 我的锅

```kt
// Kotlin program to illustrate the 
// concept of delegation

interface delegation 
{
    fun mymessage()
    fun mymessageline()
}

class delegationimplementation(val y: String) : delegation
{
    override fun mymessage() 
    { 
        print(y)
    }
    override fun mymessageline() 
    { 
        println(y)
    }
}

class Newfeature(m: delegation) : delegation by m
{
    override fun mymessage() 
    {
        print("GeeksforGeeks")
    }
}

// Main function
fun main() 
{
    val b = delegationimplementation("\nWelcome, GFG!")

    Newfeature(b).mymessage()
    Newfeature(b).mymessageline()
}
```

**输出:**

```kt
GeeksforGeeks
Welcome, GFG!

```

**例 2:**

在这个例子中，我们有一个带有 val 值和方法“fun message()”的委托基类。在 delegationimplementation 类中，我们为这个“有趣的消息”赋值，稍后在另一个类中，我们使用这个实现使用“by”关键字添加一个具有相同 val 值的新语句；

## 我的锅

```kt
// Kotlin program to illustrate the 
// concept of delegation
interface delegation
{
    val value: String
    fun mymessage()
}

class delegationimplementation(val y: String) : delegation
{
    override val value = "delegationimplementation y = $y"
    override fun mymessage() 
    {
        println(value)
    }
}

class Newfeatures(a: delegation) : delegation by a 
{
    override val value = "GeeksforGeeks"
}

fun main() 
{
    val b = delegationimplementation("Hello!GFG")
    val derived = Newfeatures(b)

    derived.mymessage()
    println(derived.value)
}
```

**输出:**

```kt
delegationimplementation y = Hello!GFG
GeeksforGeeks

```

### 优点:

1.这是一个灵活、强大且可变的方法。
2。在现有接口的帮助下，可以实现多个接口。
3。它用于向当前实现添加新的特性和值。