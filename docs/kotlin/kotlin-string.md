# 科特林串

> 原文:[https://www.geeksforgeeks.org/kotlin-string/](https://www.geeksforgeeks.org/kotlin-string/)

字符数组称为字符串。 [Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) 字符串大多与 [Java 字符串](https://www.geeksforgeeks.org/strings-in-java/)相似，但有一些新的附加功能。柯特林弦也是**不变的**在本质上意味着我们不能改变弦的元素和长度。
柯特林中的字符串类定义为:

```
class String : Comparable<String>, CharSequence
```

要在 Kotlin 中声明一个字符串，我们需要使用双引号(" ")，单引号不允许定义 string。
**语法:**

```
var variable_name = "Hello, Geeks"   
or
var variable_name : String = "GeeksforGeeks"
```

**创建空字符串:**
要在 Kotlin 中创建空字符串，我们需要创建一个 String 类的实例。

```
var variable_name = String()
```

### 字符串元素和模板–

**字符串元素–**
字符串中的字符、数字或任何其他符号被称为字符串元素。我们可以使用 string[index]轻松访问字符串的元素。元素存储在从索引 0 到(string . length–1)的字符串中。
有三种方式可以访问科特林中的字符串元素–

1.  使用索引:返回指定索引处的字符。
2.  使用 get 函数:返回指定索引处作为参数传递给 get 函数的字符。
3.  迭代字符串:使用循环访问字符串中的字符。

**科特林程序访问字符串的元素–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>){
    // accessing string elements one by one
    var str = "Hello"
    println(str[0])
    println(str[1])
    println(str[2])
    println(str[3])
    println(str[4])
    // accessing the string elements using for loop
    var str2 = "Geeks"
    for(i in str2.indices){
        print(str2[i]+" ")
    }
}
```

**输出:**

```
H
e
l
l
o
G e e k s 
```

**字符串模板–**
字符串模板表达式是一段被求值的代码，其结果被返回到字符串中。两种字符串类型(转义和原始字符串)都包含模板表达式。字符串模板以美元符号$开头，它由变量名或花括号中的任意表达式组成。

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {

    var n = 10
    println("The value of n is $n")
    // using string 
    val str = "Geeks"
    println("$str is a string which length is ${str.length}")
}
```

**输出:**

```
The value of n is 10
Geeks is a string which length is 5
```

### 字符串中的一些重要属性和函数:

*   **长度:**返回字符串的长度。

```
var s =" String"
println(s.length)
```

*   **获取(索引):**返回该特定索引处的字符。

```
s.get(3) // Output: - i
```

*   **子串(开始，结束):**返回从开始到结束但不包括结束的子串。

```
s.subSequence(1, 4) // Output: - tri
```

*   **str.compareTo(字符串):**如果 str == string，则返回 0。

**使用上述属性和功能的科特林程序–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    var g = "GeeksForGeeks"
    var e = "Geeks"
    println(g.length)
    println(g.get(4))
    println(g.subSequence(0, 5))
    println(g.compareTo(e))
}
```

**输出:**

```
13
s
Geeks
8
```

### 字符串文字–

Kotlin 中有两种类型的字符串文字–

1.  转义字符串
2.  原始字符串

**转义字符串**
转义字符串用双引号(“…”来声明)并且它可能包含转义字符，如/n，/t 等。
T4【科特林程序的转义串–

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    // escaped string
    val str = "World \n is \n amazing"
    println(str)
}
```

**输出:**

```
World 
 is 
 amazing
```

**原始字符串–多行字符串**
原始字符串放在三重引号(“”…)内"")并且它没有转义字符。它提供了将字符串写入多行的功能，因此也称为多行字符串。
**科特林程序的生串–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
// raw string - multiline string
    var str = """My
        |name
        |is
        |Yash
    """.trimMargin()
    println(str)
}
```

**输出:**

```
My
name
is
Yash
```

**转义字符–**一些转义字符是:–

*   \ ":用于双引号
*   \r:用于回车
*   \n:用于换行符
*   \ ':对于单引号
*   \\:用于反斜杠
*   \t:用于选项卡
*   \b:用于退格

### 字符串相等–

Kotlin 提供了一个额外的功能，可以用两种不同的方式比较特定类型的实例。这个特性使得 Kotlin 不同于其他编程语言。
两种相等类型是–

*   结构平等
*   参照平等

**结构相等–**
结构相等通过 **==运算符**及其逆运算**进行检查！=操作员**。默认情况下，包含 **x==y** 的表达式被转换为该类型的 **equals()** 函数的调用。
**引用相等–**
柯特林中的引用相等是通过 **===运算符**及其逆运算符**来检查的！==操作员**。只有当一个类型的两个实例都指向内存中的相同位置时，该等式才返回 true。当在运行时转换为基元类型的类型上使用时，===检查被转换为==检查和！==支票被转换成！=检查。
**柯特林程序，演示结构和参照平等–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    var x = "GeeksForGeeks"
    var y = "GeeksForGeeks"
    var z = "Geeks"
    println(x===y) // true , as both are pointing to the same StringPool
    println(x==z) //false since values are not equal
    println(x===z) //false
}
```

**输出:**

```
true
false
false
```