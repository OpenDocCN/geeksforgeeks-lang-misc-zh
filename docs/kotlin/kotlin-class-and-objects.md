# 科特林类和对象

> 原文:[https://www.geeksforgeeks.org/kotlin-class-and-objects/](https://www.geeksforgeeks.org/kotlin-class-and-objects/)

Kotlin 支持函数式和面向对象编程。在之前的文章中，我们已经学习了函数、高阶函数以及将 Kotlin 表示为函数语言的 lambdas。在这里，我们将学习代表 Kotlin 作为面向对象编程语言的基本 OOPs 概念。
**面向对象编程语言–**
类和对象是面向对象编程语言的基本概念。这些支持 OOPs 概念继承、抽象等。

## 班级

像 Java 一样，类是具有相似属性的对象的蓝图。我们需要在创建对象之前定义一个类， **class** 关键字用于定义一个类。
类声明由类名、类头和用花括号括起来的类体组成。
**类声明语法:**

```
class className {      // class header
   // property
   // member function
}
```

**类名:**每个类都有一个特定的名字
**类头:**头由一个类的参数和构造函数组成
**类体:**用花括号括起来，包含成员函数和其他属性
头和类体都是可选的；如果花括号之间没有任何内容，那么可以省略类体。

```
class emptyClass
```

如果我们想提供一个构造函数，我们需要在类名后面紧接着写关键字**构造函数**。
**创建建造师:**

```
class className constructor(parameters) {    
   // property
   // member function
}
```

**科特林类示例–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
class employee {
    // properties
    var name: String = ""
    var age: Int = 0
    var gender: Char = 'M'
    var salary: Double = 0.toDouble()
   //member functions
   fun name(){

    }
    fun age() {

    }
    fun salary(){

    }
}
```

## 目标

它是面向对象编程的基本单元，代表现实生活中的实体，具有状态和行为。对象用于访问类的属性和成员函数。在 Kotlin 中，我们可以创建一个类的多个对象。一个对象由:
**状态**组成:它由一个对象的属性来表示。它还反映了对象的属性。
**行为**:用一个对象的方法来表示。它还反映了一个对象与其他对象的反应。
**标识**:为一个对象赋予唯一的名称，使一个对象能够与其他对象进行交互。

![](img/06fed1791993e83d95e680fbcbf1cbda.png)

**创建一个对象-**
我们可以使用类的引用创建一个对象。

```
var obj = className()
```

**访问类的属性-**
我们可以使用一个对象来访问类的属性。首先使用类引用创建一个对象，然后访问属性。

```
obj.nameOfProperty
```

**访问类的成员函数-**
我们可以使用对象访问类的成员函数。

```
obj.funtionName(parameters)
```

**创建多个对象并访问类的属性和成员函数的科特林程序–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
class employee {// Constructor Declaration of Class

    var name: String = ""
    var age: Int = 0
    var gender: Char = 'M'
    var salary: Double = 0.toDouble()

    fun insertValues(n: String, a: Int, g: Char, s: Double) {
        name = n
        age = a
        gender = g
        salary = s
        println("Name of the employee: $name")
        println("Age of the employee: $age")
        println("Gender: $gender")
        println("Salary of the employee: $salary")
    }
    fun insertName(n: String) {
        this.name = n
    }

}
fun main(args: Array<String>) {
    // creating multiple objects
    var obj = employee()
    // object 2 of class employee
    var obj2 = employee()

    //accessing the member function
    obj.insertValues("Praveen", 50, 'M', 500000.00)

    // accessing the member function
    obj2.insertName("Aliena")

    // accessing the name property of class
    println("Name of the new employee: ${obj2.name}")

}
```

**输出:**

```
Name of the employee: Praveen
Age of the employee: 50
Gender: M
Salary of the employee: 500000.0
Name of the new employee: Aliena
```