# 科特林|默认和命名参数

> 原文:[https://www . geesforgeks . org/kot Lin-default-and-named-argument/](https://www.geeksforgeeks.org/kotlin-default-and-named-argument/)

在大多数编程语言中，我们需要指定函数在调用该函数时接受的所有参数，但是在 Kotlin 中，我们不需要指定函数在调用该函数时接受的所有参数，因此它是最重要的特性之一。我们可以去掉这个约束，使参数成为可选的，即在调用函数时是否传递参数。
在柯特林中，函数**参数**用逗号分隔，并用帕斯卡符号定义，即名称:data_type。

```kt
fun fun_name(name1: data_type, name2: data_type )
```

柯特林–
有两种类型的论点

*   **默认参数**
*   **命名参数**

## 科特林默认参数–

调用函数时不需要显式指定的参数称为**默认**参数。
如果调用函数时没有传递参数，那么默认参数将用作函数参数。在其他情况下，如果在函数调用期间传递参数，则传递的参数将用作函数参数。
**有三种情况为默认参数-**

1.  调用函数时不传递任何参数
2.  调用函数时传递部分参数
3.  调用函数时传递所有参数

### 调用函数时不传递任何参数–

如果在调用函数时没有传递参数，那么默认参数将用作函数参数。我们需要在定义函数时初始化变量。
**无需传递参数即可调用 student()函数的 Kotlin 程序–**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// default arguments in function definition name, standard and roll_no
fun student(name: String="Praveen", standard: String="IX" , roll_no: Int=11) {       
    println("Name of the student is: $name")
    println("Standard of the student is: $standard")
    println("Roll no of the student is: $roll_no")
}
fun main(args: Array<String>) {
    val name_of_student = "Gaurav"
    val standard_of_student = "VIII"
    val roll_no_of_student = 25
    student()         // passing no arguments while calling student
}
```

**输出:**

```kt
Name of the student is: Praveen
Standard of the student is: IX
Roll no of the student is: 11
```

**说明:**
在上面的程序中，我们使用了接受名称、标准和 roll_no 三个参数的 student 函数，注意我们已经用一些值初始化了所有的 student 参数。它用于确保如果在调用函数时没有在 student()中传递任何内容，则这些都是默认值。因此，在上面的程序中，没有传递任何参数，所以它使用默认参数作为函数参数，并将默认值打印到标准输出中。

### 调用函数时传递部分参数–

这里有些参数是在调用函数时传递的，它们被用作函数参数。如果任何形式参数没有从函数调用中获取值，那么默认值将用于该参数。
**通过传递一些参数调用 student()函数的 Kotlin 程序–**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// default arguments in function definition name,standard and roll_no
fun student( name: String="Praveen", standard: String="IX" , roll_no: Int=11 ) {
    println("Name of the student is: $name")
    println("Standard of the student is: $standard")
    println("Roll no of the student is: $roll_no")
}
fun main(args: Array<String>) {
    val name_of_student = "Gaurav"
    val standard_of_student = "VIII"
    val roll_no_of_student = 25
    // passing only two arguments name and standard of student
    student(name_of_student,standard_of_student)
}
```

**输出:**

```kt
Name of the student is: Gaurav
Standard of the student is: VIII
Roll no of the student is: 11
```

**说明:**
在上面的程序中，我们使用了接受名称、标准和 roll_no 三个参数的 student 函数，注意我们已经用一些值初始化了所有的 student 参数。这里，我们只传递了学生的姓名和标准值。因此，对于 roll_no，它将使用默认值(11)并将所有值打印到标准输出，如上所示。

### 调用函数时传递所有参数–

这里，我们必须传递函数定义中定义的所有参数，但是实际参数的数据类型必须与形式参数的数据类型以相同的顺序匹配。
**调用 student()函数并传递所有参数的 Kotlin 程序–**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// default arguments in function definition name, standard and roll_no
fun student( name: String="Praveen", standard: String="IX" , roll_no: Int=11 ) {
    println("Name of the student is: $name")
    println("Standard of the student is: $standard")
    println("Roll no of the student is: $roll_no")
}

fun main(args: Array<String>) {
    val name_of_student = "Gaurav"
    val standard_of_student = "VIII"
    val roll_no_of_student = 25

    //passing all the arguments of student name,
    //standard and roll_no in same order as defined in function
    student(name_of_student,standard_of_student,roll_no_of_student)
}
```

**输出:**

```kt
Name of the student is: Gaurav
Standard of the student is: VIII
Roll no of the student is: 25
```

**解释:**
在上面的程序中，我们在调用 student()的时候传递了所有的参数，它覆盖了函数参数的默认值。因此，它只打印在函数调用期间传递给形式参数的值。

## 科特林命名参数–

使用默认参数时，我们面临一个问题。如果我们把参数混在一起，那么就会产生编译错误，所以我们必须按照函数声明中定义的顺序把实际参数传递给形式参数。
**通过随机顺序传递参数调用 student()的 Kotlin 程序-**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// default arguments in function definition name,standard and roll_no
fun student( name: String="Praveen", standard: String="IX" , roll_no: Int=11 ) {
    println("Name of the student is: $name")
    println("Standard of the student is: $standard")
    println("Roll no of the student is: $roll_no")
}

fun main(args: Array<String>) {
    val name_of_student = "Gaurav"
    val standard_of_student = "VIII"
    val roll_no_of_student = 25
    // passing the argument name_of_student to name
    // and roll_no_of_student to standard
    student(name_of_student,roll_no_of_student)
}
```

**输出:**

```kt
Error:(12, 29) Kotlin: Type mismatch: inferred type is Int but String was expected
```

在上面的程序中，我们没有按照函数中定义的顺序传递参数。所以，它给出了编译错误。
调用函数时使用名称传递的参数称为**名为**的参数。在调用函数时，我们必须使用传递实际参数值的形式参数的名称。
**科特林程序，用于调用带有参数名称的学生()**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// default arguments in function definition
// name,standard and roll_no
fun student( name: String="Praveen", standard: String="IX" , roll_no: Int=11 ) {
    println("Name of the student is: $name")
    println("Standard of the student is: $standard")
    println("Roll no of the student is: $roll_no")
}

fun main(args: Array<String>) {
    val name_of_student = "Gaurav"
    val standard_of_student = "VIII"
    val roll_no_of_student = 25

    // passing the arguments with name as defined in function
    student(name=name_of_student,roll_no=roll_no_of_student)
}
```

**输出:**

```kt
Name of the student is: Gaurav
Standard of the student is: IX
Roll no of the student is: 25
```

**解释:**
这里，我们将使用名称的实际参数传递给正式参数。仅对于**名称**和 **roll_no** 我们已经传递了这些值，因此它打印“学生标准”的默认值。