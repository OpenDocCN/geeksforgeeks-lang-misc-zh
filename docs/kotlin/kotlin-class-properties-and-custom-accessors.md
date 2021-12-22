# 科特林|类属性和自定义访问器

> 原文:[https://www . geesforgeks . org/kot Lin-class-properties-and-custom-accessor/](https://www.geeksforgeeks.org/kotlin-class-properties-and-custom-accessors/)

一个类最基本最重要的思想就是**封装**。将代码和数据封装成一个实体是一个属性。在 Java 中，数据存储在字段中，这些字段大多是私有的。因此，访问器方法——一个 *getter* 和一个 *setter* 被提供来让给定类的客户端访问数据。为了发送关于更改的通知或验证传递的值，setter 中还存在附加的逻辑。

### 财产

在 Java 的情况下，它是附件和字段的组合。在 Kotlin 的例子中，属性是一流的语言特性。这些功能取代了字段和访问器方法。类中的一个**属性**的声明与用 ***val*** 和 ***var*** 关键字声明变量相同。声明为 var 的属性是可变的，因此可以更改。

**定义类别:**

## 我的锅

```kt
class Abc(
    val name: String,
    val ispassed : Boolean
)
```

**可读属性:**生成一个字段和一个微不足道的获取器
**可写属性:**一个获取器、一个设置器和一个字段

基本上发生的事情是，属性的声明声明了相关的访问器(对于可写属性，setter 和 getter 都是这样，对于可读属性，getter 也是这样)。字段存储该值。

**来看看类用法**

## 我的锅

```kt
class Abc(
    val name: String,
    val ispassed : Boolean
)

fun main(args: Array<String>) {

    val abc = Abc("Bob",true)
    println(abc.name)
    println(abc.ispassed)

    /*
    In Java
    Abc abc = new Abc("Bob",true);
    System.out.println(person.getName());
    System.out.println(person.isMarried());

    */
}
```

**输出:**

```kt
Bob
true
```

在 Kotlin 中，可以在没有**新**关键字的情况下调用构造函数。不是调用 getter，而是直接引用属性。逻辑保持不变，代码更加简洁。可变属性的设置器以类似的方式工作。

### 客户访问者

属性访问器的自定义实现。

## 我的锅

```kt
class Rectangle(val height: Int, val width: Int)
{
    val isSquare: Boolean
        get() {
            return height == width
        }
}

fun main(args: Array<String>) {

    val rectangle = Rectangle(41, 43)
    println(rectangle.isSquare)    
}
```

**输出:**

```kt
false
```

属性**是正方形**不需要字段来存储值。它只有一个定制的 *getter* ，并提供了实现。每次访问该属性时，都会计算该值。