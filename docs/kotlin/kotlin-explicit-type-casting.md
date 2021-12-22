# 柯特林|显式铸造

> 原文:[https://www.geeksforgeeks.org/kotlin-explicit-type-casting/](https://www.geeksforgeeks.org/kotlin-explicit-type-casting/)

在[智能转换](https://contribute.geeksforgeeks.org/type-checking-and-smart-casting/)中，我们一般使用 **`is`** 或 **`!is`** 运算符检查变量的类型，编译器自动将变量转换为目标类型，但是在**显式类型转换**中，我们使用 **`as`** 运算符。

显式类型转换可以使用以下方法完成:

1.  不安全演职人员:**为**
2.  安全演职人员: **as？**

### 不安全的强制转换运算符:as

手动地，我们使用类型转换操作符**作为**将变量转换为目标类型。
在下面的程序中，使用**作为**运算符，将字符串类型的变量`str1`转换为目标类型。

```kt
fun main(args: Array<String>){
    val str1: String = "It works fine"
    val str2: String = str1 as String      // Works
    println(str1)
}
```

**输出:**

```kt
It works fine
```

我们可能无法将变量强制转换为目标类型，它会在运行时引发异常，这就是为什么它被称为**不安全强制转换**。
当整数类型被用于转换为字符串类型时，它抛出[类转换异常](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-class-cast-exception/index.html)。

```kt
fun main(args: Array<String>){
    val str1: Any = 11
    val str2: String = str1 as String      // throw exception
    println(str1)
}
```

**输出:**

> 线程“main”Java . lang . class castexception 中的异常:类 java.lang.Integer 不能强制转换为类 java.lang.String

我们不能将*可空*字符串强制转换为*不可空*字符串，它会抛出一个异常[typescastexception](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-class-cast-exception/index.html)。

```kt
fun main(args: Array<String>){
    val str1: String? = null
    val str2: String = str1 as String      // throw exception
    println(str1)
}
```

**输出:**

> 线程“main”kot Lin 中出现异常。typescastexception:null 不能转换为非 null 类型 kotlin。线

因此，我们必须将目标类型也用作*可空的*字符串，这样类型转换就不会抛出异常。

```kt
fun main(args: Array<String>){
    val str1: String? = null
    val str2: String? = str1 as String?      // throw exception
    println(str1)
}
```

**输出:**

```kt
null 

```

### 安全演员:as？

科特林还提供了使用安全铸造操作员 **`as?`** 进行型铸造的设施。如果无法进行强制转换，它将返回 **null** ，而不是抛出一个 ClassCastException 异常。

这里有一个例子，我们试图将程序员最初知道的 **`Any`** 类型的字符串值转换为*可空的*字符串，然后它就可以工作了。当我们用整数值初始化 **`Any`** 并试图转换成可空字符串时，这种类型的转换是不可能的，并将**空值**返回到`str3`。

```kt
fun main(args: Array<String>){

    var str1: Any = "Safe casting"
    val str2: String? = str1 as? String     // it works 
    str1 = 11
    // type casting not possible so returns null to str3
    val str3: String? = str1 as? String    
    val str4: Int? = str1 as? Int          // it works
    println(str2)
    println(str3)
    println(str4)
}
```

**输出:**

```kt
Safe casting
null
11

```