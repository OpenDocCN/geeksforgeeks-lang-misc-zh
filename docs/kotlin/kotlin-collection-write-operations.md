# 柯特林集合写入操作

> 原文:[https://www . geeksforgeeks . org/kot Lin-collection-write-operations/](https://www.geeksforgeeks.org/kotlin-collection-write-operations/)

**集合写入操作**用于更改可变集合的内容。**可变集合**定义为具有添加和删除等写操作的集合。

*   添加元素*   移除元素和*   Updating elements

    ## 添加元素–

    **add()** 函数用于将元素添加到现有的可变集合组中。它将对象追加到集合的末尾。
    **科特林程序演示添加一个元素–**

    ```kt
    //add a single element to a list or
    //a set, use the add() function
    fun main(args: Array<String>) {
        val integers = mutableListOf(11, 12, 13, 14)
        integers.add(15)
        println(integers)
    }
    ```

    **输出:**

    ```kt
    [11, 12, 13, 14, 15]
    ```

    **addAll()** 函数用于将列表的所有元素添加到可变集合中。该参数可以是任何形式的可迭代、序列或数组。
    **科特林计划演示添加元素–**

    ```kt
    //add multiple elements to a list
    //or a set, use the addAll() function
    fun main(args: Array<String>) {
        val numbers = mutableListOf(1, 2, 5, 6)
        // add set elements to list
        numbers.addAll(2, setOf(2, 13, 14))
        println(numbers)

        // add array elements to list
        numbers.addAll(arrayOf(7, 8))
        println(numbers)
    }
    ```

    **输出:**

    ```kt
    [1, 2, 2, 13, 14, 5, 6]
    [1, 2, 2, 13, 14, 5, 6, 7, 8]

    ```

    **plussasign(+=)运算符**也用于在集合中添加元素。
    **科特林计划演示添加元素–**

    ```kt
    //add element to a list
    //or a set, use the plus operator
    fun main(args: Array<String>) {
        val list = mutableListOf("one", "two", "seven")
        list += listOf("four", "five")
        println(list)

        list += "three"
        println(list)
    }
    ```

    **输出:**

    ```kt
    [one, two, seven, four, five]
    [one, two, seven, four, five, three]

    ```

    ## 元素移除–

    **remove()** 函数用于从可变集合中删除一个元素。它移除元素的第一个匹配项。如果列表中不存在某个元素，则不移除任何内容。
    **科特林程序演示元素的移除–**

    ```kt
    //remove element to a list
    //or a set, use the remove() function
    fun main(args: Array<String>) {
        val numbers = mutableListOf(11, 22, 33, 44, 33)
        // removes first occurrence 33
        numbers.remove(33)
        println(numbers)
        // removes nothing
        numbers.remove(53)
        println(numbers)
    }
    ```

    **输出:**

    ```kt
    [11, 22, 44, 33]
    [11, 22, 44, 33]

    ```

    **removeAll()** 函数用于删除所有与参数匹配的元素。
    **科特林程序演示元素的移除–**

    ```kt
    //remove element to a list
    //or a set, use the removeAll() function
    fun main(args: Array<String>) {
        val counting = mutableSetOf("one", "two", "three", "four")
        println(counting)
        // remove all the elements passed as an argument
        counting.removeAll(setOf("one", "two", "four"))
        println(counting)
    }
    ```

    **输出:**

    ```kt
    [one, two, three, four]
    [three]

    ```

    **反赋值(- =)运算符**也用于移除集合中的元素。
    **科特林程序演示元素的移除–**

    ```kt
    //remove element to a list or a set
    fun main(args: Array<String>) {
        val counting = mutableListOf("one", "two", "three", "three", "four")
        counting -= "three"
        println(counting)
        // removes the elements
        counting -= listOf("four", "five", "two")
        println(counting)
    }
    ```

    **输出:**

    ```kt
    [one, two, three, four]
    [one, three]

    ```

    **retainal()功能**也用于移除元素。它删除条件不满足的元素。
    T4【科特林计划–

    ```kt
    //remove element to a list or a set, use the retainAll() function
    fun main(args: Array<String>) {
        val numbers = mutableListOf(11, 22, 33, 44)
        println(numbers)
        // only retain the numbers which satisfy the condition
        numbers.retainAll { it >= 33 }
        println(numbers)
    }
    ```

    **输出:**

    ```kt
    [11, 22, 33, 44]
    [33, 44]
    ```

    **清除()功能**删除所有采集元素。
    T4【科特林计划–

    ```kt
    //remove element to a list or a set, use the clear() function
    fun main(args: Array<String>) {
        val numbers = mutableListOf(12, 23, 34, 45)
        println(numbers)
        // it empty the list by removing all
        numbers.clear()
        println(numbers)
    }
    ```

    **输出:**

    ```kt
    [12, 23, 34, 45]
    []

    ```

    ## 元素的更新–

    更新元素操作也由可变集合提供。

    **运算符[]** 用于替换给定位置的元素。
    T3】科特林项目–

    ```kt
    //update element to a list 
    fun main(args: Array<String>) {
        val numbers = mutableListOf("one", "five", "three")
        numbers[1] =  "two"
        numbers[2] =  "two"
        println(numbers)
    }
    ```

    **输出:**

    ```kt
    [one, two, two]
    ```

    **fill()函数**用于将所有集合元素替换为指定值..
    T4【科特林计划–

    ```kt
    //update element to a list
    fun main(args: Array<String>) {
        val numbers = mutableListOf(1, 2, 3, 4)
        // replaces all elements by 3
        numbers.fill(3)
        println(numbers)
        // replaces all elements by 0
        numbers.fill(0)
        println(numbers)
    }
    ```

    **输出:**

    ```kt
    [3, 3, 3, 3]
    [0, 0, 0, 0]

    ```