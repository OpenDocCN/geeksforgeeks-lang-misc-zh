# 科特林密封班

> 原文:[https://www.geeksforgeeks.org/kotlin-sealed-classes/](https://www.geeksforgeeks.org/kotlin-sealed-classes/)

Kotlin 提供了一种重要的新型类，这种类在 Java 中是不存在的。这些被称为**密封类**。正如 sealed 这个词所暗示的，密封类符合**受限**或**有界类层次**。密封类在其中定义了一组子类。当预先知道一个类型将符合子类类型之一时，使用它。密封类通过在编译时而不是运行时限制要匹配的类型来确保类型安全。

**密封等级申报–**

```
sealed class Demo
```

要定义一个密封类，只需在类修饰符前面加上 sealed 关键字。密封类还有另一个明显的特征，默认情况下，它们的构造函数是**私有的**。

密封类是隐式的**抽象的**，因此不能被实例化。

```
sealed class Demo
fun main(args: Array)
{
    var d = Demo()     //compiler error  
} 
```

**密封级科特林程序–**

```
sealed class Demo {
    class A : Demo() {
        fun display()
        {
            println("Subclass A of sealed class Demo")
        }
    }
    class B : Demo() {
        fun display()
        {
            println("Subclass B of sealed class Demo")
        }
    }
}
fun main()
{
    val obj = Demo.B()
    obj.display()

    val obj1 = Demo.A()
    obj1.display()
}
```

**输出:**

```
Subclass B of sealed class Demo
Subclass A of sealed class Demo

```

**注意:**密封类的所有子类必须在**同一个科特林文件**中定义。但是，没有必要在密封类中定义它们，它们可以在密封类可见的任何范围内定义。

**示例:**

```
// A sealed class with a single subclass defined inside
sealed class ABC {
 class X: ABC(){...}
}

// Another subclass of the sealed class defined
class Y: ABC() {
  class Z: ABC()   // This will cause an error. Sealed class is not visible here
}

```

### 密封类，带有何时–

密封类最常用于 **`when`** 子句，因为密封类引用可以符合的类型是有限的。这完全消除了使用 *else* 子句。

**用 when 子句演示密封类的示例:**

```
// A sealed class with a string property
sealed class Fruit
    (val x: String)
{
    // Two subclasses of sealed class defined within
    class Apple : Fruit("Apple")
    class Mango : Fruit("Mango")
}

// A subclass defined outside the sealed class
class Pomegranate: Fruit("Pomegranate")

// A function to take in an object of type Fruit
// And to display an appropriate message depending on the type of Fruit
fun display(fruit: Fruit){
    when(fruit)
    {
        is Fruit.Apple -> println("${fruit.x} is good for iron")
        is Fruit.Mango -> println("${fruit.x} is delicious")
        is Pomegranate -> println("${fruit.x} is good for vitamin d")
    }
}
fun main()
{
    // Objects of different subclasses created
    val obj = Fruit.Apple()
    val obj1 = Fruit.Mango()
    val obj2 = Pomegranate()

    // Function called with different objects
    display(obj)
    display(obj1)
    display(obj2)
}
```

**输出:**

```
Apple is good for iron
Mango is delicious
Pomegranate is good for vitamin d

```