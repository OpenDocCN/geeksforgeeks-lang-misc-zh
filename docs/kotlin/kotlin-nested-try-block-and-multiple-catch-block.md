# 柯特林嵌套试块和多抓块

> 原文:[https://www . geeksforgeeks . org/kot Lin-nested-try-block-and-multi-catch-block/](https://www.geeksforgeeks.org/kotlin-nested-try-block-and-multiple-catch-block/)

### 嵌套试块–

在本文中，我们将学习嵌套的 try-catch 块和多重 catch 块。嵌套 try 块是一个我们可以在其中实现一个 try catch 块到另一个 try catch 块的块。

当内部 try-catch 块中发生的异常没有被内部 catch 块处理时，嵌套 try-catch 块的要求就出现了，然后检查外部 try-catch 块中的异常。

**嵌套尝试块的语法–**

```kt
// outer try block
try    
{    
    // inner try block   
    try    
    {    
        // code that can throw exception   
    }    
    catch(e: SomeException)    
    {    
     // catch the exception and handle it
    }    
}    
catch(e: SomeException)    
{    
// catch the exception and handle it
}    

```

**嵌套试块的 Kotlin 程序–**

```kt
fun main(args: Array<String>) {
    val numbers = arrayOf(1,2,3,4)

    try {
        for (i in numbers.indices) {
            try {
                var n = (0..4).random()
                println(numbers[i+1]/n)

            } catch (e: ArithmeticException) {
                println(e)
            }
        }
    } catch (e: ArrayIndexOutOfBoundsException) {
        println(e)
    }
}
```

**输出:**

```kt
2
3
java.lang.ArithmeticException: / by zero
java.lang.ArrayIndexOutOfBoundsException: Index 4 out of bounds for length 4

```

**注意:**这个输出是为某个随机数生成的。如果你会得到一些不同的输出，那么不要担心，因为你的输出将根据在那个时刻产生的随机数。

### 多重捕捉块–

一个试块可以有多个捕捉块。当我们不确定 try 块中会出现什么类型的异常时，我们可以为潜在的异常放置多个 catch 块，在最后一个 catch 块中，我们可以放置父异常类来处理程序中 catch 块未指定的所有剩余异常。

**多重捕获的语法–**

```kt
try {
    // code may throw exception
} catch(e: ExceptionNameOne) {
    // catch the exception one and handle it
} catch(e: ExceptionNameTwo) {
    // catch the exception two and handle it
}

```

**多个捕捉块的柯特林程序–**

```kt
import java.util.Scanner

object Test {
    @JvmStatic
    fun main(args: Array<String>) {
        val sc = Scanner(System.`in`)
        try {
            val n = Integer.parseInt(sc.nextLine())
            if (512 % n == 0)
                println("$n is a factor of 512")
        } catch (e: ArithmeticException) {
            println(e)
        } catch (e: NumberFormatException) {
            println(e)
        }
    }
}
```

**输入 1:**

```kt
GeeksforGeeks
```

**输出 1:**

```kt
java.lang.NumberFormatException: For input string: "GeeksforGeeks"
```

**输入 2:**

```kt
0
```

**输出 2:**

```kt
java.lang.ArithmeticException: / by zero
```

在上面输入 1 的程序中，我们使用了一个字符串，但是需要一个整数值来获得数字的因子。因此，它抛出 NumberFormatException。
对于输入 2，我们输入零，但是不能用零除一个整数。所以，它抛出了算术异常。

### 当处于制动块时的使用–

在 Kotlin 中，我们可以使用 when 表达式来替换多个 catch 块。在下面，我们将展示如何使用当表达式。

```kt
import java.lang.NumberFormatException
import java.util.Scanner

object Test {
    @JvmStatic
    fun main(args: Array<String>) {
        val sc = Scanner(System.`in`)
        try {
            val n = Integer.parseInt(sc.nextLine())
            if (512 % n == 0)
                println("$n is a factor of 512")
        } catch (e: Exception ) {
          when(e){
              is ArithmeticException -> { println("Arithmetic Exception: Divide by zero") }
              is NumberFormatException -> { println("Number Format Exception ") }
          }
        }
    }
}
```

**输入 1:**

```kt
GeeksforGeeks
```

**输出 1:**

```kt
Number Format Exception 
```

**输入 2:**

```kt
0
```

**输出 2:**

```kt
Arithmetic Exception: Divide by zero
```