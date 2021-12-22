# 科特林操作员过载

> 原文:[https://www.geeksforgeeks.org/kotlin-operator-overloading/](https://www.geeksforgeeks.org/kotlin-operator-overloading/)

由于 Kotlin 提供了用户定义的类型，它还提供了额外的功能来重载标准运算符，因此使用用户定义的类型更容易。所有一元、二元、关系运算符都可以重载。操作员要么通过[成员功能](https://www.geeksforgeeks.org/kotlin-functions/)要么通过[扩展功能](https://www.geeksforgeeks.org/kotlin-extension-function/)超载。这些功能之前有**运算符**修饰符。根据使用情况，每种类型的运算符都有标准函数可以重载。

### 一元运算符–

下表显示了可以为一元运算符定义的各种函数。这些函数修改调用实例。

| 运算符表达式 | 对应函数 |
| +x | x.unaryPlus() |
| ［加在以-u 结尾的法语词源的名词之后构成复数］ | x.unaryminus 纳斯() |
| ！x | x.not() |

这里， **x** 对应于定义操作符的类型。重载功能在各自的函数中定义。

**演示一元运算符重载的 Kotlin 程序–**

```kt
class UnaryOverload(var str:String) {
    // overloading the function
    operator fun unaryMinus() {
        str = str.reversed()
    }
}
// main function
fun main(args : Array<String>) {
    val obj = UnaryOverload("HELLO")
    println("Initial string is ${obj.str}")y
    //calling the overloaded function unaryMinus()
    -obj
    println("String after applying unary operator ${obj.str}")
}
```

**输出:**

```kt
Initial string is HELLO
String after applying unary operator OLLEH

```

### 递增和递减运算符–

可以通过以下函数为类型定义递增和递减运算符。这些函数返回一个带有表达式结果的新实例。

| 运算符表达式 | 对应函数 |
| ++x | x.inc() |
| ––x | x.dec() |

无论是在后缀还是前缀符号中使用，这些函数在这两种情况下都能很好地工作，具有相同的预期输出，正如使用*前缀*或*后缀*符号时所预期的那样。

**演示操作员过载的科特林程序–**

```kt
class IncDecOverload(var str:String) {
    // overloading increment function
    operator fun inc(): IncDecOverload {
        val obj = IncDecOverload(this.str)
        obj.str = obj.str + 'a'
        return obj
    }
    // overloading decrement function
    operator fun dec(): IncDecOverload {
        val obj = IncDecOverload(this.str)
        obj.str = obj.str.substring(0,obj.str.length-1)
        return obj
    }

    override fun toString(): String {
        return str
    }
}
// main function
fun main(args: Array<String>) {
    var obj = IncDecOverload("Hello")
    println(obj++)
    println(obj--)
    println(++obj)
    println(--obj)
}
```

**输出:**

```kt
Hello
Helloa
Helloa
Hello

```

### 二进制运算符–

下表显示了要定义的二进制运算符及其等效函数。所有这些函数都会修改调用实例。

| 运算符表达式 | 对应函数 |
| x1 + x2 | x1 plus(x2) |
| x1–x2 | x1 .减(x2) |
| x1 * x2 | x1×x2 |
| x1/ x2 | x1.div(x2) |
| x1 % x2 | x1.rem(x2) |
| x1..x2 | x1 .范围(x2) |

**Kotlin 程序过载 plus 功能–**

```kt
class Object(var objName: String) {
    // Overloading the function
    operator fun plus(b: Int) {
        objName = "Name is $objName and data is $b"
    }
    override fun toString(): String {
        return objName
    }
}
// main function
fun main() {
    val obj = Object("Chair")
    // Calling the overloaded function
    obj+9
    println(obj)
}
```

**输出:**

```kt
Name is Chair and data is 9

```

**注意-** 关系运算符没有任何要定义的特定函数，要在用户定义类型的实例上使用关系运算符，该类型必须实现**可比**接口。

### 其他操作员–

Kotlin 支持多种运算符，因此为一种类型定义每种运算符并不是一种好的编程实践。下表显示了 Kotlin 可以重载的一些其他有用的运算符。

| 运算符表达式 | 对应函数 |
| x2 中的 x1 | x2 .包含(x1) |
| x1！在 x2 中 | ！x2 .包含(x1) |
| x[i] | x.get(i) |
| x[i，j] | x.get(i，j) |
| x[i] = b | x.set(i，b) |
| x[i，j] = b | x.set(i，j，b) |
| x() | x.invoke() |
| 十㈠ | x.invoke(i) |
| x(i，j) | x.invoke(i，j) |
| x1 += x2 | x1.plusAssign(x2) |
| x1 -= x2 | x1 .负分配(x2) |
| x1 *= x2 | x1 . time assign(x2) |
| x1 /= x2 | x1.divAssign(x2) |
| x1 %= x2 | x1 .重新指定(x2) |