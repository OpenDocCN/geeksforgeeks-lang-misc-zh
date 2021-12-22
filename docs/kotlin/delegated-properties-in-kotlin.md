# 科特林中的委托属性

> 原文:[https://www . geesforgeks . org/delegated-properties-in-kot Lin/](https://www.geeksforgeeks.org/delegated-properties-in-kotlin/)

授权被定义为将任何权力或权力授予另一个人(老板将任务分配给其员工)来执行不同的工作。但是，委派工作的人仍然要对委派工作的结果负责。以类似的方式，在编程语言中有各种类型的属性，每当我们想使用它们来委托其他代码工作时，我们可以手动实现它们，并且如果在我们的程序中连续使用，我们可以一劳永逸地实现它们并放入库中。

### 分类

用于委托的属性主要有 3 种类型:

**1。Lazy Properties:** Lazy 是一个 lambda 函数，它接收属性以实现输入并返回 Lazy 的一个实例，其中 T 表示用于实现 Lazy 属性的属性类型。默认情况下，lazy 是同步的，这意味着该值是在第一次调用时计算的，并且在其他调用中也会返回相同的值，我们可以使用 LazyThreadSafetyMode 停止同步。将 **【懒】(** 函数作为参数发布。

**示例:**

## 我的锅

```
// Defining an inmutable variable in kotlin
val lazyValue: String by lazy
{
  // Printing to standard output
  println("GeeksforGeeks")
  "GeeksforGeeks"
}

fun main()
{
  // Printing Var lazyValue values to standardoutput
  println(lazyValue)
  println(lazyValue)
}
```

**输出:**

```
GeeksforGeeks
GeeksforGeeks
GeeksforGeeks
```

**说明:**

这里，该值仅在“println”中计算，println 调用 lazyValue，println 中的值作为输出打印，由于同步，所有回调将看到相同的值。

**2。可观察属性:**它使用包含发生变化的信息的处理程序向用户通知类的变化。它用于在属性更改时通过回调获得通知。它包含两个用于初始化对象的参数，一个是新的属性或值(初始值)，另一个是处理程序，它包含通过将输入分配给对象而进行的所有修改的信息(它包含要分配的属性、旧值、新值)。

**示例:**

## 我的锅

```
import kotlin.properties.Delegates

class Myself
{
  // Creating a Myself Class with String variable name
  var name: String by Delegates.observable("company name")
  {
    // default Previous value "company name"
    prop, old, new ->
    println("$old -> $new") // Old value is being
                             // assigned a new value
  }
}

fun main()
{
  // Assigning name variable default value
  val V1 = Myself()

  // Assigning name variable a new value "Previous to"
  V1.name = "Previous to"

  // Now again changing "Previous to " to "New Value" value
  V1.name = "New Value"
}
```

**输出:**

```
company name -> Previous to
Previous to -> New Value
```

**说明:**
这里可观察到的属性有两个参数，初始值为**“公司名称”**，第二个是我们每次给属性赋值时调用的处理程序，有三个值为“待修改属性、前一个值和新值”。

**3。可否决:**它允许我们在用户输入的参数满足指定条件时修改值，如果用户想要拦截赋值，它可以用来代替可观察的属性。可否决就像可观察属性一样，具有附加功能，允许在满足条件时修改和通知值。

**示例:**

## 我的锅

```
var max: Int by Delegates.vetoable(0)
{
  // Defining variable max with vetoable default value as 0
  property, oldValue, newValue ->
  newValue > oldValue
}

// printing value of max valriable default zero
println(max)

// assigning new value to max variable
max = 10

// printing newly assigned value to max variable
println(max)

// assigning new value to max variable but it
// doesnot satisfy max condition
max = 5

println(max)
```

**输出:**

```
0
10
10
```

**说明:**

首先打印默认值，然后分配新的最大值，并且当由于未能满足属性而再次调用上述回调时，该值没有改变。当回调返回 true 时，这意味着属性的值被更改为新值，否则新值将被丢弃，并且属性仍包含其旧(先前)值。

**4。将属性存储在地图中:**该方法用于将属性存储在地图函数中，并将其用于动态应用。

**示例:**

## 我的锅

```
class Myself(val map: Map<String, Any?>)
{
  // defining class Myself
  val my_name: String by map // Variable my_name
  val my_age: Int     by map // Variable my_age
}

// calling Myself class using map function and
// assigning value to my_name and my_age variables
fun main()
{
  val V1 = Myself(mapOf(
        "my_name" to "GeeksforGeeks",
        "my_age"  to 50))

  // Printing value of my_name variable
  println(V1.my_name)

  // Printing value of my_age variable
  println(V1.my_age) 
}
```

**输出:**

```
GeeksforGeeks
50
```

如果使用可变映射而不是只读映射，这也适用于 var 的属性

**解释:**
这里我们创建了一个我自己类，包含一个 map 函数，用于接受字符串或任何形式(int、float、string 等)的输入，并将它们存储在我自己类中 map 函数的 my_name 和 my_age 变量中，我们还可以在任何新创建的类中动态使用 map 函数。