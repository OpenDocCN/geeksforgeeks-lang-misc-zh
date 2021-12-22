# 科特林操作员

> 原文:[https://www.geeksforgeeks.org/kotlin-operators/](https://www.geeksforgeeks.org/kotlin-operators/)

运算符是对操作数执行不同操作的特殊符号。例如+和–是分别执行加法和减法的运算符。像 Java 一样，Kotlin 包含不同种类的运算符。

*   算术运算符
*   关系运算符
*   赋值运算符
*   一元运算符
*   逻辑算子
*   逐位运算符

**算术运算符–**

<figure class="table">

| 经营者 | 意义 | 表示 | 转化为 |
| --- | --- | --- | --- |
| + | 添加 | a + b | a .加(b) |
| – | 减法 | a b | a 减 b |
| * | 增加 | a * b | a .时代(b) |
| / | 分开 | a / b | 英格兰足球俱乐部 |
| % | 系数 | a % b | a.rem(b) |

</figure>

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>)
{
    var a = 20 var b = 4 println("a + b = " + (a + b))
        println("a - b = " + (a - b))
        println("a * b = " + (a.times(b)))
        println("a / b = " + (a / b))
        println("a % b = " + (a.rem(b)))
}
```

**输出:**

```
a + b = 24
a - b = 16
a * b = 80
a / b = 5
a % b = 0
```

**关系运算符–**

<figure class="table">

| 经营者 | 意义 | 表示 | 转化为 |
| --- | --- | --- | --- |
| > | 大于 | a > b | a .比较 To(b) > 0 |
| < | 不到 | a < b | a .比较 To(b) < 0 |
| >= | 大于或等于 | a >= b | a.compareTo(b) >= 0 |
| <= | 小于或等于 | a <= b | a.compareTo(b) <= 0 |
| == | 等于 | a == b | a？。等于(b)？:(b === null) |
| ！= | 不等于 | a！= b | ！(一？。等于(b)？:(b === null)) > 0 |

</figure>

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>)
{
    var c = 30
    var d = 40
    println("c > d = "+(c>d))
    println("c < d = "+(c.compareTo(d) < 0))
    println("c >= d = "+(c>=d))
    println("c <= d = "+(c.compareTo(d) <= 0))
    println("c == d = "+(c==d))
    println("c != d = "+(!(c?.equals(d) ?: (d === null))))
}
```

**输出:**

```
c > d = false
c < d = true
c >= d = false
c <= d = true
c == d = false
c != d = true
```

**赋值运算符–**

<figure class="table">

| 经营者 | 表示 | 转化为 |
| --- | --- | --- |
| += | a = a + b | a.plusAssign(b) > 0 |
| -= | a = a–b | a .负分配(b) < 0 |
| *= | a = a * b | a . time assign(b)> = 0 |
| /= | a = a / b | a.divAssign(b) <= 0 |
| %= | a = a % b | a.remAssign(b) |

</figure>

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args : Array<String>){
 var a = 10
    var b = 5
    a+=b
    println(a)
    a-=b
    println(a)
    a*=b
    println(a)
    a/=b
    println(a)
    a%=b
    println(a)

}
```

**输出:**

```
15
10
50
10
0
```

**一元运算符–**

<figure class="table">

| 经营者 | 表示 | 转化为 |
| --- | --- | --- |
| ++ | ++a 或 a++ | a.inc() |
| — | –a 或 a– | a.dec() |

</figure>

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args : Array<String>){
    var e=10
    var flag = true
    println("First print then increment: "+ e++)
    println("First increment then print: "+ ++e)
    println("First print then decrement: "+ e--)
    println("First decrement then print: "+ --e)
}
```

**输出:**

```
First print then increment: 10
First increment then print: 12
First print then decrement: 12
First decrement then print: 10
```

**逻辑运算符–**

<figure class="table">

| 经营者 | 意义 | 表示 |
| --- | --- | --- |
| && | 如果所有表达式都为真，则返回真 | (a>b) && (a>c) |
| &#124;&#124; | 如果任何表达式为真，则返回真 | (a>b) &#124;&#124; (a>c) |
| ！ | 返回表达式的补码 | a.not() |

</figure>

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args : Array<String>){
    var x = 100
    var y = 25
    var z = 10
    var result = false
    if(x > y && x > z)
     println(x)
    if(x < y || x > z)
     println(y)
    if( result.not())
     println("Logical operators")
}
```

**输出:**

```
100
25
Logical operators
```

**按位运算符–**

<figure class="table">

| 经营者 | 意义 | 表示 |
| --- | --- | --- |
| 感觉神经性听力丧失 | 有符号左移 | a.shl(b) |
| share 分享 | 带符号右移 | a.shr(b) |
| 引导 | 无符号右移 | a.ushr() |
| 和 | 按位“与” | a 和 b |
| 或者 | 按位“或” | a.or() |
| 异或运算 | 按位异或 | a.xor() |
| （同 Inventor）发明者 | 逐位求逆 | a.inv() |

</figure>

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>)
{
    println("5 signed shift left by 1 bit: " + 5.shl(1))
    println("10 signed shift right by 2 bits: : " + 10.shr(2))
    println("12 unsigned shift right by 2 bits:  " + 12.ushr(2))
    println("36 bitwise and 22: " + 36.and(22))
    println("36 bitwise or 22: " + 36.or(22))
    println("36 bitwise xor 22: " + 36.xor(22))
    println("14 bitwise inverse is: " + 14.inv())
}
```

**输出:**

```
5 signed shift left by 1 bit: 10
10 signed shift right by 2 bits: : 2
12 unsigned shift right by 2 bits:  3
36 bitwise and 22: 4
36 bitwise or 22: 54
36 bitwise xor 22: 50
14 bitwise inverse is: -15
```