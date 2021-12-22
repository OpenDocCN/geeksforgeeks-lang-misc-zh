# Kotlin | Lambdas 表达式和匿名函数

> 原文:[https://www . geeksforgeeks . org/kot Lin-lambdas-expressions-and-anonymous-functions/](https://www.geeksforgeeks.org/kotlin-lambdas-expressions-and-anonymous-functions/)

在本文中，我们将学习 Kotlin 中的 lambdas 表达式和匿名函数。虽然在语法上相似，但是 Kotlin 和 Java lambdas 有非常不同的特性。

Lambdas 表达式和 Anonymous 函数都是*函数文字*表示这些函数没有声明，而是作为表达式立即传递。

### λ表达式–

我们知道，Kotlin lambdas 的语法类似于 Java Lambdas。没有名字的函数叫做匿名函数。对于 lambda 表达式，我们可以说它是匿名函数。

**例:**

## 科特林

```
fun main(args: Array<String>) {
    val company = { println("GeeksforGeeks")}

    // invoking function method1
    company() 

    // invoking function method2
    company.invoke()
}
```