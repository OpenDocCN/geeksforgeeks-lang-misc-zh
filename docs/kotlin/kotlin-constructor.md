# 科特林建造师

> 原文:[https://www.geeksforgeeks.org/kotlin-constructor/](https://www.geeksforgeeks.org/kotlin-constructor/)

构造函数是一种特殊的成员函数，在创建类的对象时调用，主要用于初始化变量或属性。一个类需要有一个构造函数，如果我们不声明构造函数，那么编译器会生成一个默认的构造函数。
科特林有两种类型的施工人员–

1.  **一级建造师**
2.  **二级建造师**

Kotlin 中的类最多只能有一个主构造函数和一个或多个辅助构造函数。主构造函数初始化类，而辅助构造函数用于初始化类并引入一些额外的逻辑。

### 主构造器–

使用**构造函数**关键字，在类名之后初始化主构造函数。参数在主构造函数中是可选的。

```kt
class Add constructor(val a: Int, val b: Int) {
     // code
}
```

如果没有指定注释或访问修饰符，构造函数关键字可以省略**。** 

```kt
class Add(val a: Int, val b: Int) {
     // code
}
```

****初级建造师科特林程序–**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
//main function
fun main(args: Array<String>)
{
    val add = Add(5, 6)
    println("The Sum of numbers 5 and 6 is: ${add.c}")
}
//primary constructor
class Add constructor(a: Int,b:Int)
{
    var c = a+b;
}
```

****输出:**** 

```kt
The Sum of two numbers is: 11
```

****解释:**
当我们为类创建对象 add 时，值 5 和 6 传递给构造函数。构造函数参数 a 和 b 分别用参数 5 和 6 初始化。
局部变量 c 包含变量之和。总的来说，我们使用 **${add.c}** 来访问构造函数的属性。** 

### **带有初始化程序块的主构造函数–**

**主构造函数不能包含任何代码，初始化代码可以放在一个单独的初始值设定项块中，前缀为 **init** 关键字。
**带初始化块的主构造函数的柯特林程序–**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
fun main(args: Array<String>) {
    val emp = employee(18018, "Sagnik")
}
class employee(emp_id : Int , emp_name: String) {
    val id: Int
    var name: String

    // initializer block
    init {
        id = emp_id
        name = emp_name

        println("Employee id is: $id")
        println("Employee name: $name")
    }
}
```

****输出:**** 

```kt
Employee id is: 18018
Employee name: Sagnik
```

****解释:**
为类员工创建对象 **emp** 时，将值 18018 和“Sagnik”传递给构造函数的参数 **emp_id** 和 **emp_name** 。在类 id 和名称中声明了两个属性。
Initializer 块在对象创建时执行，不仅初始化属性，还打印到标准输出。** 

### **主构造函数中的默认值–**

**类似于函数中的函数默认值，我们可以用一些默认值初始化构造函数参数。
**科特林程序中主构造函数的默认值–**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
fun main(args: Array<String>) {
    val emp = employee(18018, "Sagnik")
    // default value for emp_name will be used here
    val emp2 = employee(11011)
    // default values for both parameters because no arguments passed
    val emp3 = employee()

}
class employee(emp_id : Int = 100 , emp_name: String = "abc") {
    val id: Int
    var name: String

    // initializer block
    init {
        id = emp_id
        name = emp_name

        print("Employee id is: $id, ")
        println("Employee name: $name")
        println()
    }
}
```

****输出:**** 

```kt
Employee id is: 18018, Employee name: Sagnik

Employee id is: 11011, Employee name: abc

Employee id is: 100, Employee name: abc
```

****说明:**
这里我们用一些默认值 emp_id = 100 和 EMP _ name =“ABC”初始化了构造函数参数。
创建对象 **emp** 时，我们传递了这两个参数的值，因此它会打印这些值。
但是，在创建对象 **emp2** 时，我们没有传递 emp_name，因此初始化器块使用默认值并打印到标准输出。** 

### **二级建造师–**

**如上所述，Kotlin 可能有一个或多个二级构造函数。辅助构造函数允许初始化变量，也允许为类提供一些逻辑。它们的前缀是**构造函数**关键字。
**科特林实施二级建造师程序-**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
//main function
fun main(args: Array<String>)
{
    Add(5, 6)
}
//class with one secondary constructor
class Add
{
    constructor(a: Int, b:Int)
    {
        var c = a + b
        println("The sum of numbers 5 and 6 is: ${c}")
    }
}
```

****输出:**** 

```kt
The sum of numbers 5 and 6 is: 11
```

**将调用哪个辅助构造函数由编译器根据收到的参数决定。在上面的程序中，我们没有指定调用哪个构造函数和编译器自己决定。
**一个类中两个二级构造函数的 Kotlin 程序-**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
fun main(args: Array<String>) {
    employee(18018, "Sagnik")
    employee(11011,"Praveen",600000.5)
}
class employee {

      constructor (emp_id : Int, emp_name: String ) {
          var id: Int = emp_id
          var name: String = emp_name
          print("Employee id is: $id, ")
          println("Employee name: $name")
          println()
      }

       constructor (emp_id : Int, emp_name: String ,emp_salary : Double) {
           var id: Int = emp_id
           var name: String = emp_name
           var salary : Double = emp_salary
           print("Employee id is: $id, ")
           print("Employee name: $name, ")
           println("Employee name: $salary")
       }
}
```

****输出:**** 

```kt
Employee id is: 18018, Employee name: Sagnik

Employee id is: 11011, Employee name: Praveen, Employee name: 600000.5
```

****科特林程序一个班三个二级建造师–**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
//main function
fun main(args: Array<String>)
{
    Add(5, 6)
    Add(5, 6, 7)
    Add(5, 6, 7, 8)
}
//class with three secondary constructors
class Add
{
    constructor(a: Int, b: Int)
    {
        var c = a + b
        println("Sum of 5, 6 = ${c}")
    }
    constructor(a: Int, b: Int, c: Int)
    {
        var d = a + b + c
        println("Sum of 5, 6, 7 = ${d}")
    }
    constructor(a: Int, b: Int, c: Int, d: Int)
    {
        var e = a + b + c + d
        println("Sum of 5, 6, 7, 8 = ${e}")
    }
}
```

****输出:**** 

```kt
Sum of 5, 6 = 11
Sum of 5, 6, 7 = 18
Sum of 5, 6, 7, 8 = 26
```

### **从另一个调用一个辅助构造函数–**

**一个二级构造函数可以使用 **this()** 函数调用同一个类的另一个二级构造函数。在下面的程序中，我们使用 **this(a，b，7)** 调用了另一个构造函数，因为调用该构造函数需要三个参数。
**从一个构造函数调用另一个构造函数的柯特林程序-**** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
//main function
fun main(args: Array<String>)
{
    Add(5,6)
}
class Add {
    // calling another secondary using this
    constructor(a: Int,b:Int) : this(a,b,7) {
        var sumOfTwo = a + b
        println("The sum of two numbers 5 and 6 is: $sumOfTwo")
    }
    // this executes first
    constructor(a: Int, b: Int,c: Int) {
        var sumOfThree = a + b + c
        println("The sum of three numbers 5,6 and 7 is: $sumOfThree")
    }
}
```

****输出:**** 

```kt
The sum of three numbers 5,6 and 7 is: 18
The sum of two numbers 5 and 6 is: 11
```

### **从子类辅助构造函数调用父类辅助构造函数–**

**我们可以使用 **super** 关键字从子类调用父类的二级构造函数。在下面的程序中，我们已经展示了调用的过程。** 

## **Java 语言(一种计算机语言，尤用于创建网站)**

```kt
fun main(args: Array<String>) {
    Child(18018, "Sagnik")
}
open class Parent {
    constructor (emp_id: Int, emp_name: String, emp_salary: Double) {
        var id: Int = emp_id
        var name: String = emp_name
        var salary : Double = emp_salary
        println("Employee id is: $id")
        println("Employee name: $name")
        println("Employee salary: $salary")
        println()
    }
}
class Child : Parent {
    constructor (emp_id : Int, emp_name: String):super(emp_id,emp_name,500000.55){
        var id: Int = emp_id
        var name: String = emp_name
        println("Employee id is: $id")
        println("Employee name: $name")
    }
}
```

****输出:**** 

```kt
Employee id is: 18018
Employee name: Sagnik
Employee salary: 500000.55

Employee id is: 18018
Employee name: Sagnik
```