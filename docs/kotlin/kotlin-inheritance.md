# 科特林传承

> 原文:[https://www.geeksforgeeks.org/kotlin-inheritance/](https://www.geeksforgeeks.org/kotlin-inheritance/)

继承是面向对象编程中更重要的特性之一。继承使代码可重用，它允许现有类(基类)的所有特性被新类(派生类)继承。此外，派生类还可以添加一些自己的特性。

**继承语法:**

```
open class baseClass (x:Int ) {
      ..........
}
class derivedClass(x:Int) : baseClass(x) {
     ...........
}
```

在科特林，默认情况下所有职业都是**决赛**。要允许派生类从基类继承，我们必须在**基类**前面使用**打开**关键字。

**Kotlin 从基类继承属性和方法:**
当我们继承一个类时，所有的属性和函数也会被继承。我们可以在派生类中使用基类变量和函数，也可以使用派生类对象调用函数。

## 我的锅

```
//base class
open class baseClass{
    val name = "GeeksforGeeks"
    fun A(){
        println("Base Class")
    }
}
//derived class
class derivedClass: baseClass() {
    fun B() {
        println(name)           //inherit name property
        println("Derived class") 
    }
}
fun main(args: Array<String>) {
    val derived = derivedClass()
    derived.A()         // inheriting the  base class function
    derived.B()         // calling derived class function
}
```