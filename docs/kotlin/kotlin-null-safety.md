# 科特林零安全

> 原文:[https://www.geeksforgeeks.org/kotlin-null-safety/](https://www.geeksforgeeks.org/kotlin-null-safety/)

Kotlin 的类型系统旨在消除代码中空引用的危险，因为这是一个十亿美元的错误。 **NullPointerExceptions** 由程序在运行时抛出，有时会导致应用程序故障或系统崩溃。
如果有人用 Java 或其他有空引用概念的语言编程，那么他一定经历过代码中的**空指针异常**。如果 Kotlin 编译器在没有执行任何其他语句的情况下找到任何空引用，它也会抛出 NullPointerException。
空指针异常的可能原因如下:

*   显式调用以引发 NullPointerException()
*   使用！！操作员
*   与初始化相关的一些数据不一致，例如，未初始化的数据作为参数传递。
*   Java 互操作，例如试图访问空引用上的成员，泛型类型具有不正确的空性。

### Kotlin 中的可空和不可空类型–

Kotlin 类型系统区分了两种类型引用，一种可以保存 null(可空引用)，另一种不能保存 null(非空引用)。
字符串类型的变量不能保存**空值**。如果我们试图给变量赋空值，就会产生编译器错误。

```
var s1: String = "Geeks"
s1 = null // compilation error
```

为了允许变量为空，我们可以将变量声明为可空字符串，写成 **String？**

```
var s2: String? = "GeeksforGeeks"
s2 = null // ok
print(s2)
```

现在，如果我们想访问字符串 s1 的长度，它保证不抛出 NPE，所以我们可以放心地说:

```
val l = s1.length
```

但是如果我们想访问字符串 s2 的长度，那就不安全了，编译器会报告一个错误:

```
val l = s2.length         // error: variable 's2' can be null
```

**不可空类型的科特林程序–**

## 我的锅

```
fun main(args: Array<String>){
    // variable is declared as non-nullable
    var s1 : String = "Geeks"

    //s1 = null  // gives compiler error

    print("The length of string s1 is: "+s1.length)
}
```

**输出:**

```
The length of string s1 is: 5
```

这里，如果我们试图将 **null** 赋给一个不可为 null 的变量，那么它会给出编译器时间错误。但是，如果我们试图访问字符串的长度，那么它保证不会通过 NullPointerException。
**可空类型的科特林程序-**

## 我的锅

```
fun main(args: Array<String>) {
    // variable is declared as nullable
    var s2: String? = "GeeksforGeeks" 

    s2 = null    // no compiler error 

    println(s2.length)  // compiler error because string can be null
}
```

**输出:**

```
Error:(8, 15) Kotlin: Only safe (?.) or non-null asserted (!!.) calls are allowed on a nullable receiver of type String?
```

在这里，我们可以轻松地将 null 赋给可空类型变量。但是我们应该使用安全操作符来获取字符串的长度。

### 检查条件中的**是否为空**-

检查 null 引用的最常见方式是使用 if-else 表达式。我们可以显式检查变量是否为空，并分别处理这两个选项。
**检查空值的科特林程序–**

## 我的锅

```
fun main(args: Array<String>) {
    // variable declared as nullable
    var s: String? = "GeeksforGeeks"
    println(s)
    if (s != null) {
        println("String of length ${s.length}")
    } else {
        println("Null string")
    }
    // assign null
    s = null
    println(s)
    if (s != null) {
        println("String of length ${s.length}")
    } else {
        println("Null String")
    }
}
```

**输出:**

```
GeeksforGeeks
String of length 13
null
Null String
```

注意，我们已经使用了 **if-else** 块来检查可空性。如果字符串包含 null，则它执行 If 块，否则它执行 else 块。

### 安全呼叫操作员(？。) –

空值比较很简单，但是嵌套的 if-else 表达式的数量可能很大。科特林有安全呼叫接线员吗？。这降低了复杂性，并且仅当特定引用包含非空值时才执行操作..它允许我们在一个表达式中组合一个空值检查和一个方法调用。
以下表达式:

```
firstName?.toUpperCase()
```

相当于:

```
if(firstName != null) 
    firstName.toUpperCase()
else
    null 
```

**使用安全操作符的科特林程序–**

## 我的锅

```
fun main(args: Array<String>) {
    // variable declared as nullable
    var firstName: String? = "Praveen"
    var lastName: String? = null

    println(firstName?.toUpperCase())
    println(firstName?.length)
    println(lastName?.toUpperCase())
}
```

**输出:**

```
PRAVEEN
7
null
```

如果值不为空-
**let()方法–**
要仅在引用包含不可空值时执行操作，我们可以使用 let 运算符。仅当变量 firstName 不为空时，才会执行字母内部的 lambda 表达式。

```
val firstName: String? = null
firstName?.let { println(it.toUpperCase()) }
```

这里，变量 firstName 为空，因此不会执行 lambda 表达式来将字符串转换为大写字母。
**科特林程序的使用让–**

## 我的锅

```
fun main(args: Array<String>) {
    // created a list contains names
    var stringlist: List<String?> = listOf("Geeks","for", null, "Geeks")
    // created new list
    var newlist = listOf<String?>()
    for (item in stringlist) {
        // executes only for non-nullable values
        item?.let { newlist = newlist.plus(it) }
    }
    // to print the elements stored in newlist
    for(items in newlist){
        println(items)
    }
}
```

**输出:**

```
Geeks
for
Geeks
```

**还()方法链使用 let()–**
如果我们想要应用一些额外的操作，比如打印列表中不可为空的项目，我们可以使用**还()**方法，并使用 **let()** 或 **run()** :
链接它

## 我的锅

```
fun main(args: Array<String>) {
    // created a list contains names
    var stringlist: List<String?> = listOf("Geeks","for", null, "Geeks")
    // created new list
    var newlist = listOf<String?>()
    for (item in stringlist) {
        // executes only for non-nullable values
        item?.let { newlist = newlist.plus(it) }
        item?.also{it -> println(it)}
    }
}
```

**输出:**

```
Geeks
for
Geeks
```

**run()方法–**
科特林有一个 **run()** 方法来对可空引用执行一些操作。看起来很像 **let()** 但是在函数体内部，run()方法只有在我们使用**这个**引用而不是函数参数:
的时候才起作用

## 我的锅

```
fun main(args: Array<String>) {
    // created a list contains names
    var stringlist: List<String?> = listOf("Geeks","for", null, "Geeks")
    // created new list
    var newlist = listOf<String?>()
    for (item in stringlist) {
        // executes only for non-nullable values
        item?.run { newlist = newlist.plus(this) } // this reference
        item?.also{it -> println(it)}
    }
}
```

**输出:**

```
Geeks
for
Geeks
```

### 埃尔维斯算子(？:) –

当原始变量为空时，埃尔维斯运算符用于返回非空值或默认值。换句话说，如果左表达式不为空，那么 elvis 运算符返回它，否则返回右表达式。只有当发现左侧为空时，才会计算右侧表达式。
以下表达式:

```
val name = firstName ?: "Unknown"
```

相当于:

```
val name = if(firstName!= null) 
         firstName
      else 
         "Unknown"
```

而且我们还可以使用**抛出**和**返回**表达式在猫王操作符右侧，在函数中非常有用。因此，我们可以抛出一个异常，而不是在猫王操作符的右侧返回一个默认值。

```
val name = firstName ?: throw IllegalArgumentException("Enter valid name")
```

**使用猫王操作符的柯特林程序–**

## 我的锅

```
fun main(args: Array<String>) {
    var str : String?  = "GeeksforGeeks"
    println(str?.length)
    str = null
    println(str?.length ?: "-1")

}
```

**输出:**

```
13
-1
```

### 非空断言:！！操作员

非空断言(！！)运算符将任何值转换为非 null 类型，如果该值为 null，则引发异常。
如果有人想要 NullPointerException，那么他可以使用这个操作符显式地询问。

## 我的锅

```
fun main(args: Array<String>) {
    var str : String?  = "GeeksforGeeks"
    println(str!!.length)
    str = null
    str!!.length
}
```

**输出:**

```
13
Exception in thread "main" kotlin.KotlinNullPointerException
    at FirstappKt.main(firstapp.kt:8)
```