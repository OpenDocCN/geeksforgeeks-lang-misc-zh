# 科特林中的返回、跳转和标签

> 原文:[https://www . geesforgeks . org/returns-jumps-and-labels-in-kot Lin/](https://www.geeksforgeeks.org/returns-jumps-and-labels-in-kotlin/)

Kotlin 是由 JetBrains 开发的一种静态类型的通用编程语言，它已经构建了像 IntelliJ IDEA、PhpStorm、Appcode 等世界一流的 ide。它于 2011 年由 JetBrains 首次引入，是 JVM 的一种新语言。Kotlin 是一种面向对象的语言，也是一种比 Java“更好的语言”，但仍然可以与 Java 代码完全互操作。正如柯特林所说:柯特林有**三个**结构跳跃表达式如下:

1.  return
2.  disconnect
3.  continue

正如柯特林所说，这些可能是大型表达的一部分。那么，让我们从“回归”开始。

### 1.返回

这是一个语句，通常我们在函数中使用，在函数执行后返回值。默认情况下，它从最近的封闭函数或匿名函数返回。让我们举个例子，

**例:**

## 科特林

```kt
fun add(a:Int,b:Int) : Int {
   // ans having final value after execution
   val ans = a + b 
   // here we have returned it
   return ans 
 }
 fun main(args: Array<String>) {

    val first: Int = 10
    val second: Int = 20
    // called function and 
    // Collected the returned value in sum
    val sum = add(first,second)
    println("The sum is: $sum")
}
```