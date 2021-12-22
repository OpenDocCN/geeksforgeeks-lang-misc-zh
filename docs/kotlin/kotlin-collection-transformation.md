# 科特林|收藏转化

> 原文:[https://www . geeksforgeeks . org/kot Lin-collection-transformation/](https://www.geeksforgeeks.org/kotlin-collection-transformation/)

[科特林](https://www.geeksforgeeks.org/introduction-to-kotlin/)标准库为集合*变换*提供了不同的扩展功能集。这些函数有助于根据转换定义的规则从现有集合构建新集合。

有不同数量的转换函数:

*   绘图
*   拉链
*   联合
*   变平
*   字符串表示

## 映射–

映射转换用于从一个函数在另一个集合的元素上获得的结果创建一个集合，用于映射的基函数是 **map()** 。当给定的 lambda 函数应用于每个后续元素时，它会返回 lambda 结果列表。
它保持原始集合中存储的元素的顺序。为了应用额外使用元素索引作为参数的转换，我们可以使用 **mapIndexed()** 。

**科特林绘图程序–**

```
fun main(args : Array<String>) {
    val numbers = setOf(1, 2, 3)

    // multiple all elements by 2
    println("The new elements are: "+numbers.map { it * 2 })

    // multiple idx with element
    println("The modified elements are: "+numbers.mapIndexed 
    { idx, value -> value * idx })
}
```

**输出:**

```
The new elements are: [2, 4, 6]
The modified elements are: [0, 2, 6]

```

在转换之后，如果我们在某些元素上获得空值，我们只需要调用 **mapNotNull()** 函数来代替 **map()** ，或者调用 **mapIndexedNotNull()** 来代替 **mapIndexed()** ，就可以很容易地从集合中过滤掉空值。

```
fun main(args: Array<String>) {
    val numbers = setOf(1, 2, 3)

    // filter out the null values and print
    println("Numbers without null value: "+numbers.mapNotNull
    { if ( it == 1) null else it * 2 })

    println("Numbers without null value: "+numbers.mapIndexedNotNull
    { idx, value -> if (idx == 0) null else value * idx })
}
```

**输出:**

```
Numbers without null value: [4, 6]
Numbers without null value: [2, 6]

```

## 拉链–

通过从两个集合中从相同的索引值中挑选元素，Zipping 转换有助于建立对，这可以在 **zip()** 扩展功能的帮助下完成。它可以通过传递另一个集合(数组)作为参数在一个集合或数组上调用，并返回**对**对象的列表。

来自接收集合的第一对元素和来自集合的第二对元素作为参数传递。如果集合大小不匹配，则 zip()的结果集合相当于较小大小的集合，并且较大集合的最后元素从结果中排除。也可以中缀形式 *a* zip *b* 调用。

**使用 zip()方法的 Kotlin 程序–**

```
fun main(args: Array<String>) {
    val numbers = listOf("One","Two","Three","four")
    val integers = listOf(1,2,3,4)

    // pair string number with integers
    println(numbers zip integers)

    val newInt = listOf(1,2)
    // pair string with less than numbers
    println("New pairs :"+numbers.zip(newInt))
}
```

**输出:**

```
[(One, 1), (Two, 2), (Three, 3), (four, 4)]
New pairs :[(One, 1), (Two, 2)]

```

如果我们有一个配对列表，那么我们可以在**解压**扩展函数的帮助下进行反向转换，该函数从这些配对中构建两个列表:

*   第一个列表包含原始列表中每个对的第一个元素。
*   第二个列表包含原始列表中的第二个元素。

**使用 unzip()方法的 Kotlin 程序–**

```
fun main(args: Array<String>) {
    val companies = listOf("Apple" to 1, "Google" to 2,
        "Amazon" to 3, "Facebook" to 4)

    // print after unzip the pairs
    println("Pairs unzipped: "+companies.unzip())
}
```

**输出:**

```
Pairs unzipped: ([Apple, Google, Amazon, Facebook], [1, 2, 3, 4])
```

## 关联–

关联转换有助于从集合元素及其相关联的某些值构建地图。这里，基本关联函数是 **associateWith()** ，它创建一个地图，其中原始集合元素是键，关联值是通过给定的转换函数从原始元素获得的。

**注意:**如果我们得到两个元素相等，那么只有最后一个保留在地图中。

**使用 associateWith()方法的 Kotlin 程序–**

```
fun main(args: Array<String>) {

    val captains = listOf("Kohli", "Root", "Smith", "Williamson","Root")

    // print the elements associated with their length
    println(captains.associateWith { it.length })
}
```

**输出:**

```
{Kohli=5, Root=4, Smith=5, Williamson=10}

```

## 展平–

展平转换有助于将所有嵌套集合转换为单个集合。如果我们操作嵌套集合，我们会发现提供对嵌套集合元素的平面访问的标准库函数是有用的。

基本函数是**扁平化()**，我们可以在集合的集合上调用它，例如，集合列表，然后它返回嵌套集合的所有元素的单个列表。

**使用扁平化()方法的柯特林程序–**

```
fun main(args: Array<String>) {

    val openers = listOf(setOf("Warner", "Finch") ,setOf("Roy","Bairstow")
        ,setOf("Rohit,Dhawan"),setOf("Guptill","Henry"))

    // print the elements associated with their length
    println("All the openers are: "+openers.flatten())
}
```

**输出:**

```
All the openers are: [Warner, Finch, Roy, Bairstow, Rohit,Dhawan, Guptill, Henry]

```

## 字符串表示–

字符串表示意味着我们可以以可读的格式检索集合内容。有两个函数可以将集合转换为字符串:

*   **joinToString()**
*   连接()

函数 **joinToString()** 根据提供的参数从集合元素中构建一个字符串。函数 **joinTo()** 也构建了一个字符串，但是将结果附加到给定的*可追加的*对象上。

当用缺省参数调用上述函数时，两者都返回类似于在集合上调用 **toString()** 的结果:一串由逗号和空格分隔的元素的字符串表示。

**使用字符串表示方法的柯特林程序–**

```
fun main(args: Array<String>) {
    val colors = listOf("Red","Green","Blue","Orange","Yellow")

    println(colors)
    // join all elements in a single List
    println(colors.joinToString())

    val listString = StringBuffer("Colors are: ")
    colors.joinTo(listString)
    println(listString)
}
```

**输出:**

```
[Red, Green, Blue, Orange, Yellow]
Red, Green, Blue, Orange, Yellow
Colors are: Red, Green, Blue, Orange, Yellow

```