# 科特林仿制药

> 原文:[https://www.geeksforgeeks.org/kotlin-generics/](https://www.geeksforgeeks.org/kotlin-generics/)

**泛型**是强大的特性，允许我们定义可以使用不同数据类型访问的类、方法和属性，同时保持对**编译时**类型安全性的检查。

**创建参数化类–**
泛型类型是在类型之上参数化的类或方法。我们总是使用尖括号(**)来指定程序中的类型参数。**

**泛型类的定义如下:**

```kt
class MyClass<T>(text: T) {
    var name = text
} 
```

**要创建这样一个类的实例，我们需要提供类型参数:**

```kt
val my : MyClass<String> = Myclass<String>("GeeksforGeeks")
```

**如果可以从构造函数的参数中推断出参数，则允许省略类型参数:**

```kt
val my = MyClass("GeeksforGeeks") 
```

**这里，GeeksforGeeks 的类型是 String，所以编译器认为我们说的是 Myclass**

****仿制药的优势–****

1.  ****类型转换是不可避免的-** 不需要对对象进行类型转换。**
2.  ****类型安全-** 通用一次只允许单一类型的对象。**
3.  ****编译时安全性-** 泛型代码在编译时针对参数化类型进行检查，以避免运行时错误。**

### **我们程序中的一般用途-**

**在下面的例子中，我们创建了一个 **Company** 类，其主构造函数只有一个参数。现在，我们尝试将公司类的对象中不同类型的数据作为字符串和整数传递。Company 类的主构造函数接受字符串类型(**“geeskfurgeks”**)，但在传递整数类型( **12** )时给出编译时错误。**

****没有泛型类的 Kotlin 程序-****

```kt
class Company (text: String) {
    var x = text
    init{
        println(x)
    }
}
fun main(args: Array<String>){
    var name: Company = Company("GeeksforGeeks")
    var rank: Company = Company(12)// compile time error
}
```

****输出:****

```kt
Error:(10, 33) Kotlin: The integer literal does not conform to the expected type String 
```

**为了解决上述问题，我们可以创建一个用户定义的泛型类型类，在单个类中接受不同类型的参数。类型为**的类 Company 是一个通用类型类，同时接受 Int 和 String 类型的参数。****

******科特林程序使用泛型类-******

```kt
**class Company<T> (text : T){
    var x = text
    init{
        println(x)
    }
}
fun main(args: Array<String>){
    var name: Company<String> = Company<String>("GeeksforGeeks")
    var rank: Company<Int> = Company<Int>(12)
} **
```

******输出:******

```kt
**GeeksforGeeks
1234** 
```

### ****差异–****

****与 Java 不同，Kotlin 默认情况下使数组不变。通过扩展，泛型类型在 Kotlin 中是不变的。这可以通过关键词中的**出**和**来管理。不变性是一种属性，通过这种属性，已经为特定数据类型定义的标准泛型函数/类不能接受或返回另一种数据类型。**任何**都是所有其他数据类型的超类型。
方差为*两种*类型-******

1.  ******申报地点差异(使用进出)******
2.  ******使用部位差异:类型投影******

### ****Kotlin out 和 in 关键字–****

******关键词–******

****在 Kotlin 中，我们可以在泛型类型上使用 **`out`** 关键字，这意味着我们可以将此引用分配给它的任何超类型。`out`值只能由给定的类产生，不能消耗:****

```kt
**class OutClass<out T>(val value: T) {
    fun get(): T {
        return value
    }
}** 
```

****上面，我们已经定义了一个 **`OutClass`** 类，它可以产生一个类型为 T 的值。然后，我们可以将一个 OutClass 的实例分配给它的超类型引用:****

```kt
**val out = OutClass("string")
val ref: OutClass<Any> = out** 
```

******注意:**如果我们没有在上面的类中使用 **`out`** 类型，那么给定的语句会产生一个编译器错误。****

******关键词–******

****如果我们想将其分配给其子类型的引用，那么我们可以在泛型类型上使用 **`in`** 关键字。 **`in`** 关键字只能用于消耗的参数类型，不能用于生产的参数类型:****

```kt
**class InClass<in T> {
    fun toString(value: T): String {
        return value.toString()
    }
}** 
```

****这里，我们已经声明了一个 toString()方法，该方法只消耗一个类型为 t 的值。然后，我们可以将一个类型为 Number 的引用分配给其子类型的引用–Int:****

```kt
**val inClassObject: InClass<Number> = InClass()
val ref<Int> = inClassObject** 
```

******注意:**如果我们没有在上面的类中使用 in 类型，那么给定的语句会产生编译器错误。****

### ****协方差–****

****协方差意味着替换子类型是可接受的，但超类型是不可接受的，即泛型函数/类可以接受已经为其定义的数据类型的子类型，例如，为 Number 定义的泛型类可以接受 Int，但为 Int 定义的泛型类不能接受 Number。这可以在科特林中使用 **`out`** 关键字来实现，如下所示-****

```kt
**fun main(args: Array<String>) {
    val x: MyClass<Any> = MyClass<Int>()        // Error: Type mismatch
    val y: MyClass<out Any> = MyClass<String>() // Works since String is a subtype of Any
    val z: MyClass<out String> = MyClass<Any>() // Error since Any is a supertype of String
}
class MyClass<T>**
```

****我们可以通过将 out 关键字附加到声明站点来直接允许协方差。以下代码工作正常。****

```kt
**fun main(args: Array<String>) {
        val y: MyClass<Any> = MyClass<String>() // Compiles without error
}
class MyClass<out T>**
```

### ****反差–****

****它用于替换子类型中的超类型值，即泛型函数/类可以接受已经为其定义的数据类型的超类型，例如，为 Number 定义的泛型类不能接受 Int，但为 Int 定义的泛型类可以接受 Number。使用关键字中的**在 Kotlin 中实现如下-******

```kt
**fun main(args: Array<String>) {
        var a: Container<Dog> = Container<Animal>()  //compiles without error
        var b: Container<Animal> = Container<Dog>()  //gives compilation error
}
open class Animal
class Dog : Animal()
class Container<in T>**
```

### ****类型投影–****

****如果我们想要将某个类型的数组的所有元素复制到任意类型的数组中，那么这是可能的，但是为了允许编译器编译我们的代码，我们需要用 **`out`** 关键字注释输入参数。这使得编译器可以推断输入参数可以是任何类型的任何子类型:****

******将一个数组的元素复制到另一个数组的柯特林程序–******

```kt
**fun copy(from: Array<out Any>, to: Array<Any>) {
    assert(from.size == to.size)
    // copying (from) array to (to) array
    for (i in from.indices)
        to[i] = from[i]
    // printing elements of array in which copied
    for (i in to.indices) {
    println(to[i])
    }
}
fun main(args :Array<String>) {
    val ints: Array<Int> = arrayOf(1, 2, 3)
    val any :Array<Any> = Array<Any>(3) { "" }
    copy(ints, any)

}**
```

******输出:******

```kt
**1
2
3** 
```

### ****恒星投影–****

****当我们不知道值的具体类型，只想打印一个数组的所有元素时，我们使用星号(*)投影。****

******使用恒星投影的科特林程序–******

```kt
**// star projection in array
fun printArray(array: Array<*>) {
    array.forEach { print(it) }
}
fun main(args :Array<String>) {
    val name  = arrayOf("Geeks","for","Geeks")
    printArray(name)
}**
```

******输出:******

```kt
**GeeksforGeeks**
```