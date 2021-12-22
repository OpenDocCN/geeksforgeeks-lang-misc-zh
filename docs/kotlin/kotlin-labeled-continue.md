# 科特林标记为继续

> 原文:[https://www.geeksforgeeks.org/kotlin-labeled-continue/](https://www.geeksforgeeks.org/kotlin-labeled-continue/)

在本文中，我们将学习如何在 Kotlin 中使用**继续**。当在编程中使用循环时，有时希望跳过循环的当前迭代。在这种情况下，我们可以在程序中使用*继续*语句。基本上，*继续*用于针对特定条件重复循环。它跳过以下语句，继续循环的下一次迭代。
在 Kotlin 中有两种类型的 continue-
我们知道，**未标记的 continue** 用于跳过最近闭合循环的迭代，但标记的 **continue** 用于跳过所需闭合循环的迭代。可以借助内部@、外部等标签。我们只需要在表达式前面写一个标签，并使用 continue@abc 调用它。
我们将学习如何使用带标签的 continue in 一阵子、do-while 和 for 循环。

### 在 while 循环中使用标记为继续的–

标记为**继续**用于在所需块满足特定条件时跳过该块的迭代，而不检查 while 循环中的条件。如果您使用标签 outer@标记外环，使用 inner@标记内环，那么您可以使用条件块中的 **continue@outer** 轻松跳过特定条件。
**标记为 while 循环中继续的语法-**

```kt
outer@ while(firstcondition) {
      // code
      inner@ while(secondcondition) {
            //code
            if(condition for continue) {
               continue@outer
            } 
      }
}
```

**使用标记为**的**的科特林程序继续循环-**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>) {

    var num1 = 4
    outer@ while (num1 > 0) {
        num1--
        var num2 = 4

        inner@ while (num2 > 0) {
            if (num1 <= 2)
                continue@outer
            println("num1 = $num1, num2 = $num2")
            num2--
        }
    }
}
```

**输出:**

```kt
num1 = 3, num2 = 4
num1 = 3, num2 = 3
num1 = 3, num2 = 2
num1 = 3, num2 = 1
```

**在边做边循环中使用标记的继续**

我们也可以在 do-while 循环中使用标记的 continue。在下面的程序中，我们使用了一个嵌套的 do-while 循环，并用 outer@标记了外部循环，用 inner@标记了内部循环。在内部边做边循环中继续通过的条件。如果条件变为真，则*继续@外部*跳过以下语句或表达式，并将控制权交给外部 do-while 进行重复。
**在边做边循环中标记为继续的语法-**

```kt
outer@ do {
       // code
       inner@ do {
           // code
           if(condition for continue) {
              continue@outer
           }
       } while(firstcondition)
} while(secondcondition)

```

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>) {

    var num1 = 4
    outer@ do {
        num1--
        var num2 = 4

        inner@ do {
            if (num1 <= 2)
                continue@outer
            println("num1 = $num1; num2 = $num2")
            num2--
        } while (num2 > 0)

    } while (num1 > 0)
}
```

**输出:**

```kt
num1 = 3; num2 = 4
num1 = 3; num2 = 3
num1 = 3; num2 = 2
num1 = 3; num2 = 1
```

**使用标记的继续循环–**

我们也可以使用标记为*的继续*进行循环。在下面的程序中，我们对循环使用了嵌套，并用外部@标记了外部循环，用内部@标记了内部循环。内部 for 循环中继续传递的条件。如果条件变为真，则它跳过以下语句，并将控制传递给外部 for 循环，以便进一步迭代。
标记为继续循环的语法**-**标记为 T5】

```kt
outer@ for(iteration through iterator) {
    // code
      inner@ for(iteration through iterator) {
           // code
          if(condition for continue) {
          continue@outer
          }
      }
}
```

**在 for 循环中继续使用标记为**的**的科特林程序-**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>) {
    outer@ for (num1 in 4 downTo 1) {

        inner@ for (num2 in 4 downTo 1) {
            if (num1 <= 3)
                continue@outer
            println("num1 = $num1; num2 = $num2")
        }
    }
}
```

**输出:**

```kt
num1 = 4; num2 = 4
num1 = 4; num2 = 3
num1 = 4; num2 = 2
num1 = 4; num2 = 1
```