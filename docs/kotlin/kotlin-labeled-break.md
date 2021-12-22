# 标有断开的柯特林

> 原文:[https://www.geeksforgeeks.org/kotlin-labeled-break/](https://www.geeksforgeeks.org/kotlin-labeled-break/)

在处理循环时，假设您想在满足某个条件时立即停止循环的执行。在这种情况下，您可以使用**中断**或**返回**表达式退出循环。
在本文中，我们将学习如何使用 **break** 表达式退出循环。当 break 表达式在程序中遇到时，它终止于最近的封闭循环。
在 Kotlin 中有两种类型的 *break* 表达:

众所周知，[无标记中断](https://www.geeksforgeeks.org/kotlin-unlabeled-break/)是在满足一定条件时，终止到最近的封闭循环。
但是 ***标记为断开*** 用于在满足特定条件时终止到所需循环。可以借助标签来完成。后跟@符号的标识符称为标签，例如- inner@、outer@、first@、second@等。任何表达式都可以使用 label，而且应该写在前面。
我们将学习如何在 while、do-while 和 for 循环中使用带标签的 break 表达式。

### 使用带标签的边循环边插入–

标记中断用于在满足特定条件时退出到所需的块，而不检查 while 循环中的条件。然后，将控制转移到 while 块的以下语句。
如果使用标签 **outer@** 标记外环，则可以在断开条件块中使用 **break@outer** 轻松断开外环。
**循环时被标记为中断的语法-**

```kt
outer@ while(condition) {
      // code
      inner@ while(condition) {
            // code
            if(break condition) {
               break @outer
            } 
      }
}
```

**使用带标签的 while 循环的 Kotlin 程序–**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>) {
    var num1 = 4
    outer@ while (num1 > 0) {
        var num2 = 4
        inner@ while (num2 > 0) {
            if (num1==2)
                break@outer
            println("num1 = $num1, num2 = $num2")
            num2--
        }
        num1--
    }
}
```