# 科特林三连

> 原文:[https://www.geeksforgeeks.org/triple-in-kotlin/](https://www.geeksforgeeks.org/triple-in-kotlin/)

在编程中，我们调用[函数](https://www.geeksforgeeks.org/kotlin-functions/)来执行特定的任务。关于函数最好的一点是我们可以调用它任何次数，并且它在计算后返回一些值，即如果我们有 **add()** 函数，那么它总是返回输入的两个数字的总和。但是，函数有一些限制，比如函数一次只返回一个值。如果需要返回不同数据类型的多个值，那么我们可以创建一个类，并声明我们希望从函数返回的所有变量，然后创建该类的一个对象，并轻松地在列表中收集所有返回值。**主要问题**是，如果程序中有太多函数一次返回多个值，那么我们必须为所有这些函数创建一个单独的类，并最终使用该类。这个过程增加了程序的冗长性和复杂性。为了应对这些类型的问题，科特林引入了**对**和**三重**的概念。

### 什么是三重？

Kotlin 语言提供了一种简单的数据类型，可以在单个实例中存储三个值。这可以使用称为**三重**的数据类来完成。存储任意三个值的是一个简单的[泛型类](https://www.geeksforgeeks.org/kotlin-generics/)，三个值之间的关系没有任何有价值的意义。两个三元组对象之间的比较是基于**值**进行的，即只有当所有三个分量相等时，两个三元组才相等。

**类别定义:**

```kt
data class Triple<out A, out B, out C> : Serializable
```

有三个**参数:**

*   ****第一个值的类型****
*   ****B–**第二个值的类型**
*   ****C–**类型的第三个值**

### **构造器**

**在柯特林中，[构造函数](https://www.geeksforgeeks.org/kotlin-constructor/)是一个特殊的成员函数，在创建类的对象时调用，主要用于初始化变量或属性。要创建三元组的新实例，我们使用:**

```kt
Triple(first: A, second: B, third: C)
```

****使用构造函数创建三元组的 Kotlin 示例:****

## **我的锅**

```kt
fun main() {
    val (x, y, z) = Triple(1, "Geeks", 2.0)
    println(x)
    println(y)
    println(z)
}
```

****输出:****

```kt
1
Geeks
2.0
```

### **性能**

**我们可以在单个变量中接收三元组的值，也可以使用**第一**、**第二**和**第三**属性来提取值。**

*   ****第一个**:该字段存储配对的第一个值。**
*   ****秒**:该字段存储配对的第二个值。**
*   ****第三个**:该字段存储配对的第三个值。**

****使用属性**检索三元组值的科特林程序**

## **我的锅**

```kt
fun main() {
    // declare triple
    var triple = Triple("Hello Geeks",
                        "This is Kotlin tutorial",
                        listOf(10, 20, 30))
    println(triple.first)
    println(triple.second)
    println(triple.third)
}
```

****输出:****

```kt
Hello Geeks
This is Kotlin tutorial
[10, 20, 30]
```

### **功能**

****toString():** 这个函数返回与 Triple 等价的字符串。**

```kt
fun toString(): String
```

****科特林程序的使用功能:****

## **我的锅**

```kt
fun main() {
    // first triple
    val triple = Triple(5, 5, 5)
    println("String representation is "+triple.toString())

      // second triple
    val triple2 = Triple("Geeks",
                         listOf("Praveen", "Gaurav", "Abhi"),
                         12345)
    print("Another string representation is "+ triple2.toString())
}
```

****输出:****

```kt
String representation is (5, 5, 5)
Another string representation is (Geeks, [Praveen, Gaurav, Abhi], 12345)
```

### **扩展函数**

**正如我们在之前的文章中了解到的那样，[扩展函数](https://www.geeksforgeeks.org/kotlin-extension-function/)提供了向现有类添加更多功能的能力，而无需继承它们。**

****toList():** 该函数返回给定三元组的列表等价物。**

```kt
fun <T>Triple<T, T, T>.toList(): List<T>
```

****使用扩展功能的柯特林程序:****

## **我的锅**

```kt
fun main() {
    // first triple
    var obj = Triple(1, 2, 3)
    val list1: List<Any> = obj.toList()
    println(list1)

      // second triple
    var obj2 = Triple("Hello", 2.0000 ,
                      listOf(10, 20, 30))
    val list2: List<Any> = obj2.toList()
    println(list2)
}
```

****输出:****

```kt
[1, 2, 3]
[Hello, 2.0, [10, 20, 30]]
```