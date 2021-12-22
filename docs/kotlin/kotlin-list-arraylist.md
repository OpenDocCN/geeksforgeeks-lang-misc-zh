# 框的列表:数组列表

> 原文:[https://www.geeksforgeeks.org/kotlin-list-arraylist/](https://www.geeksforgeeks.org/kotlin-list-arraylist/)

ArrayList 类用于在 [Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) 中创建动态数组。动态数组声明我们可以根据需要增加或减少数组的大小。它还提供读写功能。数组列表可能包含重复项，并且本质上是非同步的。我们使用数组列表来访问指定元素的索引，将一个数组列表转换成字符串或另一个数组以及更多功能。

### 构造函数–

> 1)数组列表<e>():–创建一个空的数组列表
> 2)数组列表(容量:Int):–创建一个指定大小的数组列表。
> 3)数组列表(元素:集合<E>):–创建一个由集合元素填充的数组列表。</e>

### 一些重要的方法-

### add(索引:Int，元素:E):布尔值

它用于将特定元素添加到数组列表中。第二个参数包含要添加的元素，它是必需的，第一个参数是我们要添加元素的索引，它是可选的，默认情况下它的值是 1 +数组的最后一个索引。
**例:–**

```kt
fun main(args: Array<String>) {
    // creating empty arraylist using constructor
    var arraylist = ArrayList<String>()
    //adding String elements in the list
    arraylist.add("Geeks")

    arraylist.add("Geeks")
    // iterating the list
    println("Array list ---->")
    for(i in arraylist)
        println(i)

    arraylist.add( 1 , "For")
    println("Arraylist after insertion ---->")
    for(i in arraylist)
        println(i)
}
```

**输出:**

```kt
Arraylist ---->
Geeks
Geeks
Arraylist after insertion ---->
Geeks
For
Geeks

```

### addAll(索引:Int，元素:集合):布尔值

它用于将指定集合的所有元素添加到指定索引处的当前列表中。第一个参数是索引值，也是可选的。

```kt
fun main(args: Array<String>) {
    // creating empty arraylist using constructor
    var arraylist=ArrayList<String>()
    //adding String elements in the list
    arraylist.add("Geeks")
    arraylist.add("For")
    arraylist.add("Geeks")
    // creating new arraylist1
    var arraylist1=ArrayList<String>()
    //adding all elements from arraylist to arraylist1
    println("Elements in arraylist1 -->")
    arraylist1.addAll(arraylist)
    for(i in arraylist1)
        println(i)
}
```

**输出:**

```kt
Elements in arraylist1 -->
Geeks
For
Geeks

```

### get(索引:Int): E

它用于返回列表中指定索引处的元素。

```kt
fun main(args: Array<String>) {
    // creating empty arraylist using constructor
    var arraylist=ArrayList<Int>()
    // adding elements
    arraylist.add(10)
    arraylist.add(20)
    arraylist.add(30)
    arraylist.add(40)
    arraylist.add(50)

    // iterating through the elements
    for(i in arraylist)
    print("$i ")
    println()
    println("Accessing the index 2 of arraylist: "+arraylist.get(3))
}
```

**输出:**

```kt
10 20 30 40 50
Accessing the index 2 of arraylist: 40

```

### 集合(索引:Int，元素:E):E

它用于用作为参数传递的指定元素替换当前列表中指定位置的元素。

```kt
fun main(args: Array<String>) {
    // creating empty arraylist using constructor
    var arraylist=ArrayList<String>()
    // adding elements
    arraylist.add("Geeks")
    arraylist.add("for")
    arraylist.add("Geeks:")
    arraylist.add("Portal")
    // iterating through the elements
    for(i in arraylist)
        print("$i ")
    println()
    // set the element at index 3 with new string
    arraylist.set(3,"A computer Science portal for students")
    // iterating through the elements
    for(i in arraylist)
        print("$i ")
}
```

**输出:**

```kt
Geeks for Geeks: Portal 
Geeks for Geeks: A computer Science portal for students 

```

### 索引（元素： E）： 整数

它用于返回列表中指定元素第一次出现的索引，如果列表中没有指定元素，则返回-1。

```kt
fun main(args: Array<String>) {
    // creating empty arraylist using constructor
    var arraylist=ArrayList<String>()
    // adding elements
    arraylist.add("Geeks")
    arraylist.add("for")
    arraylist.add("Geeks")

    // iterating through the elements
    for(i in arraylist)
        print("$i ")
    println()
    println("The index of the element is: "+arraylist.indexOf("Geeks"))
}
```

**输出:**

```kt
Geeks for Geeks 
The index of the element is: 0

```

### 移除(元素:E):布尔值

它用于从当前集合中移除特定元素的第一个匹配项(如果有)。类似地，为了移除索引 I 处的元素，我们使用**移除(索引)**

```kt
fun main(args: Array<String>) {
    // creating empty arraylist using constructor
    var arraylist=ArrayList<String>()
    // adding elements
    arraylist.add("Geeks")
    arraylist.add("for")
    arraylist.add("Geeks")

    arraylist.remove("for")
    // iterating through the elements
    for(i in arraylist)
        print("$i ")
}
```

**输出:**

```kt
Geeks Geeks

```

### 清除()

它用于从列表中移除所有元素。

```kt
fun main(args: Array<String>) {
    // creating empty arraylist using constructor
    var arraylist=ArrayList<Int>()
    // adding elements
    arraylist.add(10)
    arraylist.add(20)
    arraylist.add(30)
    arraylist.add(40)
    arraylist.add(50)

    // iterating through the elements
    for(i in arraylist)
        print("$i ")
    arraylist.clear()
    println()
    println("The size of arraylist after clearing all elements: "+arraylist.size)
}
```

**输出:**

```kt
10 20 30 40 50 
The size of arraylist after clearing all the elements: 0

```