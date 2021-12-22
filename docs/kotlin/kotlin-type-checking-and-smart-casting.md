# 柯特林|类型检查和智能铸造

> 原文:[https://www . geeksforgeeks . org/kot Lin-类型检查和智能转换/](https://www.geeksforgeeks.org/kotlin-type-checking-and-smart-casting/)

### 类型检查–

在 Kotlin 中，我们可以在运行时使用 **`is`** 运算符来检查某个变量的类型。这是一种在运行时检查变量类型的方法，以分离不同对象的流。

**使用 if-else 块进行类型检查的 Kotlin 程序-**

```kt
fun main(args: Array<String>) {
    var name = "Praveen"
    var age = 24
    var salary = 5000.55
    val employeeDetails: List<Any> = listOf(name,age,salary)

    for(attribute in employeeDetails) {
        if (attribute is String) {
            println("Name: $attribute")
        } else if (attribute is Int) {
            println("Age: $attribute")
        } else if (attribute is Double) {
            println("Salary: $attribute")
        } else {
            println("Not an attribute")
        }
    }
}
```

**输出:**

```kt
Name: Praveen
Age: 24
Salary: 5000.55

```

**说明:**
这里我们初始化三个变量*名字*、*年龄*和*工资*然后传入列表<any>。然后，借助*遍历列表进行*循环，在每个 *if-else* 块中，我们使用**是**运算符检查元素的类型，并执行相应的 **`print()`** 语句。</any>

**使用 **`when`** 表达式–**
我们可以很容易地将 *if-else* 块替换为*时的*表达式。我们已经了解了何时在控制流文章中表达。更多细节可以参考科特林中的[当表达式](https://www.geeksforgeeks.org/kotlin-when-expression/)。

**柯特林程序的类型检查使用时–**

```kt
fun main(args: Array<String>) {
    var name = "Praveen"
    var age = 24
    var salary = 5000.55
    var emp_id = 12345f
    val employeeDetails: List<Any> = listOf(name, age, salary, emp_id)

    for (attribute in employeeDetails) {
        when (attribute) {
            is String -> println("Name: $attribute ")
            is Int -> println("Age: $attribute")
            is Double -> println("Salary: $attribute")
            else -> println("Not an attribute")
        }
    }
}
```

**输出:**

```kt
Name: Praveen 
Age: 24
Salary: 5000.55
Not an attribute

```

### 智能铸造–

在 Java 或其他编程语言中，在访问变量的属性之前，需要对该变量进行**显式**类型转换，但是科特林进行了**智能**转换。一旦变量通过任何条件运算符，柯特林编译器就会自动将其转换为特定的类引用。

让我们以 Java 为例，首先，我们使用运算符的[instance 检查变量的类型，然后将其转换为目标类型，如下所示–](https://www.geeksforgeeks.org/java-instanceof-and-its-applications/)

```kt
Object ob = "GeeksforGeeks";

if(ob instanceof String) {
    // Explicit type casting
    String str = (String) ob;

    System.out.println("length of String " + str.length());
 }
```

在科特林，智能类型铸造是最有趣的功能之一。我们使用 **`is`** 或 **`!is`** 运算符检查变量的类型，编译器自动将变量强制转换为目标类型，如下所示-

```kt
fun main(args: Array<String>) {
    val str1: String? = "GeeksforGeeks"
    var str2: String? = null   // prints String is null
    if(str1 is String) {

        // No Explicit type Casting needed.
        println("length of String ${str1.length}")
    }
    else {
        println("String is null")
    }
}
```

**输出:**

```kt
length of String 13
```

**使用`!is`运算符**
同样使用 **`!is`** 运算符我们可以检查变量。

```kt
fun main(args: Array<String>) {
    val str1: String? = "GeeksforGeeks"
    var str2: String? = null  // prints String is null
    if(str1 !is String) {
        println("String is null")
    }
    else {
        println("length of String ${str1.length}")
    }
}
```

**输出:**

```kt
length of String 13
```

**注意:**当编译器不能保证变量在检查和使用之间不能改变时，智能强制转换不起作用。智能强制转换根据以下规则适用:

*   **val** 除了局部委托属性外，局部变量始终有效。
*   **val** 属性仅在属性是私有的或内部的，或者在声明属性的同一个模块中执行检查时有效。智能强制转换不适用于开放属性或具有自定义 getters 的属性。
*   **var** 局部变量只有在变量在检查和使用之间没有被修改，没有在修改它的 lambda 中被捕获，并且不是局部委托属性的情况下才起作用。
*   **var** 属性–从不工作，因为变量可以随时修改。