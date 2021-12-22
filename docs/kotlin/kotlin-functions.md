# 科特林功能

> 原文:[https://www.geeksforgeeks.org/kotlin-functions/](https://www.geeksforgeeks.org/kotlin-functions/)

一个**函数**是一个执行特殊任务的代码单元。在编程中，函数用于将代码分解成更小的模块，从而使程序更易于管理。

**例如:**如果我们必须计算两个数的和，那么定义一个有趣的 **`sum()`** 。

```kt
fun sum(a: Int, b: Int): Int {
    return a + b
}

```

我们可以任意多次调用`sum(x, y)`，它会返回两个数的和。因此，函数避免了代码的重复，使代码更具可重用性。

在 Kotlin 中，有两种类型的函数-

***   Standard library function*   User defined function**

## Kotlin 标准库函数–

在 Kotlin 中，有不同数量的内置函数已经在标准库中定义并可供使用。我们可以通过根据需求传递参数来调用它们。

在下面的程序中，我们将使用内置功能*`arrayOf()`**`sum()`*和 *`println()`* 。函数 *`arrayOf()`* 需要像整数、双精度等一些参数来创建一个数组，我们可以使用不需要任何参数的 *`sum()`* 来找到所有元素的总和。

```kt
fun main(args: Array<String>) {
    var sum = arrayOf(1,2,3,4,5,6,7,8,9,10).sum()

    println("The sum of all the elements of an array is: $sum")
}
```

**输出:**

```kt
The sum of all the elements of an array is: 55
```

在下面的程序中，我们将使用 **rem()** 来寻找余数。

```kt
fun main(args: Array<String>) {
    var num1 = 26
    var num2 = 3

    var result = num1.rem(num2)
    println("The remainder when $num1 is divided by $num2 is: $result")
}
```

**输出:**

```kt
The remainder when 26 is divided by 3 is: 2

```

不同标准库函数及其使用的列表–

*   **sqrt()**–用于计算一个数的平方根。
*   **打印()**–用于将消息打印到标准输出。
*   **rem()**–求一个数除以另一个数后的余数。
*   **To int()**–将数字转换为整数值。
*   **读取线()**–用于标准输入。
*   **compare To()**–比较两个数字并返回布尔值。

## Kotlin 用户定义函数–

由用户定义的函数称为用户定义函数。众所周知，要把一个大程序分成小模块，我们需要定义函数。每个定义的函数都有自己的属性，如函数名、函数返回类型、传递给函数的参数数量等。

### 创建用户定义的函数-

在 Kotlin 中，函数可以在顶部声明，不需要创建一个类来保存函数，这是我们在其他语言(如 Java 或 Scala)中习惯做的。

通常，我们将函数定义为:

```kt
fun fun_name(a: data_type, b: data_type, ......): return_type  {
    // other codes
    return
}

```

*   **趣味**–定义功能的关键字。
*   **fun _ Name**–后来用来调用函数的函数名。
*   **a:data_type**–这里，a 是传递的参数，data _ type 像整数或字符串一样指定参数的数据类型。
*   **return _ type**–指定函数返回的数据值的类型。
*   **{…。}**–花括号代表功能块。

**柯特林函数`mul()`将两个参数类型相同的数字相乘-**

```kt
fun mul(num1: Int, num2: Int): Int {
    var number = num1.times(num2)
    return number
}
```

**说明:**我们在上面定义了一个函数，从 **fun** 关键字开始，返回类型为 Integer。

```kt
>> mul() is the name of the function
>> num1 and num2 are names of the parameters being accepted by the function
  and both are Integer type.

```

**柯特林函数`student()`具有不同类型的参数-**

```kt
fun student(name: String , roll_no: Int , grade: Char) {
    println("Name of the student is : $name")
    println("Roll no of the student is: $roll_no")
    println("Grade of the student is: $grade")
}
```

**解释-** 我们已经使用 fun 关键字定义了一个函数，默认情况下，fun 关键字的返回类型是 Unit。

```kt
>> student is the name of the function.
>> name is the parameter of String data type.
>> roll_no is the parameter of Integer data type
>> grade is the parameter of Character data type

```

### 用户定义函数的调用-

我们创建一个函数来分配特定的任务。每当调用一个函数时，程序就离开当前代码段，开始执行该函数。

**功能的流量控制-**

1.  程序进入包含函数调用的行。
2.  当函数被调用时，控制转移到该函数。
3.  逐个执行函数的所有指令。
4.  只有当函数到达右大括号或任何 return 语句时，控制才会被传递回来。
5.  函数返回的任何数据都被用来代替原始代码行中的函数。

**柯特林程序通过传递两个参数调用`mul()`函数-**

```kt
fun mul(a: Int, b: Int): Int {
    var number = a.times(b)
    return number
}
fun main(args: Array<String>) {
    var result = mul(3,5)
    println("The multiplication of two numbers is: $result")
}
```

**输出:**

```kt
The multiplication of two numbers is: 15 
```

**解释-**
在上面的程序中，我们通过传递两个参数来调用`mul(3, 5)`函数。当函数被调用时，控制转移到`mul()`并开始执行块中的语句。使用内置的**次()**计算两个数字的倍数，并存储在一个可变的数字中。然后，它退出返回整数值的函数，并控制转移回`main()`，在那里它调用`mul()`。然后我们将函数返回的值存储到可变变量结果中，`println()`将其打印到标准输出中。

**Kotlin 程序通过传递所有参数调用 student()函数-**

```kt
fun student( name: String , grade: Char , roll_no: Int) {
    println("Name of the student is : $name")
    println("Grade of the student is: $grade")
    println("Roll no of the student is: $roll_no")

}
fun main(args: Array<String>) {
    val name = "Praveen"
    val rollno = 25
    val grade = 'A'
    student(name,grade,rollno)
    student("Gaurav",'B',30)
}
```

**输出:**

```kt
Name of the student is : Praveen
Grade of the student is: A
Roll no of the student is: 25
Name of the student is : Gaurav
Grade of the student is: B
Roll no of the student is: 30

```

**解释-**
在上面的程序中，我们通过按照所需的相同顺序传递参数来调用`student()`函数。如果我们试图混淆这些参数，那么就会出现类型不匹配的错误。在第一次调用中，我们使用变量传递参数，在第二次调用中，我们传递参数值，而不存储在变量中。所以，这两种方法调用函数都是正确的。