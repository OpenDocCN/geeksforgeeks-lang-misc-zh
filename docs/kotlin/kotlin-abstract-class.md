# 科特林抽象类

> 原文:[https://www.geeksforgeeks.org/kotlin-abstract-class/](https://www.geeksforgeeks.org/kotlin-abstract-class/)

在柯特林中，抽象类是用类前面的 **`abstract`** 关键字声明的。抽象类不能实例化意味着我们不能为抽象类创建对象。

**抽象类声明:**

```
abstract class className {
    .........
} 

```

**需要记住的点:**

1.  我们不能为抽象类创建对象。
2.  默认情况下，抽象类的所有变量(属性)和成员函数都是非抽象的。因此，如果我们想要覆盖子类中的这些成员，那么我们需要使用 **`open`** 关键字。
3.  如果我们将一个成员函数声明为抽象的，那么我们不需要用 **`open`** 关键字进行注释，因为这些关键字在默认情况下是打开的。
4.  抽象成员函数没有主体，必须在派生类中实现。

抽象类可以包含抽象和非抽象成员，如下所示:

```
abstract class className(val x: String) {   // Non-Abstract Property

    abstract var y: Int      // Abstract Property

    abstract fun method1()   // Abstract Methods

    fun method2() {          // Non-Abstract Method
        println("Non abstract function")
    }
}

```

**在抽象类中同时使用抽象和非抽象成员的 Kotlin 程序-**

```
//abstract class
abstract class Employee(val name: String,val experience: Int) {   // Non-Abstract
                                                                  // Property
    // Abstract Property (Must be overridden by Subclasses)
    abstract var salary: Double

    // Abstract Methods (Must be implemented by Subclasses)
    abstract fun dateOfBirth(date:String)

    // Non-Abstract Method
    fun employeeDetails() {
        println("Name of the employee: $name")
        println("Experience in years: $experience")
        println("Annual Salary: $salary")
    }
}
// derived class
class Engineer(name: String,experience: Int) : Employee(name,experience) {
    override var salary = 500000.00
    override fun dateOfBirth(date:String){
        println("Date of Birth is: $date")
    }
}
fun main(args: Array<String>) {
    val eng = Engineer("Praveen",2)
    eng.employeeDetails()
    eng.dateOfBirth("02 December 1994")
}
```

**输出:**

```
Name of the employee: Praveen
Experience in years: 2
Annual Salary: 500000.0
Date of Birth is: 02 December 1994

```

**说明:**
在上面的程序中，*工程师*类是从*员工*类派生出来的。为工程师类实例化一个对象 **`eng`** 。我们在创建主构造函数时向它传递了两个参数。这会初始化 Employee 类的非抽象属性**名称**和**体验**。这

那么 **`employeeDetails()`** 的方法就叫做使用 **`eng`** 的对象。它将打印员工的姓名、经验和被覆盖的工资值。

最后，使用 **`eng`** 对象调用 **`dateOfBirth()`** ，我们已经将参数日期传递给了主构造函数。它覆盖了 Employee 类的抽象乐趣，并将作为参数传递的值打印到标准输出中。

### 用抽象成员重写非抽象开放成员–

在 Kotlin 中，我们可以使用 override 关键字覆盖开放类的非抽象开放成员函数，然后在抽象类中使用一个抽象。在下面的程序中，我们将做到这一点。

**用抽象类覆盖非抽象开放函数的柯特林程序–**

```
open class Livingthings {
    open fun breathe() {
        println("All living things breathe")
    }
}
abstract class Animal : Livingthings() {
    override abstract fun breathe()
}
class Dog: Animal(){
    override fun breathe() {
        println("Dog can also breathe")
    }
}
fun main(args: Array<String>){
    val lt = Livingthings()
    lt.breathe()
    val d = Dog()
    d.breathe()
}
```

**输出:**

```
All living things breathe
Dog can also breathe

```

### 多个派生类–

抽象类的抽象成员可以在所有派生类中被重写。在程序中，我们覆盖了三个计算器派生类中的 **`cal`** 函数。

**在多个派生类中重写抽象函数的柯特林程序–**

```
// abstract class
abstract class Calculator {
    abstract fun cal(x: Int, y: Int) : Int
}
// addition of two numbers
class Add : Calculator() {
    override fun cal(x: Int, y: Int): Int {
        return x + y
    }
}
// subtraction of two numbers
class Sub : Calculator() {
    override fun cal(x: Int, y: Int): Int {
        return x - y
    }
}
// multiplication of two numbers
class Mul : Calculator() {
    override fun cal(x: Int, y: Int): Int {
        return x * y
    }
}
fun main(args: Array<String>) {
    var add: Calculator = Add()
    var x1 = add.cal(4, 6)
    println("Addition of two numbers $x1")
    var sub: Calculator = Sub()
    var x2 = sub.cal(10,6)
    println("Subtraction of two numbers $x2")
    var mul: Calculator = Mul()
    var x3 = mul.cal(20,6)
    println("Multiplication of two numbers $x3")
}
```

**输出:**

```
Addition of two numbers 10
Subtraction of two numbers 4
Multiplication of two numbers 120
Division of two numbers 3

```