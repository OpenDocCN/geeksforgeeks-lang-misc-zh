# 柯特林型转换

> 原文:[https://www.geeksforgeeks.org/kotlin-type-conversion/](https://www.geeksforgeeks.org/kotlin-type-conversion/)

类型转换(也称为类型转换)是指将一个数据类型变量的实体更改为另一个数据类型。

众所周知，Java 支持从较小数据类型到较大数据类型的隐式类型转换。整数值可以赋给长数据类型。
**例如:**

```kt
var myNumber = 100
var myLongNumber: Long = myNumber            // Compiles Successfully

```

但是，Kotlin 不支持隐式类型转换。整数值不能赋给长数据类型。

```kt
var myNumber = 100
var myLongNumber: Long = myNumber       // Compiler error
// Type mismatch: inferred type is Int but Long was expected

```

在 Kotlin 中， *helper* 函数可用于显式地将一种数据类型转换为另一种数据类型。

**例如:**

```kt
var myNumber = 100
var myLongNumber: Long = myNumber.toLong()     // compiles successfully

```

以下助手函数可用于将一种数据类型转换为另一种数据类型:

*   托字节（）
*   托荷()
*   toInt（）
*   toLong（）
*   toFLoat（）
*   toDouble（）
*   toChar()

**注意:**没有可转换为布尔类型的辅助函数。

**从大数据类型到小数据类型的转换–**

```kt
var myLongNumber = 10L
var myNumber2: Int = myLongNumber1.toInt()

```

柯特林程序将一种数据类型转换成另一种数据类型:

```kt
fun main(args: Array<String>)
{

    println("259 to byte: " + (259.toByte()))
    println("50000 to short: " + (50000.toShort()))
    println("21474847499 to Int: " + (21474847499.toInt()))
    println("10L to Int: " + (10L.toInt()))
    println("22.54 to Int: " + (22.54.toInt()))
    println("22 to float: " + (22.toFloat()))
    println("65 to char: " + (65.toChar()))
    println("A to Int: " + ('A'.toInt()))
}
```

**输出:**

```kt
259 to byte: 3
50000 to short: -15536
21474847499 to Int: 11019
10L to Int: 10
22.54 to Int: 22
22 to float: 22.0
65 to char: A
A to Int: 65

```