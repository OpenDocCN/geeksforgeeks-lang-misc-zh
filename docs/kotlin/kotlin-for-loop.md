# 科特林 for loop

> 原文:[https://www.geeksforgeeks.org/kotlin-for-loop/](https://www.geeksforgeeks.org/kotlin-for-loop/)

在 Kotlin 中，循环的**相当于 C#等其他语言的 **foreach** 循环。这里 for 循环用于遍历任何提供迭代器的数据结构。它的用法与其他编程语言(如 Java 或 C)的循环非常不同。**

柯特林中循环的*语法:*

```kt
for(item in collection) {
       // code to execute
}

```

在 Kotlin 中，for 循环用于迭代以下内容，因为它们都提供了迭代器。

*   范围
*   排列
*   线
*   收藏品

### 使用 for 循环遍历*范围*

您可以遍历*范围*，因为它提供了迭代器。有许多方法可以迭代范围。用于 for 循环检查值的操作符中的**是否在范围内。
以下程序是以不同方式遍历范围的示例，**中的**是操作员检查范围内的值。如果值在范围之间，则返回 true 并打印该值。**

*   **Iterate through range to print the values:**

    ```kt
    fun main(args: Array<String>)
    {
        for (i in 1..6) {
            print("$i ")
        }
    }
    ```

    **输出:**

    ```kt
    1 2 3 4 5 6
    ```

*   **Iterate through range to jump using step-3 :**

    ```kt
    fun main(args: Array<String>)
    {
        for (i in 1..10 step 3) {
            print("$i ")
        }
    }
    ```

    **输出:**

    ```kt
    1 4 7 10
    ```

*   **You can not iterate through Range from top to down without using *DownTo* :**

    ```kt
    fun main(args: Array<String>)
    {
        for (i in 5..1) {
            print("$i ")
        }
        println("It prints nothing")
    }
    ```

    **输出:**

    ```kt
    It prints nothing
    ```

*   **Iterate through Range from top to down with using *downTo* :**

    ```kt
    fun main(args: Array<String>)
    {
        for (i in 5 downTo 1) {
            print("$i ")
        }
    }
    ```

    **输出:**

    ```kt
    5 4 3 2 1
    ```

*   **Iterate through Range from top to down with using *downTo* and *step 3*:**

    ```kt
    fun main(args: Array<String>)
    {
        for (i in 10 downTo 1 step 3) {
            print("$i ")
        }
    }
    ```

    **输出:**

    ```kt
    10 7 4 1
    ```

    ### 使用 for 循环遍历*数组*

    数组是一种包含相同数据类型(如整数或字符串)的数据结构。可以使用 for 循环遍历数组，因为它还提供了迭代器。每个数组都有一个起始索引，默认情况下，它是 0。

    您可以遍历以下数组:

    *   不使用索引属性
    *   使用索引属性
    *   与索引库函数一起使用
    *   **Traverse an array without using index property:**

        ```kt
        fun main(args: Array<String>) {
            var numbers = arrayOf(1,2,3,4,5,6,7,8,9,10)

            for (num in numbers){
                if(num%2 == 0){
                    print("$num ")
                }
            }
        }
        ```

        **输出:**

        ```kt
        2 4 6 8 10
        ```

    *   **Traverse an array with using index property:**

        ```kt
        fun main(args: Array<String>) {

            var planets = arrayOf("Earth", "Mars", "Venus", "Jupiter", "Saturn")

            for (i in planets.indices) {
                println(planets[i])
            }
        }
        ```

        **输出:**

        ```kt
        Earth
        Mars
        Venus
        Jupiter
        Saturn

        ```

    *   **Traverse an array using `withIndex()` Library Function:**

        ```kt
        fun main(args: Array<String>) {
            var planets = arrayOf("Earth", "Mars", "Venus", "Jupiter", "Saturn")

            for ((index,value) in planets.withIndex()) {
                println("Element at $index th index is $value")
            }
        }
        ```

        **输出:**

        ```kt
        Element at 0 th index is Earth
        Element at 1 th index is Mars
        Element at 2 th index is Venus
        Element at 3 th index is Jupiter
        Element at 4 th index is Saturn

        ```

### 使用 for 循环遍历*字符串*

可以使用 for 循环遍历字符串，因为它还提供了迭代器。

有以下方法可以遍历字符串:

*   不使用索引属性
*   使用索引属性
*   与索引库函数一起使用

```kt
fun main(args: Array<String>) {
    var name = "Geeks"
    var name2 = "forGeeks"

    // traversing string without using index property
    for (alphabet in name)   print("$alphabet ")

    // traversing string with using index property
    for (i in name2.indices) print(name2[i]+" ")
    println(" ")

    // traversing string using withIndex() library function
    for ((index,value) in name.withIndex())
    println("Element at $index th index is $value")
}
```

**输出:**

```kt
G e e k s f o r G e e k s  
Element at 0 th index is G
Element at 1 th index is e
Element at 2 th index is e
Element at 3 th index is k
Element at 4 th index is s

```

### 循环遍历*集合*—

您可以使用 for 循环遍历*集合*。有三种类型的收藏列表，地图和集合。
在`listOf()`功能中我们可以同时传递不同的数据类型。

**下面是使用 for 循环遍历列表的程序。**

```kt
fun main(args: Array<String>) {

    // read only, fix-size
    var collection = listOf(1,2,3,"listOf", "mapOf", "setOf")

    for (element in collection) {
        println(element)
    }
}
```

**输出:**

```kt
1
2
3
listOf
mapOf
setOf

```