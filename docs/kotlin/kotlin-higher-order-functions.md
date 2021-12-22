# 柯特林高阶函数

> 原文:[https://www . geeksforgeeks . org/kot Lin-高阶-函数/](https://www.geeksforgeeks.org/kotlin-higher-order-functions/)

Kotlin 语言对函数式编程有极好的支持。Kotlin 函数可以存储在变量和数据结构中，作为参数传递给其他高阶函数并从这些函数返回。

### 高阶函数–

在柯特林中，可以接受函数作为参数或者可以返回函数的函数称为**高阶函数**。我们将传递匿名函数或 lambdas，而不是整数、字符串或数组作为函数的参数。为了方便起见，lambdas 经常作为参数在 Kotlin 函数中传递。

### 将λ表达式作为参数传递给高阶函数–

我们可以将λ表达式作为参数传递给高阶函数。
有两种**类型的 lambda 表达式可以传递-**

*   **返回单位的λ表达式**
*   **Lambda 表达式，返回整数、字符串等任何值**

****λ表达式的柯特林程序，返回单位-****

## **我的锅**

```kt
      // lambda expression
var lambda = {println("GeeksforGeeks: A Computer Science portal for Geeks") }
      // higher-order function
fun higherfunc( lmbd: () -> Unit ) {     // accepting lambda as parameter
    lmbd()                               //invokes lambda expression
}
fun main(args: Array<String>) {
     //invoke higher-order function
    higherfunc(lambda)                 // passing lambda as parameter
}
```