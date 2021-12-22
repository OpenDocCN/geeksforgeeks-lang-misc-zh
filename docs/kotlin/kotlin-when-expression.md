# 科特林当表情

> 原文:[https://www.geeksforgeeks.org/kotlin-when-expression/](https://www.geeksforgeeks.org/kotlin-when-expression/)

在 Kotlin 中，**当**替换了其他语言如 Java 的**开关**操作符时。当满足某个条件时，需要执行某个代码块。*的论证当*表达式与所有分支逐一比较，直到找到某种匹配。找到第一个匹配项后，它会到达 when 块的末尾，并执行 when 块旁边的代码。与 java 或任何其他编程语言中的 switch case 不同，我们不需要在每个 case 的末尾使用 break 语句。
在科特林， ***时*** 可以用两种方式:

*   当作为陈述
*   当作为一种表达

### 使用*时*作为与*其他*的声明–

**时**可以作为有无*的语句，否则*分支。如果将其用作语句，则将所有单个分支的值与参数进行顺序比较，并在条件匹配的情况下执行相应的分支。如果没有一个分支满足条件，那么它将执行 else 分支。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
import java.util.Scanner;
fun main(args: Array<String>) {
    var reader = Scanner(System.`in`)
    print("Enter any largebody:")
    var lb = reader.next()

    when(lb) {
        "Sun" -> println("Sun is a Star")
        "Moon" -> println("Moon is a Satellite")
        "Earth" -> println("Earth is a planet")
         else -> println("I don't know anything about it")
    }
}
```

**输出:**

```kt
Enter any largebody: Sun
Sun is a Star

Enter any largebody: Mars
I don't know anything about it
```

### 使用 when 作为陈述，不带*或*–

不用 *else* 分支，我们可以用 when 作为语句。如果将其用作语句，则将所有单个分支的值与参数进行顺序比较，并在条件匹配的情况下执行相应的分支。如果没有一个分支满足这个条件，那么它就退出程序块，不打印任何东西到系统输出。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
import java.util.Scanner;
fun main(args: Array<String>) {
    var reader = Scanner(System.`in`)
    print("Enter name:")
    var lb = reader.next()

    when(lb) {
        "Sun" -> println("Sun is a Star")
        "Moon" -> println("Moon is a Satellite")
        "Earth" -> println("Earth is a planet")
    }
}
```

**输出:**

```kt
Enter name: Mars

Process finished with exit code 0
```

### 将 when 用作表达式–

如果用作表达式，满足条件的分支的值将是整个表达式的值。作为表达式**当**返回一个与自变量匹配的值时，我们可以将其存储在变量中或者直接打印出来。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
import java.util.Scanner;
fun main(args: Array<String>) {
    var reader = Scanner(System.`in`)
    print("Enter the month number:")
    var monthOfYear = reader.nextInt()
    var month = when(monthOfYear){
        1->"January"
        2->"February"
        3->"March"
        4->"April"
        5->"May"
        6->"June"
        7->"July"
        8->"August"
        9->"September"
        10->"October"
        11->"November"
        12->"December"
        else -> {
            println("Not a month of year")
        }
    }
    println(month)
}
```

**输出:**

```kt
Enter the month number:8
August
```

如果参数不满足任何分支条件，则执行 else 分支。作为一个表达式，else 分支是强制的，除非编译器能够证明所有可能的情况都被分支条件覆盖。如果我们不能使用 else 分支，它将给出一个编译器错误。

```kt
Error:(6, 17) Kotlin: 'when' expression must be exhaustive, add necessary 'else' branch
```

### 在 Kotlin 中阻止时的不同使用方式:

**用逗号–**
将多个分支组合在一个分支中我们可以用逗号分隔多个分支。当公共逻辑被一些分支共享时，我们可以将它们组合成一个分支。在下面的例子中，我们需要检查输入的大天体是否是行星，所以我们将所有行星的名称组合在一个分支中。除了行星名称之外的任何输入都将执行 else 分支。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
import java.util.Scanner;
fun main(args: Array<String>) {
    var reader = Scanner(System.`in`)
    print("Enter name of planet: ")
    var name = reader.next()
    when(name) {
        "Mercury","Earth","Mars","Jupiter"
            ,"Neptune","Saturn","Venus","Uranus" -> println("Planet")
        else -> println("Neither planet nor star")
    }
}
```

**输出:**

```kt
Enter name of planet: Earth
Planet
```

**使用**或**中的**检查输入值是否在范围内–**
！在**运算符中，我们可以检查在阻塞时传入的参数范围。Kotlin 中的 in 运算符用于检查某个范围内特定变量或属性的存在性。如果参数位于特定范围内，那么在运算符中返回 true，如果参数不位于特定范围内，那么！返回真。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
import java.util.Scanner;
fun main(args: Array<String>) {
    var reader = Scanner(System.`in`)
    print("Enter the month number of year: ")
    var num = reader.nextInt()
    when(num){
        in 1..3 -> println("It is spring season")
        in 4..6 -> println("It is summer season")
        in 7..8 ->println("It is rainy season")
        in 9..10 -> println("It is autumn season")
        in 11..12 -> println("It is winter season")
        !in 1..12 ->println("Enter valid month of year")
    }
}
```

**输出:**

```kt
Enter the month number of year: 5
It is summer season

Enter the month number of year: 14
Enter valid month of year
```

**检查给定变量是否为特定类型–**
使用**是**还是**！是**运算符我们可以在 when 块中检查作为参数传递的变量的类型。如果变量是整数类型，则为整数返回真，否则返回假。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun main(args: Array<String>) {
    var num: Any = "GeeksforGeeks"
    when(num){
        is Int -> println("It is an Integer")
        is String -> println("It is a String")
        is Double -> println("It is a Double")
    }
}
```

**输出:**

```kt
It is a String
```

**用 when 代替 if-else-if 链**–
我们可以用 when 代替 if-else-if。如果没有提供参数，那么分支条件只是布尔表达式，只有当条件为真时，分支才会被执行:

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun isOdd(x: Int) = x % 2 != 0
fun isEven(x: Int) = x % 2 == 0

fun main(args: Array<String>) {
    var num = 8
    when{
        isOdd(num) ->println("Odd")
        isEven(num) -> println("Even")
        else -> println("Neither even nor odd")
    }
}
```

**输出:**

```kt
Even
```

**检查字符串是否包含特定的前缀或后缀–**
我们也可以通过下面的方法检查给定字符串中的前缀或后缀。如果字符串包含前缀或后缀，那么它将返回布尔值 true，否则返回 false。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
fun hasPrefix(company: Any) = when (company) {
    is String -> company.startsWith("GeeksforGeeks")
    else -> false
}

fun main(args: Array<String>) {
    var company = "GeeksforGeeks a computer science portal"
    var result = hasPrefix(company)
    if(result) {
        println("Yes, string started with GeeksforGeeks")
    }
    else {
        println("No, String does not started with GeeksforGeeks")
    }
}
```

**输出:**

```kt
Yes, string started with GeeksforGeeks
```