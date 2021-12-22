# 柯特林中缀函数符号

> 原文:[https://www . geeksforgeeks . org/kot Lin-infix-function-notation/](https://www.geeksforgeeks.org/kotlin-infix-function-notation/)

在本文中，我们将学习柯特林函数中使用的*中缀符号*。在 Kotlin 中，标有**中缀**关键字的函数也可以使用中缀表示法调用，即不使用括号和点进行调用。
柯特林-
中有两种**中缀函数符号**

1.  **标准库中缀函数符号**
2.  **用户定义的中缀函数符号**

## **标准库中缀函数符号–**

**当我们调用 and、or、shr、shl 等运算符时，编译器会查找函数并调用所需的函数。有许多标准的库中缀符号函数，但我们将在这里讨论其中的一些。
让我们逐一讨论一些中缀符号。
**1。Kotlin 程序使用按位 and 运算符–**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
fun main(args: Array<String>) {
    var a = 15
    var b = 12
    var c = 11
    // call using dot and parenthesis
    var result1 =(a > b).and(a > c)          
    println("Boolean result1 = $result1")
    // call using infix notation
    var result2 =(a > b) and (a > c)         
    println("Boolean result1 = $result2")
}
```

****输出:**** 

```kt
Boolean result1 = true
Boolean result1 = true
```

****说明:**
在这里，我们已经使用中缀( **a 和 b** )调用了 **a .和(b)** 函数。
两者在标准输出中产生相同的结果。
**2。使用带符号右移运算符的 Kotlin 程序–**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
fun main(args: Array<String>) {
    var a = 8

    // // call using infix notation
    var result1 = a shr 2
    println("Signed shift right by 2 bit: $result1")
    // call using dot and parenthesis
    var result2 = a.shr(1)
    println("Signed shift right by 1 bit: $result2")
}
```

****输出:**** 

```kt
Signed shift right by 2 bit: 2
Signed shift right by 1 bit: 4
```

****说明:**
在上面的程序中，我们使用了带符号的 shift 运算符。首先，使用中缀符号执行操作，然后使用点和括号执行操作。
如果我们将值移位 2 位，则 **2 <sup>3</sup> =8** 变为 **2 <sup>(3-2=1)</sup> =2** 。
**3。使用递增和递减运算符的 Kotlin 程序–**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
fun main(args: Array<String>) {
    var a = 8
    var b = 4

    println(++a)      // call using infix notation
    println(a.inc())  // call using dot and parenthesis
    println(--b)      // call using infix notation
    println(b.dec())  // call using dot and parenthesis
}
```

****输出:**** 

```kt
9
10
3
2
```

****解释:**
这里，我们使用了使用中缀符号的递增和递减运算符。
++a 代表 a(8) + 1，因此打印 9
a.inc()也代表 a(9) + 1，因此打印 10
–b 代表 b(4)–1 = 3
b . dec()也代表 b(3)- 1 = 2** 

## **用户定义的中缀函数符号–**

**如果函数满足以下要求，我们可以用中缀符号创建自己的函数:** 

*   **它必须是成员函数或扩展函数**
*   **它必须接受单个参数**
*   **参数不能接受可变数量的参数，并且不能有默认值**
*   **必须标注**中缀**关键字**

****用中缀符号创建平方函数的科特林程序–**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
class math {
    // user defined infix member function
    infix fun square(n : Int): Int{
        val num = n * n
        return num
    }
}
fun main(args: Array<String>) {
   val m = math()
    // call using infix notation
    val result = m square 3
    print("The square of a number is: "+result)
}
```

****输出:**** 

```kt
The square of a number is: 9
```

****说明:**
在上面的程序中，我们已经创建了自己的中缀记数函数( **m square 3** )。
1。首先，我们把中缀定义为类**数学**中的中缀符号函数，因为它必须是成员函数。
2。**中缀**关键字用于标记功能。
3。它只包含一个参数，没有默认值，函数返回类型也是整数。** 

```kt
square(n : Int):Int
```

**然后，我们为类 **math()**
创建一个对象，并使用中缀符号调用该函数-** 

```kt
m square 3
```

**它计算数字的平方并返回值 9
**Kotlin 程序用中缀符号–**
检查变量的数据类型**

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
class check{
    // user defined infix member function
    infix fun dataType(x: Any):Any{
    var i = when(x){
            is String -> "String"
            is Int -> "Integer"
            is Double -> "Double"
            else -> "invalid"
        }
        return i
    }
}
fun main(args: Array<String>){
    var chk = check()
    // call using infix notation
    var result = chk dataType 3.3
    println(result)
}
```

****输出:**** 

```kt
Double
```

****解释:**
我们创建了一个中缀符号函数来查找变量的数据类型。
数据类型在中缀调用中作为参数传递-** 

```kt
chk dataType 3.3
```

**当检查传递参数的数据类型并返回所需值时。
这里，它将**加倍**返回到标准输出。** 

## **中缀函数与算子的相关性**

**执行指令时优先级很重要。中缀函数调用的优先级低于算术运算符、类型转换和 rangeTo 运算符。
以下表达式等价:** 

```kt
2 shr 1 + 2 and 2 shr (1 + 2)
1 until n * 2 and 0 until (n * 2)
xs union ys as Set<*> and xs union (ys as Set<*>)
```

**另一方面，中缀函数调用比布尔运算符&&和||、is-和 in-check 以及其他一些运算符具有更高的优先级。
以下表达式也是等价的:** 

```kt
a xor b || c and a xor (b || c)
a in b xor c and a in (b xor c)
```