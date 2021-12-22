# 科特林可比界面

> 原文:[https://www . geesforgeks . org/compatible-interface-in-kot Lin/](https://www.geeksforgeeks.org/comparable-interface-in-kotlin/)

由于 **Kotlin** 为程序员提供了根据类定义新类型的方法，因此必须有一种方法来比较这些类的实例。和 Java 一样，[可比接口](https://www.geeksforgeeks.org/comparable-vs-comparator-in-java/)提供了一个 **compareTo()** 函数来比较两个对象。Kotlin 通过**可比界面**提供此功能。然而，它也提供了某些[扩展功能](https://www.geeksforgeeks.org/kotlin-extension-function/)，这提供了更多的功能。Kotlin 还提供了一个额外的优势，即实现 Comparable 接口的实例可以使用[关系运算符](https://www.geeksforgeeks.org/kotlin-operators/)进行比较。

### 功能–

**compare to()–**
这个函数比较调用对象和传递的对象。它返回**零**，如果两者相等，如果传递的对象更大，则返回一个**负**数，否则返回一个**正**数。

```
abstract operator fun compareTo(other: T): Int

```

### 扩展功能–

**强制至少()–**
该函数检查调用对象是否大于某个最小对象。如果大于当前对象，则返回当前对象，否则返回最小对象

```
fun <T : Comparable> T.coerceAtLeast(minimumValue: T): T

```

**强制大气()–**
该函数检查调用对象是否比给定的最大对象小**。如果当前对象较小，则返回当前对象，否则返回最大对象。**

```
fun <T : Comparable> T.coerceAtMost(maximumValue: T): T 
```

****胁迫()–**
该功能检查调用对象是否在某个**最小值**和**最大值**范围内。如果对象在该范围内，则返回该对象，否则如果对象小于最小值，则返回最小值，否则返回最大值。**

```
fun <T : Comparable> T.coerceIn(
    minimumValue: T?, 
    maximumValue: T?
): T 
```

****演示可比界面的示例–****

```
class Rectangle(val length: Int, val breadth: Int): Comparable<Rectangle>{
    override fun compareTo(other: Rectangle): Int {
        val area1 = length * breadth
        val area2 = other.length * other.breadth

        // Comparing two rectangles on the basis of area
        if(area1 == area2){
            return 0;
        }else if(area1 < area2){
            return -1;
        }
        return 1;
    }
}

fun main(){
    var obj1 = Rectangle(5,5)
    var obj2 = Rectangle(4,4)
    var min = Rectangle(2,2)
    var max = Rectangle(9,9)

    // Using relational operator compare two rectangles
    println("Is rectangle one greater than equal"+
                " to rectangle two? ${obj1>obj2}")
    println("Is rectangle one greater than the " +
            "minimum sized rectangle? ${obj1.coerceAtLeast(min) == obj1} ")

    obj2 = Rectangle(10,10)
    println("Is rectangle two smaller than " +
            "the maximum sized rectangle? ${obj2.coerceAtMost(max) == obj2}")

    println("Is rectangle one within " +
            "the bounds? ${obj1.coerceIn(min,max) == obj1}")
}
```

****输出:****

```
Is rectangle one greater than equal to rectangle two? true
Is rectangle one greater than the minimum sized rectangle? true 
Is rectangle two smaller than the maximum sized rectangle? false
Is rectangle one within the bounds? true 
```

****range to()–**
该功能检查数值是否在范围内。如果在范围内找不到值，则返回 false，否则返回 true。这里的数字是根据 IEEE-754 标准进行比较的。**

```
operator fun <t :="" comparable="">> T.rangeTo(
    that: T
): ClosedRange</t>
```

****使用 rangeTo()函数的 Kotlin 程序–****

```
fun main(args : Array<String>) {
    val range = 1..1000
    println(range)

    println("Is 55 within the range? ${55 in range}") // true
    println("Is 100000 within the range? ${100000 in range}") // false
}
```

****输出:****

```
1..1000
Is 55 within the range? true
Is 100000 within the range? false 
```