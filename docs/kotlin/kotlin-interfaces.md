# 科特林界面

> 原文:[https://www.geeksforgeeks.org/kotlin-interfaces/](https://www.geeksforgeeks.org/kotlin-interfaces/)

**接口**是 Kotlin 提供的自定义类型，不能直接实例化。相反，这些定义了实现类型必须遵循的行为形式。使用接口，您可以定义一组属性和方法，具体类型必须遵循和实现这些属性和方法。

### 创建接口–

Kotlin 中的接口定义以**接口**关键字开始，后面是接口名称，后面是花括号，接口成员位于花括号内。不同的是，成员没有自己的定义。这些定义将由符合要求的类型提供。

**示例:**

```
interface Vehicle()
{
  fun start()
  fun stop()
}

```

### 实现接口–

接口可以由类或对象实现。实现接口时，一致性类型必须为其所有成员提供定义。要实现一个接口，自定义类型的名称后跟一个冒号和要实现的接口的名称。

```
class Car: Vehicle

```

**演示柯特林界面的示例–**

```
interface Vehicle {
    fun start()
    fun stop()
}

class Car : Vehicle {
    override fun start()
    {
        println("Car started")
    }

    override fun stop()
    {
        println("Car stopped")
    }
}

fun main()
{
    val obj = Car()
    obj.start()
    obj.stop()
}
```

**输出:**

```
Car started
Car stopped

```

**说明:**
在本程序中，界面 Vehicle 声明了 **`start()`** 和 **`stop()`** 两种方法，需要进行覆盖。类 *Car* 使用类文字语法实现接口，并使用 override 关键字覆盖两种方法。最后，主函数创建一个 Car 类的对象，并调用这两个方法。

### 默认值和默认方法–

接口中的方法可以有**默认的**参数值。如果在函数调用时未提供参数值，则使用默认值。此外，这些方法可以有默认实现。这些用于方法被**而不是**覆盖的情况。

**演示默认值和默认方法的示例–**

```
interface FirstInterface {
    fun add(a: Int, b: Int = 5)
    fun print()
    {
        println("This is a default method defined in the interface")
    }
}
class InterfaceDemo : FirstInterface {
    override fun add(a: Int, b: Int)
    {
        val x = a + b
        println("Sum is $x")
    }

    override fun print()
    {
        super.print()
        println("It has been overridden")
    }
}

fun main()
{
    val obj = InterfaceDemo()
    println(obj.add(5))
    obj.print()
}
```

**输出:**

```
Sum is 10
This is a default method defined in the interface
It has been overridden

```

**说明:**
在上面的程序中， *FirstInterface* 定义了两种方法**`add`(**)和**`print`(**)。 *add()* 方法有两个参数，其中一个参数的默认值为 5。此外， *print()* 方法是默认实现。因此，当类 *InterfaceDemo* 实现接口时，它会覆盖这两个方法，并使用 **super** 关键字调用 print()的默认实现。此外，在 main 函数中，调用 add 方法时只指定了一个参数，因为第二个参数被赋予了默认值。

### 界面中的属性–

就像方法一样，接口也可以包含属性。然而，由于接口没有状态，它们不能被实例化，所以没有后备字段来保存它们的值。因此，接口中的字段要么是抽象的，要么是提供了一个实现。

**演示界面属性的示例–**

```
interface InterfaceProperties {
    val a : Int
    val b : String
        get() = "Hello"
}

class PropertiesDemo : InterfaceProperties {
    override val a : Int = 5000
    override val b : String = "Property Overridden"
}

fun main()
{
    val x = PropertiesDemo()
    println(x.a)
    println(x.b)
}
```

**输出:**

```
5000
Property Overridden

```

**说明:**
在上面的程序中， *InterfaceProperties* 定义了两个属性 a，a 为整数，b 为 String 类型，a 为 *getter* 。类*属性演示*实现*接口属性*并覆盖这两个属性，为它们提供值。main 函数创建类的对象，并使用点语法访问属性。

### 接口中的继承–

Kotlin 中的接口也可以继承其他接口。当一个接口扩展另一个接口时，它可以添加自己的属性和方法，实现类型必须为两个接口中的所有属性和方法提供定义。一个接口可以继承多个接口。

**演示接口继承的示例–**

```
interface Dimensions {
    val length : Double
    val breadth : Double
}

interface CalculateParameters : Dimensions {
    fun area()
    fun perimeter()
}

class XYZ : CalculateParameters {
    override val length : Double
        get() = 10.0
    override val breadth : Double
        get()= 15.0

    override fun area()
    {
        println("Area is ${length * breadth}")
    }

    override fun perimeter()
    {
        println("Perimeter is ${2*(length+breadth)}")
    }
}

fun main()
{
    val obj = XYZ()
    obj.area()
    obj.perimeter()
}
```

**输出:**

```
Area is 150.0
Perimeter is 50.0

```

**说明:**
在程序中，界面维度定义了两个属性**长度**和**宽度**。界面*计算参数*继承了维度，增加了**`area()`****`perimeter()`**两种方法。类 **XYZ** 实现*计算参数*并覆盖属性和方法，然后在主函数中调用。

### 多接口实现–

由于 Kotlin 中的类遵循单一继承的概念，即每个类只能继承一个类，但是，在接口的情况下，一个类支持多重继承，也称为 Kotlin 中的多重一致性。一个类可以实现多个接口，前提是它为接口的所有成员提供一个定义。

**演示多接口实现的示例–**

```
interface InterfaceProperties {
    val a : Int
    val b : String
        get() = "Hello"
}

interface InterfaceMethods {
    fun description()
}

class MultipleInterface : InterfaceProperties, InterfaceMethods {
    override val a : Int
        get() = 50

    override fun description()
    {
        println("Multiple Interfaces implemented")
    }
}
fun main()
{
    val obj = MultipleInterface()
    obj.description()
}
```

**输出:**

```
Multiple Interfaces implemented

```

**说明:**
在程序中定义了两个接口*接口属性*和*接口方法*。这些接口由类 *MultipleInterface* 实现，然后在主函数中调用方法。