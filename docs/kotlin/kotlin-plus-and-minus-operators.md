# 科特林|加减运算符

> 原文:[https://www . geesforgeks . org/kot Lin-加减运算符/](https://www.geeksforgeeks.org/kotlin-plus-and-minus-operators/)

在[柯特林](https://www.geeksforgeeks.org/introduction-to-kotlin/)、**加**和**减**操作符用于处理通常称为集合(列表、集合、地图)的对象列表。

顾名思义，*加*运算符将给定集合的元素或对象相加或连接。第一个集合的元素保持不变，第二个集合的元素与之相加，然后在新的只读集合中返回结果。

另一个*减*运算符也包含第一个集合的所有元素，但是它移除第二个集合的元素，如果它是单个元素，减运算符移除它的出现。就像加号运算符结果存储在一个新的只读集合中一样。

**语法:**

```kt
val result = collection1 + collection2
```

**Kotlin 示例演示了对元素列表使用加减运算符–**

```kt
fun main(args: Array<String>) {
    // initialize collection with string elements
    val firstcollection = listOf("three", "one", "twenty")

    // perform plus operator on list
    val plusList = firstcollection + "zero"
    // perform minus operator on list
    val minusList = firstcollection - listOf("three")
    println("Result of plus operator is : " + plusList)
    println("Result of minus operator is : " + minusList)
}
```

**输出:**

```kt
Result of plus operator is : [three, one, twenty, zero]
Result of minus operator is : [one, twenty]

```

加号和减号运算符在地图上的工作方式与其他集合略有不同。Plus 运算符返回包含两个地图元素的地图:左侧的地图和右侧的配对或其他地图。

减号运算符从左侧的映射条目创建一个映射，但带有右侧操作数的键的条目除外。

**Kotlin 示例演示了两种运算符在地图上的使用–**

```kt
fun main(args : Array<String>) {
    // create and initialize map with keys and values
    val firstMap = mapOf("one" to 1, "two" to 2, "three" to 3)
    // plus operator to add 4
    print("Result of plus operator: ")
    println(firstMap + Pair("four", 4))
    // minus operator to minus 1
    print("Result of minus operator: ")
    println(firstMap - "one")
}
```

**输出:**

```kt
{one=1, two=2, three=3, four=4}
{two=2, three=3}

```