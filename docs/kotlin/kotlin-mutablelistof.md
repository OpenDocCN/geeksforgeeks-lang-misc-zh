# 科特林变异列表()

> 哎哎哎:# t0]https://www . geeksforgeeks . org/kot Lin-mutual list of/

在[科特林](https://www.geeksforgeeks.org/introduction-to-kotlin/)中，**可变列表()**方法用于实例化可变列表接口。可变列表类用于创建可变列表，在列表中可以添加或删除元素。方法*返回一个可变列表接口的实例，并获取一个特定类型的数组或混合(取决于可变列表实例的类型)元素，或者也可以为空。*

**语法:**

```kt
 fun  <T> mutableListOf( vararg elements: T): MutableList <T>
```

**参数:**
取特定类型或混合类型的数组或空参数。当需要创建空的可变列表实例时，使用空参数。

**返回:**

它返回可变列表接口的实例。

**演示可变性的 Kotlin 程序()–**

```kt
fun main(args: Array<String>)
    {
        //declaring a mutable list of integers
        val mutableListA = mutableListOf<Int>( 1 , 2 , 3 , 4 , 3);
        println(mutableListA)

        //declaring a mutable list of strings
        val mutableListB = mutableListOf<String>("Geeks","for" , "geeks");
        println(mutableListB)

        //declaring an empty mutable list of integers
        val mutableListC = mutableSetOf<Int>()
        println("Empty list "+mutableListC )
    }
```

**输出:**

```kt
[1, 2, 3, 4, 3]
[Geeks, for, geeks]
Empty list []

```

## 在列表中添加和删除元素–

我们可以使用 add()函数在可变列表中添加元素，并使用 remove()函数移除元素。

**演示可变性的 Kotlin 程序()–**

```kt
fun main(args: Array<String>) {
    var mutablelist=mutableListOf("Geeks", "For");
    //adding string elements
    mutablelist.add("Geeks")
    for(i in mutablelist)
        println(i)
    println("... after removing \"For\" ...")
    //removing "For"
    mutablelist.remove("For")
    for(i in mutablelist)
        println(i)
}
```

**输出:**

```kt
Geeks
For
Geeks
... after removing "For" ...
Geeks
Geeks

```

## 设置索引–

使用索引函数 indexOf()，lastIndexOf()，我们可以获得指定元素的索引。我们还可以使用 elementAt()函数找到特定索引处的元素。

**使用索引的柯特林程序–**

```kt
fun main(args: Array<String>)
{
    val captains = mutableListOf("Kohli","Smith","Root","Rohit","Dhawan")

    println("The element at index 2 is: "+captains.elementAt(2))

    println("The index of element is: "+captains.indexOf("Smith"))

    println("The last index of element is: "+captains.lastIndexOf("Rohit"))
}
```

**输出:**

```kt
The element at index 2 is: Root
The index of element is: 1
The last index of element is: 3
```

## 列出第一个和最后一个元素–

我们可以使用 first()和 last()函数获取列表的第一个和元素。

```kt
fun main(args: Array<String>){
    val captains = mutableListOf(1,2,3,4,"Kohli","Smith",
        "Root","Malinga","Dhawan","Rohit")

    println("The first element of the list is: "+captains.first())

    println("The last element of the list is: "+captains.last())
}
```

**输出:**

```kt
The first element of the list is: 1
The last element of the list is: Rohit

```

## 可变列表中的遍历–

我们可以用遍历列表中所有项目的迭代器运行 for 循环。

```kt
fun main(args: Array<String>)
{
    //declaring a mutable list of integers
    val seta = mutableListOf( 1 , 2 , 3 , 4 );

    //traversal of seta using an iterator 'item'
    for(item in seta)
        println( item )
}
```

**输出:**

```kt
1
2
3
4

```

## contains()和 containsAll()函数–

这两种方法都用于检查列表中是否存在元素？

**使用 contains()和 containsAll()函数的 Kotlin 程序–**

```kt
fun main(args: Array<String>){
    val captains = mutableListOf(1,2,3,4,"Kohli","Smith",
        "Root","Malinga","Rohit","Dhawan")

    var name = "Dhawan"
    println("The list contains the element $name or not?" +
            "   "+captains.contains(name))

    var num = 5
    println("The list contains the element $num or not?" +
            "   "+captains.contains(num))

    println("The list contains the given elements or not?" +
            "   "+captains.containsAll(setOf(1,3,"Root")))
}
```

**输出:**

```kt
The list contains the element Dhawan or not?   true
The list contains the element 5 or not?   false
The list contains the given elements or not?   true

```