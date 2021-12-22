# 科特林内嵌类

> 原文:[https://www.geeksforgeeks.org/kotlin-inline-classes/](https://www.geeksforgeeks.org/kotlin-inline-classes/)

自 Kotlin 1.3 版本以来，内联类由 Kotlin 引入，以克服某些类型的传统包装器的缺点。这些内联类将类型别名的优点与基本数据类型的值域相结合。

让我们假设我们正在销售一些物品，并且*成本*被定义为浮动类型。这在下面的数据类中描述

```
data class Items(val itemno: Int, val cost: float, val qty: Int)
```

如果我们支持两种类型的货币，如美元和卢比，我们需要在另一个类中重构成本。

## Java 语言(一种计算机语言，尤用于创建网站)

```
data class Items(val itemno: Int, val cost: Cost, val qty: Int)
data class Cost(val value: Float, val currency: Currency)
enum class Currency {
    RUPEE,
    DOLLAR
}
```

上述方法有两个问题:
1。内存开销
2。复杂性
这两个问题被内联类克服了

## Java 语言(一种计算机语言，尤用于创建网站)

```
data class Item(val id: Int, val price: RupeePrice, val qty: Int)
inline class RupeePrice(val price: Float) {
    inline fun toDollars(): Float = price * 71.62f
}
```

内联类必须有一个在主构造函数中初始化的属性。在运行时，内联类的实例将使用这个单一属性来表示:类的数据被*“内联”*到它的用法中(这就是“内联类”这个名字的原因)。

## 成员

它们类似于常规类，因为它们被允许声明属性和函数。然而，它们也有一定的局限性。内联类不能有 *init* 块，也不能像 *lateinit/delegated* 属性那样有复杂的可计算属性。

## Java 语言(一种计算机语言，尤用于创建网站)

```
inline class Name(val s: String) {
    val length: Int
        get() = s.length
    fun greet() {
        println("Hello, $s")
    }
}   
fun main() {
    val name = Name("Kotlin")
    name.greet() // method `greet` is called as a static method
    println(name.length) // property getter is called as a static method
}
```

## 遗产

这些类允许继承接口，但不能扩展其他类，必须是*最终*

## Java 语言(一种计算机语言，尤用于创建网站)

```
interface Printable {
    fun prettyPrint(): String
}
inline class Name(val s: String) : Printable {
    override fun prettyPrint(): String = "Let's $s!"
}   
fun main() {
    val name = Name("Kotlin")
    println(name.prettyPrint()) // Still called as a static method
}
```

## 表现

内联类可以表示为包装器或基础类型。虽然后者是首选的，但有时保留包装是有用的。无论何时作为其他类型使用，它们都必须装箱。*引用相等*没有意义，因为它既可以表示为基础值，也可以表示为包装器。

## Java 语言(一种计算机语言，尤用于创建网站)

```
interface I
inline class Foo(val i: Int) : I
fun asInline(f: Foo) {}
fun  asGeneric(x: T) {}
fun asInterface(i: I) {}
fun asNullable(i: Foo?) {}
fun  id(x: T): T = x
fun main() {
    val f = Foo(42)

    asInline(f)    // unboxed: used as Foo itself
    asGeneric(f)   // boxed: used as generic type T
    asInterface(f) // boxed: used as type I
    asNullable(f)  // boxed: used as Foo?, which is different from Foo

    // below, 'f' first is boxed (while being passed to 'id') and then unboxed (when returned from 'id')
    // In the end, 'c' contains unboxed representation (just '42'), as 'f'
    val c = id(f) 
}
```

作为一种底层类型，这些内联类可能会导致诸如平台签名崩溃之类的模糊错误。

## Java 语言(一种计算机语言，尤用于创建网站)

```
inline class UInt(val x: Int)
// Represented as 'public final void compute(int x)' on the JVM
fun compute(x: Int) { }
// Also represented as 'public final void compute(int x)' on the JVM!
fun compute(x: UInt) { }
```

为了防止这样的错误，我们使用了一个名为**的过程，在这个过程中，我们给函数名添加了一些 hashcode。因此 *fun compute(x: UInt)* 将表示为*public final void compute-(int x)*，解决了这个问题。**

## 内联类与类型别名

虽然两者可能看起来相似，但是类型别名是与底层类型赋值兼容的。此外，内联类引入了一个全新的类型，而类型别名为现有类型提供了一个替代名称

## Java 语言(一种计算机语言，尤用于创建网站)

```
typealias NameTypeAlias = String
inline class NameInlineClass(val s: String)
fun acceptString(s: String) {}
fun acceptNameTypeAlias(n: NameTypeAlias) {}
fun acceptNameInlineClass(p: NameInlineClass) {}
fun main() {
    val nameAlias: NameTypeAlias = ""
    val nameInlineClass: NameInlineClass = NameInlineClass("")
    val string: String = ""

    acceptString(nameAlias) // OK: pass alias instead of underlying type
    acceptString(nameInlineClass) // Not OK: can't pass inline class instead of underlying type

    // And vice versa:
    acceptNameTypeAlias(string) // OK: pass underlying type instead of alias
    acceptNameInlineClass(string) // Not OK: can't pass underlying type instead of inline class
}
```

> 内联类的设计是新的，没有给出兼容性保证。在 Kotlin 1.3+中，将会报告一个警告，表明此功能是实验性的。为了消除这一点，我们必须通过传递编译器参数-Xinline-class 来选择使用这个实验特性。