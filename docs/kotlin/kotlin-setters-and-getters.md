# 科特林沉降器和吸气剂

> 原文:[https://www.geeksforgeeks.org/kotlin-setters-and-getters/](https://www.geeksforgeeks.org/kotlin-setters-and-getters/)

属性是任何编程语言的重要组成部分。在 Kotlin 中，我们可以像声明另一个变量一样定义属性。Kotlin 属性可以使用 **var** 关键字声明为*可变*，或者使用 **val** 关键字声明为*不可变*。

### **属性的语法**

```kt
var <propertyName>[: <PropertyType>] [= <property_initializer>]
    [<getter>]
    [<setter>]
```

这里，属性**初始化器**、**获取器**和**设置器**是可选的。我们也可以省略属性**类型**，如果可以从初始值中推断出来的话。*只读*或*不可变*属性声明的语法在两个方面不同于可变属性声明:

1.  它以 ***val*** 而不是 ***var*** 开始。
2.  它不允许二传手。

```kt
fun main(args : Array) {
    var x: Int = 0
    val y: Int = 1
    x = 2 // In can be assigned any number of times
    y = 0 // It can not be assigned again
    }
```

在上面的代码中，我们试图再次为' **y'** 赋值，但是它显示了一个编译时错误，因为它不能接受更改。

### 沉降器和吸气剂

在科特林中，**设置器**用于*设置任意变量的值*，而**获取器**用于*获取值*。Getters 和 Setters 在代码中自动生成。让我们定义一个属性“**名称**”，在一个类中，**公司**。**名称**的数据类型是字符串，我们将*用一些默认值初始化*。

```kt
class Company {
var name: String = "Defaultvalue"
}
```

上面的代码相当于这个代码:

```kt
class Company {
    var name: String = "defaultvalue"
        get() = field                     // getter
        set(value) { field = value }      // setter
}
```

我们*实例化了类“公司{…}”的对象“**c”**。当我们初始化“**名称”**属性时，它被传递给设置器的*参数值*，并将“字段”设置为值。当我们试图访问对象的**名称**属性时，我们得到字段是因为这个代码 **get() =字段**。我们可以**获取**或**使用**点(。)符号**–***

```kt
val c = Company()
c.name = "GeeksforGeeks"  // access setter
println(c.name)           // access getter (Output: GeeksforGeeks)
```

### **默认设置器和获取器的 Kotlin 程序**

## 我的锅

```kt
class Company {
    var name: String = ""
        get() = field        // getter
        set(value) {         // setter
            field = value
        }
}
fun main(args: Array<String>) {
    val c = Company()
    c.name = "GeeksforGeeks"  // access setter
    println(c.name)           // access getter
}
```

**输出:**

```kt
GeeksforGeeks
```

### 值和字段标识符

我们在上面的程序中注意到了这两个标识符。

*   **值:**按照惯例，我们选择 setter 参数的名称作为**值**，但如果我们愿意，也可以选择不同的名称。**值参数**包含属性被赋予的值。在上面的程序中，我们已经将属性名初始化为**c . name**=“GeeksforGeeks”，**值参数**包含**赋值的**值“geeks forgeeks”。
*   **后备字段(field):** 允许将属性值尽可能存储在内存中。当我们**用一个值初始化**一个属性时，**的初始化值**被写入该属性的**后台字段**。在上述程序中，**值**被分配给**字段，**，然后，**字段**被分配给 **get()** 。

### 私人修饰词

如果我们希望**在公共访问中获得**方法，我们可以编写以下代码:

```kt
var name: String = ""
    private set
```

而且，由于 set 访问器附近的私有修饰符，我们只能在类内部的方法中设置名称。 **Kotlin 程序通过使用类内部的方法来设置值。**

## 我的锅

```kt
class Company () {
    var name: String = "abc"
        private set

    fun myfunc(n: String) {
        name = n             // we set the name here
    }
}

fun main(args: Array<String>) {
    var c = Company()
    println("Name of the company is: ${c.name}")
    c.myfunc("GeeksforGeeks")
    println("Name of the new company is: ${c.name}")
}
```

**输出:**

```kt
Name of the company is: abc
Name of the new comapny is: GeeksforGeeks
```

**说明:**

这里，我们使用了私有修饰符和 set。首先实例化类 Company()的一个对象，并使用 **${c.name}** 访问属性名。然后，我们在类内部定义的函数中传递名称“GeeksforGeeks”作为参数。名称属性用新名称更新，并再次访问。

### 自定义设置器和获取器

## 我的锅

```kt
class Registration( email: String, pwd: String, age: Int , gender: Char) {

    var email_id: String = email
        // Custom Getter
        get() {
           return field.toLowerCase()
        }
    var password: String = pwd
        // Custom Setter
        set(value){
            field = if(value.length > 6) value else throw IllegalArgumentException("Passwords is too small")
        }

    var age: Int = age
        // Custom Setter
        set(value) {
            field = if(value > 18 ) value else throw IllegalArgumentException("Age must be 18+")
        }
    var gender : Char = gender
        // Custom Setter
        set (value){
            field = if(value == 'M') value else throw IllegalArgumentException("User should be male")
        }
}

fun main(args: Array<String>) {

    val geek = Registration("PRAVEENRUHIL1993@GMAIL.COM","Geeks@123",25,'M')

    println("${geek.email_id}")
    geek.email_id = "GEEKSFORGEEKS@CAREERS.ORG"
    println("${geek.email_id}")
    println("${geek.password}")
    println("${geek.age}")
    println("${geek.gender}")

    // throw IllegalArgumentException("Passwords is too small")
    geek.password = "abc"   

    // throw IllegalArgumentException("Age should be 18+")
    geek.age= 5  

    // throw IllegalArgumentException("User should be male")
    geek.gender = 'F'        
}
```

**输出:**

```kt
praveenruhil1993@gmail.com
geeksforgeeks@careers.org
Geeks@123
25
M
```