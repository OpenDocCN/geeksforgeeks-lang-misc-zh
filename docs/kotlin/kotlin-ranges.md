# 科特林山脉

> 原文:[https://www.geeksforgeeks.org/kotlin-ranges/](https://www.geeksforgeeks.org/kotlin-ranges/)

在[柯特林](https://www.geeksforgeeks.org/introduction-to-kotlin/)中，范围是由端点定义的有限值的集合。科特林的范围包括开始、停止和步骤。起始值和终止值包含在范围内，步长值默认为 1。
该系列用于同类产品。

在科特林有三种**和**方法来创建范围–

*   使用**(..)**操作员
*   使用 **rangeTo()** 功能
*   使用 **downTo()** 功能

### （..)操作员

这是处理范围的最简单方法。它将创建从开始到结束的范围，包括开始和结束的值。它是 rangeTo()函数的运算符形式。使用(..)运算符我们可以为整数和字符创建范围。
**柯特林程序的整数范围使用(..)操作员–**

```kt
fun main(args : Array<String>){

    println("Integer range:")
    // creating integer range 
    for(num in 1..5){
        println(num)
    }
}
```

**输出:**

```kt
Integer range:
1
2
3
4
5

```

**柯特林程序的字符范围使用(..)操作员–**

```kt
fun main(args : Array<String>){

    println("Character range:")
    // creating character range 
    for(ch in 'a'..'e'){
        println(ch)
    }
}
```

**输出:**

```kt
Character range:
a
b
c
d
e

```

### rangeTo()函数

它类似于(..)运算符。它将创建一个直到作为参数传递的值的范围。它也用于创建整数和字符的范围。
**使用 rangeTo()函数的整数范围的 Kotlin 程序–**

```kt
fun main(args : Array<String>){

    println("Integer range:")
    // creating integer range 
    for(num in 1.rangeTo(5)){
        println(num)
    }
}
```

**输出:**

```kt
Integer range:
1
2
3
4
5

```

**使用 rangeTo()函数对字符范围进行 Kotlin 编程–**

```kt
fun main(args : Array<String>){

    println("Character  range:")
    // creating character range
    for(ch in 'a'.rangeTo('e')){
        println(ch)
    }
}
```

**输出:**

```kt
Character  range:
a
b
c
d
e

```

### downTo()函数

它与范围 To()或(..)运算符。它以降序创建一个范围，即从较大的值到较小的值。下面我们以相反的顺序为整数和字符创建范围。
**使用 downTo()函数的整数范围柯特林程序–**

```kt
fun main(args : Array<String>){

    println("Integer range in descending order:")
    // creating integer range
    for(num in 5.downTo(1)){
        println(num)
    }
}
```

**输出:**

```kt
Integer range in descending order:
5
4
3
2
1

```

**使用 downTo()函数对字符范围进行 Kotlin 编程–**

```kt
fun main(args : Array<String>){

    println("Character range in reverse order:")
    // creating character range
    for(ch in 'e'.downTo('a')){
        println(ch)
    }
}
```

**输出:**

```kt
Character range in reverse order:
e
d
c
b
a

```

### 使用 forEach 循环的范围–

forEach 循环也用于遍历范围。

```kt
fun main(args : Array<String>){

    println("Integer  range:")
    // creating integer range
    (2..5).forEach(::println)
}
```

**输出:**

```kt
Integer  range:
2
3
4
5

```

### 步骤()

使用关键字**步长**，可以提供值之间的步长。它主要用于在 rangeTo()或 downTo()或 in()中提供两个值之间的差距..)运算符。步长的默认值为 1，步长函数值不能为 0。

**使用步骤的柯特林程序–**

```kt
fun  main(args: Array<String>) {
    //for iterating over the range
    var i = 2
    // for loop with step keyword
    for (i in 3..10 step 2) 
        print("$i ") 
    println()
    // print first value of the range
    println((11..20 step 2).first) 
    // print last value of the range
    println((11..20 step 4).last)  
    // print the step used in the range
    println((11..20 step 5).step)  
}
```

**输出:**

```kt
3 5 7 9 
11
19
5

```

### 反向函数()

它用于反转给定的范围类型。我们可以使用 reverse()函数以降序打印范围，而不是 downTo()。

```kt
fun main(args: Array<String>) {
    var range = 2..8
    for (x in range.reversed()){
        print("$x ")
    }
}
```

**输出:**

```kt
8 7 6 5 4 3 2 
```

### 范围内的一些预定义功能–

柯特林范围内有一些预定义函数:最小值()、最大值()、和()、平均值()。

```kt
fun main() {

    val predefined = (15..20)

    println("The minimum value of range is: "+predefined.min())
    println("The maximum value of range is: "+predefined.max())
    println("The sum of all values of range is: "+predefined.sum())
    println("The average value of range is: "+predefined.average())
}
```

**输出:**

```kt
The minimum value of range is: 15
The maximum value of range is: 20
The sum of all values of range is: 105
The average value of range is: 17.5

```

### 检查一个值是否在范围内？

```kt
fun  main(args: Array<String>)
{
    var i = 2
    //to check whether the value lies in the range
    if( i in 5..10)
        println("$i is lie within the range")
    else
        println("$i does not lie within the range")
}
```

**输出:**

```kt
2 does not lie within the range
```