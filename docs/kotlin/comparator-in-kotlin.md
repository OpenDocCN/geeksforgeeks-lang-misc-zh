# 科特林的比较器

> 原文:[https://www.geeksforgeeks.org/comparator-in-kotlin/](https://www.geeksforgeeks.org/comparator-in-kotlin/)

在编程环境中，当出现对新类型的需求时，还有一个主要任务就是对一个类型的实例进行排序。为了比较一个类型的两个实例，我们实现了[可比接口](https://www.geeksforgeeks.org/comparable-interface-in-kotlin/)。然而，由于在订购实例中，它们必须被自动比较，并且由于订单可以根据各种参数而变化，Kotlin 提供了一个简单的**比较器界面**。此接口比较两个同类型的对象，并按顺序排列它们。

### 功能–

**比较:**该函数比较一个类型的两个实例，如果两个实例相等，则返回零，如果第二个实例更大，则返回负数，否则返回正数。

```kt
abstract fun compare(a: T, b: T): Int

```

### 扩展功能–

**反转:**该函数以一个比较器作为参数，返回与传递的比较器顺序相反的比较器。

```kt
fun <T> Comparator<T>.reversed(): Comparator<T>

```

**然后:**这个函数结合了两个比较器，第二个只有在根据第一个比较器的值相等时才使用。

```kt
infix fun <T> Comparator<T>.then(
    comparator: Comparator<in T>
): Comparator<T>

```

**示例演示比较、然后和反转功能。**

```kt
// A simple class to represent a name
class Name(val firstName: String,val lastName: String){
    override fun toString(): String {
        return """$firstName $lastName"""
    }
}

// A comparator to compare first names of Name
class ComparatorOne: Comparator<Name>{
    override fun compare(o1: Name?, o2: Name?): Int {
        if(o1 == null || o2 == null){
            return 0;
        }
        return o1.firstName.compareTo(o2.firstName)
    }
}

// A comparator to compare last names of Name
class AnotherComparator: Comparator<Name>{
    override fun compare(o1: Name?, o2: Name?): Int {
        if(o1 == null || o2 == null)
            return 0
        return o1.lastName.compareTo(o2.lastName)
    }
}

fun main(){
    val list = ArrayList<Name>()
    list.add(Name("Steve","Waugh"))
    list.add(Name("Steve","Smith"))
    list.add(Name("Virat","Kohli"))
    list.add(Name("Kane","Williamson"))
    list.add(Name("Joe","Root"))

    println("The list is:")
    println(list)

    val comparatorOne = ComparatorOne()
    // Sorting list according to first names
    list.sortWith(comparatorOne)
    println("List sorted according to first name")
    println(list)

    val anotherComparator = AnotherComparator()
    val finalComparator = comparatorOne.then(anotherComparator)
    // Sorting list according to first name then by last name
    list.sortWith(finalComparator)
    println("List sorted according to first name and last name")
    println(list)

    val reverseComparator = finalComparator.reversed()
    // Reverse sorting the list
    list.sortWith(reverseComparator)
    println("List reverse sorted")
    println(list)
}
```

**输出:**

```kt
The list is:
[Steve Waugh, Steve Smith, Virat Kohli, Kane Williamson, Joe Root]
List sorted according to first name
[Joe Root, Kane Williamson, Steve Waugh, Steve Smith, Virat Kohli]
List sorted according to first name and last name
[Joe Root, Kane Williamson, Steve Smith, Steve Waugh, Virat Kohli]
List reverse sorted
[Virat Kohli, Steve Waugh, Steve Smith, Kane Williamson, Joe Root]

```

**然后通过:**该函数将类型实例转换为可比较类型的实例，然后使用这些实例对它们进行比较。

```kt
fun <T> Comparator<T>.thenBy(
    selector: (T) -> Comparable<*>?
): Comparator<T>

```

**然后按降序:**该函数返回一个降序比较器，该比较器将一个值转换为可比较类型的实例，然后比较这些实例。

```kt
inline fun <T> Comparator<T>.thenByDescending(
    crossinline selector: (T) -> Comparable<*>?
): Comparator<T>

```

**演示 thenBy 和 then by 降序功能的示例**

```kt
class Person(val height: Int,val weight: Int){
    override fun toString(): String {
        return "Height = ${height}, Weight = ${weight}"
    }
}

fun main() {
    val comparator = compareBy<Person> { it.height }
    val list = listOf<Person>(
        Person(4, 10),
        Person(2, 10),
        Person(3, 45),
        Person(3, 25),
        Person(7, 95),
        Person(5, 50)
    )

    println("Sorted first according to height then by weight")
    val anotherComparator = comparator.thenBy { it.weight }
    println(list.sortedWith(anotherComparator))

    println("Sorted first according to weight then by descending order in height")
    val comparator2 = compareBy<Person> { it.weight }.thenByDescending { it.height }
    println(list.sortedWith(comparator2))
}
```

**输出:**

```kt
Sorted first according to height then by weight
[Height = 2, Weight = 10, Height = 3, Weight = 25, Height = 3, Weight = 45, Height = 4, Weight = 10, Height = 5, Weight = 50, Height = 7, Weight = 95]
Sorted first according to weight then by descending order in height
[Height = 4, Weight = 10, Height = 2, Weight = 10, Height = 3, Weight = 25, Height = 3, Weight = 45, Height = 5, Weight = 50, Height = 7, Weight = 95]

```

**然后比较器:**该函数返回一个比较器，该比较器使用主比较器和一个函数来执行比较。

```kt
fun <T> Comparator<T>.thenComparator(
    comparison: (a: T, b: T) -> Int
): Comparator<T>

```

**thenDescending:** 这个函数结合了两个比较器，第二个只在根据第一个比较器的值相等时使用，并且按照降序对元素进行排序。

```kt
infix fun <T> Comparator<T>.thenDescending(
    comparator: Comparator<in T>
): Comparator<T>

```

**演示比较器和下降功能的示例。**

```kt
fun main(){
    val list = listOf<Pair<String,Int>>(
        Pair("A",3),
        Pair("B",1),
        Pair("G",345),
        Pair("E",20),
        Pair("A",0),
        Pair("J",0)
    )

    val comparator = compareBy<Pair<String,Int>> { it.first }
        .thenComparator({a,b -> compareValues(a.second,b.second)})

    println("Pairs sorted by String then by Integers")
    println(list.sortedWith(comparator))

    val anotherComparator = compareBy<Pair<String,Int>> { it.second }
    val anotherComparator2 = compareBy<Pair<String,Int>>{it.first}
    println("Pairs sorted by Integers then by Strings in Descending order")
    println(list.sortedWith(anotherComparator.thenDescending(anotherComparator2)))
}
```

**输出:**

```kt
Pairs sorted by String then by Integers
[(A, 0), (A, 3), (B, 1), (E, 20), (G, 345), (J, 0)]
Pairs sorted by Integers then by Strings in Descending order
[(J, 0), (A, 0), (B, 1), (A, 3), (E, 20), (G, 345)]

```