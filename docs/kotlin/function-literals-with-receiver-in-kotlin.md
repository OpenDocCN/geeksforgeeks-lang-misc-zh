# 柯特林中带接收器的函数文字

> 原文:[https://www . geesforgeks . org/function-lithos-with-receiver-in-kot Lin/](https://www.geeksforgeeks.org/function-literals-with-receiver-in-kotlin/)

在科特林，职能是一等公民。这意味着函数可以赋给变量，作为参数传递，或者从另一个函数返回。虽然 Kotlin 是静态类型的，但为了实现这一点，函数需要有一个类型。它存在，被称为函数类型，它们是:

> *   瓦尔心愿:()->单位

**本条前提条件:**

*   [柯特林](https://www.geeksforgeeks.org/kotlin-functions/)中的功能
*   [柯特林](https://www.geeksforgeeks.org/kotlin-reflection/)中的函数引用
*   柯特林中**接收器的基本思想**

函数引用是反射的一个例子。它返回对函数的引用，该函数还实现了表示函数类型的接口。这就是为什么它可以这样使用。一般来说，编程中的文字是语法糖的立方体，用于表示语言认为特别重要的某些类型的值。因此，函数文字是一种特殊的符号，用于简化函数的定义。Kotlin 中有两种类型的函数文字:

*   [Lambda 表达式](https://www.geeksforgeeks.org/kotlin-lambdas-expressions-and-anonymous-functions/)(这是定义函数的一种简称。)
*   [匿名函数](https://www.geeksforgeeks.org/kotlin-lambdas-expressions-and-anonymous-functions/)(是定义函数的替代方式。)

### 介绍

函数文本是未声明但作为表达式传入的函数。Lambdas 和匿名函数是函数文字。在 Kotlin 中，我们可以用一个 receiver 对象调用一个函数字面量，我们可以在函数字面量的主体内部调用 receiver 对象上的方法，非常像扩展函数。在本文中，我们将学习如何将函数文字用于接收器。

**示例:**按照以下步骤理解函数文字:

让我们从字符串上的一个简单函数文字开始，它返回一个添加到接收方字符串的字符串:

## 我的锅

```
fun main (args: Array<String>) {
  var s = "gonna do "
  val addS = fun String. (successor: String) : String {
    return this + successor
  }
  s = s . addS ("nothing much.")
  printIn (s)
}
```

函数文字可以访问被调用的接收器，并且可以访问与该接收器关联的方法。我们也可以在普通函数中将接收器作为参数传递，其中第一个参数用于接收器。这在我们需要使用普通函数 So String 的场景中非常有用。(字符串)-> Int 类似于(字符串，字符串)-> Int 兼容。查看以下示例:

## 我的锅

```
fun main (args: Array<String>) {
  var s = "gonna do "
  val addS = fun String. (successor: String) : Int {
    return this . length + successor . length
      }
    var x = s. addS ("nothing  much.")
    printin (x)
    fun testIfEqual (op: (String, String) -> Int, a: String, b:String, c: Int) =
  assert (op (a, b) == c)
    test IfEqual (addS, "gonna do ","nothing much. ",
                  s . length + "nothing     much.". length)
}
```

如果可以推断出接收器类型，那么 lambda 可以用作函数文本。所以基本上，我们可以在接收器对象上调用一个函数文字，在函数体内部，我们可以访问和调用接收器对象上的方法，类似于 Kotlin 中的扩展函数。以下是其语法:

> 接收器。函数一般(参数)->返回类型