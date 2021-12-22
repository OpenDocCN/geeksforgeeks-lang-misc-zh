# 科特林数据类型

> 原文:[https://www.geeksforgeeks.org/kotlin-data-types/](https://www.geeksforgeeks.org/kotlin-data-types/)

Kotlin 中最基本的数据类型是*原始数据类型*，其他都是*引用类型*，比如数组和字符串。Java 需要使用原语数据类型的包装器(java.lang.Integer)来表现得像对象，但是 Kotlin 已经将所有数据类型都作为对象。

**Kotlin 中有不同的数据类型–**

1.  整数数据类型
2.  浮点数据类型
3.  布尔数据类型
4.  字符数据类型

**整数数据类型**:

这些数据类型包含包含整数值。

| 数据类型 | 位 | 最小值 | 最大值 |
| --- | --- | --- | --- |
| 字节 | 8 位 | -128 | One hundred and twenty-seven |
| 短的 | 16 位 | -32768 | Thirty-two thousand seven hundred and sixty-seven |
| （同 Internationalorganizations）国际组织 | 32 位 | -2147483648 | Two billion one hundred and forty-seven million four hundred and eighty-three thousand six hundred and forty-seven |
| 长的 | 64 位 | -9223372036854775808 | 9223372036854775807 |

让我们编写一个程序来表示所有整数数据类型及其最小值和最大值。

```kt
// Kotlin code
fun main(args : Array<String>) {
    var myint = 35
    //add suffix L for long integer
    var mylong = 23L

    println("My integer ${myint}")
    println("My long integer ${mylong}")

    var b1: Byte = Byte.MIN_VALUE
    var b2: Byte = Byte.MAX_VALUE
    println("Smallest byte value: " +b1)
    println("Largest byte value: " +b2)

    var S1: Short = Short.MIN_VALUE
    var S2: Short = Short.MAX_VALUE
    println("Smallest short value: " +S1)
    println("Largest short value: " +S2)

    var I1: Int = Int.MIN_VALUE
    var I2: Int = Int.MAX_VALUE
    println("Smallest integer value: " +I1)
    println("Largest integer value: " +I2)

    var L1: Long = Long.MIN_VALUE
    var L2: Long = Long.MAX_VALUE
    println("Smallest long integer value: " +L1)
    println("Largest long integer value: " +L2)
}
```

**输出:**

```kt
My integer 35
My long integer 23
Smallest byte value: -128
Largest byte value: 127
Smallest short value: -32768
Largest short value: 32767
Smallest integer value: -2147483648
Largest integer value: 2147483647
Smallest long integer value: -9223372036854775808
Largest long integer value: 9223372036854775807

```

**浮点数据类型**:

这些数据类型用于存储十进制值或小数部分。

| 数据类型 | 位 | 最小值 | 最大值 |
| --- | --- | --- | --- |
| 漂浮物 | 32 位 | 1.4984647777 | 3 . 38860+38 |
| 两倍 | 64 位 | 4 . 48860 . 8888888861 | 1 . 2008 年 12 月 20 日 |

让我们编写一个程序来表示浮点数据类型及其最小值和最大值。

```kt
// Kotlin code
fun main(args : Array<String>) {
    var myfloat = 54F                  // add suffix F for float
    println("My float value ${myfloat}")

    var F1: Float = Float.MIN_VALUE
    var F2: Float = Float.MAX_VALUE
    println("Smallest Float value: " +F1)
    println("Largest Float value: " + F2)

    var D1: Double = Double.MIN_VALUE
    var D2: Double = Double.MAX_VALUE
    println("Smallest Double value: " + D1)
    println("Largest Double value: " + D2)
}
```

**输出:**

```kt
My float value 54.0
Smallest Float value: 1.4E-45
Largest Float value: 3.4028235E38
Smallest Double value: 4.9E-324
Largest Double value: 1.7976931348623157E308

```

**布尔数据类型**:

布尔数据类型只代表一位信息**真或假**。Kotlin 中的布尔类型与 Java 中的相同。这些运算析取(||)或合取(& &)可以在布尔类型上执行。

| 数据类型 | 位 | 数据范围 |
| --- | --- | --- |
| 布尔 | 1 位 | 对还是错 |

让我们编写一个程序来表示布尔数据类型。

```kt
// Kotlin code
fun main(args : Array<String>){
  if (true is Boolean){
        print("Yes,true is a boolean value")
    }
}
```

**输出:**

```kt
Yes, true is a boolean value

```

**字符数据类型**:

字符数据类型表示小写字母(a-z)、大写字母(A-Z)、数字(0-9)等符号。

| 数据类型 | 位 | 最小值 | 最大值 |
| --- | --- | --- | --- |
| 茶 | 8 位 | -128 | One hundred and twenty-seven |

让我们编写一个程序来表示字符数据类型。

```kt
// Kotlin code
fun main(args : Array<String>){
     var alphabet: Char = 'C'
     println("C is a character : ${alphabet is Char}")
}
```

**输出:**

```kt
C is a character : true

```