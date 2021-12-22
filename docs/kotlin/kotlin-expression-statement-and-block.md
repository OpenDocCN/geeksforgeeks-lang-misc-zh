# 柯特林表达、陈述和阻止

> 原文:[https://www . geeksforgeeks . org/kot Lin-expression-statement-and-block/](https://www.geeksforgeeks.org/kotlin-expression-statement-and-block/)

### 柯特林表情–

表达式由产生单个值的变量、运算符、方法调用等组成。像其他语言一样，柯特林表达式是任何程序的构造块，通常是为了产生新的价值而创建的。有时，它可以用来给程序中的变量赋值。需要注意的是，一个表达式可以包含另一个表达式。

*   变量声明不能是表达式(var a = 100)
*   赋值不是表达式(b = 15)
*   类声明不是表达式(类 XYZ {…)。})

**注意:**在柯特林中，每个函数至少返回一个单位值，所以每个函数都是一个表达式。
我们举个例子:

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun sumOf(a:Int,b:Int): Int{
    return a+b
}

fun main(args: Array<String>){
    val a = 10
    val b = 5
    var sum = sumOf(a,b)
    var mul = a * b
    println(sum)
    println(mul)
}
```

**输出:**

```
15
50
```

这里， **a * b** 和 **sumof(a，b)** 都是表达式，返回整数值。 **sumOf()** 是一个函数，返回传递给它的两个参数之和。

#### 柯特林 *if* 表达式–

在 Java 中， ***if*** 是一个语句，但是在 Kotlin 中 **if** 是一个表达式。它被称为表达式，因为它比较 a 和 b 的值并返回最大值。因此，在 Kotlin 中没有三元运算符 **(a > b)？a:b** 因为被 *if 表达式*代替了。

```
if(condition) condition met! else condition not met!
```

让我们举一个例子来返回两个变量中的最大值:

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>){
    val a = 1000
    val b = 999
    var c = 1122
    var max1 = if(a > b) a else b
    var max2 = if(c > a) c else a
    println("The maximum of ${a} and ${b} is $max1 " )
    println("The maximum of ${c} and ${a} is $max2 " )
}
```

**输出:**

```
The maximum of 1000 and 999 is 1000 
The maximum of 1122 and 1000 is 1122 
```

### 科特林声明–

语句是任何编程语言的语法单位，表示要执行的某些操作。一个程序是由一个或多个语句序列组成的。在 Java 中，语句总是以分号结尾，但是在 Kotlin 中，分号(；)是可选的。

*   变量的声明是一条语句。

```
val marks = 90
var grade = 'A' 
```

*   给变量赋值也是一种语句。

```
var sum = 10 + 20        // it is a statement
```

*   这里， **10 + 20** 是一个表达式，而 **var sum = 10 + 20** 是一个语句。

**多语句:**
多语句是在一行中写多条语句的语句。
**例如:**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>){
    val sum: Int
    sum = 100
    println(sum)                             // single statement
    println("Hello");println("Geeks!")       // Multiple statements
}
```

**输出:**

```
100
Hello
Geeks!
```

### 科特林街区–

块是用花括号({…})括起来的一段软件代码。一个块可以由一个或多个语句组成，前面是变量声明。一个块包含一个或多个嵌套在其中的块。每个函数都有自己的块，主函数也包含一个块。
**例如:**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {              //start of main block or outer block
     val array = intArrayOf(2, 4, 6, 8)
     for (element in array) {                // start of inner block
        println(element)
     }                                       // end of inner block
 }                                           // end of main block
```

**输出:**

```
2
4
6
8
```

**嵌套块中变量的作用域:**
在块头声明的变量在整个块和任何嵌套块中都可见，除非在内部块头声明了同名变量。当新的声明在整个内部块中有效时，外部声明在内部块的末尾再次生效。所以，我们可以说变量有嵌套的作用域。