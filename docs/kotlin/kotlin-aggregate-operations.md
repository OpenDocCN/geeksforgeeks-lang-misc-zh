# 科特林聚合操作

> 原文:[https://www.geeksforgeeks.org/kotlin-aggregate-operations/](https://www.geeksforgeeks.org/kotlin-aggregate-operations/)

**聚合操作**是对数据结构(如数组)作为一个整体执行的操作，而不是对单个元素执行的操作。

*   **count()** 函数用于返回元素个数。*   **sum()** 函数用于返回数字集合中元素的和。*   **min()** 函数用于返回最小的元素。*   **max()** 函数用于返回最大的元素。*   **average()** 函数用于返回数字集合中元素的平均值。*   **maxBy()** 函数返回一个 Collector，它根据给定的。*   **minBy()** 函数返回一个 Collector，它根据给定的。*   **maxWith()** 函数取一个 Comparator 对象，一般返回最大的元素。*   **minWith()** 函数取一个 Comparator 对象，一般返回最小的元素。*   **sumBy()** 通过使用线性代数和矩阵包功能，执行有效且可选的加权分组求和..*   **sumByDouble()** Returns the sum of all values produced by selector function applied to each element in the array..

    **使用一些聚合函数的柯特林程序–**

    ```
    //Functions that used aggregate operations
    fun main(args: Array<String>) {
        val numbers = listOf(6,34,57,78,12,4,5,5)

        println("Count the number of element in the list: ${numbers.count()}")
        println("Sum of the elements in the list: ${numbers.sum()}")
        println("Min value in the list: ${numbers.min()}")
        println("Max value in the list: ${numbers.max()}")
        println("Average of all elements in the list: ${numbers.average()}")
    }
    ```

    **输出:**

    ```
    Count the number of element in the list: 8
    Sum of the elements in the list: 201
    Min value in the list: 4
    Max value in the list: 78
    Average of all elements in the list: 25.125

    ```

    **使用 sumBy()和 sumByDouble()函数的 Kotlin 程序-**

    ```
    //Functions that used aggregate operations
    fun main(args: Array<String>) {
        val numbers = listOf(6,34,57,78,12,4,5,5)
        println("Multiply each element with 3 and sum: "+numbers.sumBy { it * 3 })
        println(numbers.sumByDouble { it.toDouble() / 2 })
    }
    ```

    **输出:**

    ```
    Multiply each element with 3 and sum: 603
    100.5

    ```

    **使用 minBy()和 maxWith()函数的 Kotlin 程序–**

    ```
    //Functions that used aggregate operations
    fun main(args: Array<String>) {
        val numbers = listOf(6,34,57,78,12,4,5,5)
        val minRem = numbers.minBy { it % 4}
        println("Minimum remainder returned by: " +minRem)

        val strings = listOf("Cricket","Football","Volley","Chess")
        val maxstrln = strings.maxWith(compareBy { it.length })
        println("String with max length is: " +maxstrln)
    }
    ```

    **输出:**

    ```
    Minimum remainder returned by: 12
    String with max length is: Football

    ```

    ## 折叠和缩小函数

    *   **fold()函数**:它以一个关联二元运算符函数为参数，将使用它来折叠集合中的元素。。
    *   **foldRight()功能**:其工作方式类似于 fold()。遍历集合中元素的顺序是从右到左。
    *   **foldIndexed()函数**:用于迭代时获取当前索引的访问权。
    *   **foldrigendeddexed()函数:**它的工作方式类似于 foldIndexed()。遍历集合中元素的顺序是从右到左
    *   **reduce()函数**将数组缩减为单个值。它为数组的每个值执行一个提供的函数。
    *   **reduceRight()函数**:其工作方式类似于 reduce()。移除集合中元素的顺序是从右到左。
    *   **reduceIndexed()函数**从第一个元素开始累加值，从左到右对当前累加器值和给定集合中每个元素及其索引应用[运算]。
    *   **reduceRightIndexed()函数:**它的工作方式类似于 reduceIndexed()。集合中的顺序是从右到左。

    **使用 fold()和 reduce()函数的 Kotlin 程序–**

    ```
    //Fold and Reduce Functions
    fun main(args: Array<String>) {
        val numbers = listOf(57,78,12,4,5,5, 42)
        val sum = numbers.reduce { sum, element -> sum + element }
        println("The sum of all elements in list "+sum)
        val sumThrice = numbers.fold(0) { sum, element -> sum + element * 3}
        println("Multiply each element with 3 and sum "+sumThrice)
    }
    ```

    **输出:**

    ```
    The sum of all elements in list 203
    Multiply each element with 3 and sum 609

    ```

    **使用 foldRight()函数的 Kotlin 程序–**

    ```
    //Fold and Reduce Functions
    fun main(args: Array<String>) {
        val numbers = listOf(6,34,57,78,12,4,5,5, 4)
        val sumThriceRight= numbers.foldRight(0){element, sum -> sum + element*3}
        println("The sum of the numbers from the right side: "+sumThriceRight)
    }
    ```

    **输出:**

    ```
    The sum of the numbers from the right side: 615
    ```

    **使用文件夹索引()和文件夹索引()的柯特林程序–**

    ```
    //Fold and Reduce Functions
    fun main(args: Array<String>) {
        val numbers = listOf(6,34,57,78,12,4,5,5, 42, 10, 4)
        val sumOfEvenNumbers = numbers.foldIndexed(0)
        { idx, sum, element -> if (idx % 2 == 0) sum + element else sum }
        println("Sum of even numbers: "+sumOfEvenNumbers)

        val sumOfEvenFromRight = numbers.foldRightIndexed(0)
        { idx, element, sum -> if (idx % 2 == 0) sum + element else sum }
        println("Sum of even numbers from Right side: "+sumOfEvenFromRight)
    }
    ```

    **输出:**

    ```
    Sum of even numbers: 126
    Sum of even numbers from Right side: 126

    ```