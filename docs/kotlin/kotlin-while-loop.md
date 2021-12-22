# Kotlin while loop

> 原文:[https://www.geeksforgeeks.org/kotlin-while-loop/](https://www.geeksforgeeks.org/kotlin-while-loop/)

在编程中，循环用于重复执行特定的代码块，直到满足特定的条件。如果你必须打印从 1 到 100 的计数，那么你必须写 100 次打印语句。但是在循环的帮助下，你可以节省时间，你只需要写两行。

**While loop–**
它由一个代码块和一个条件组成。首先评估条件，如果条件为真，则在块中执行代码。它一直重复，直到条件变为假，因为每次在进入块之前检查条件。while 循环可以被认为是重复 *if* 语句。

***而*** 的语法循环——

```kt
while(condition) {
           // code to run
}
```

**流程图-**

![](img/7a185c7e34ba9db4e8c1b2f9baff285f.png)

**Kotlin 程序使用 while 循环打印从 1 到 10 的数字:**
在下面的程序中，我们使用 while 循环打印数字。首先，用 1 初始化变量编号。将表达式(数字< = 10)放入 while 循环中，检查是否正确？。如果为真，则进入块并执行打印语句，并将数字增加 1。这样重复，直到条件变为假。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>) {
    var number = 1

    while(number <= 10) {
        println(number)
        number++;
    }
}
```

**输出:**

```kt
1
2
3
4
5
6
7
8
9
10
```

**使用 while 循环打印数组元素的 Kotlin 程序:**
在下面的程序中，我们创建一个数组(名称)，用不同数量的字符串初始化，并将变量索引初始化为 0。一个数组的大小可以通过**数组的大小**来计算。将条件(索引<name . size)放入 while 循环中。
如果索引值小于或等于数组大小，则它进入块并打印存储在相应索引处的名称，并且在每次迭代后增加索引值。这样重复，直到条件变为假。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>) {
    var names = arrayOf("Praveen","Gaurav","Akash","Sidhant","Abhi","Mayank")
    var index = 0

    while(index < names.size) {
        println(names[index])
        index++
    }
}
```

**输出:**

```kt
Praveen
Gaurav
Akash
Sidhant
Abhi
Mayank
```