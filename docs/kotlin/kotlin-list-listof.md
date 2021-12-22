# 科特林名单:listOf()

> 哎哎哎:# t0]https://www . geeksforgeeks . org/kot Lin-list of/

列表是元素的一般有序集合。 [Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) 有两种类型的列表，不可变列表(不可修改)和可变列表(可修改)。
只读列表是用 listOf()创建的，它的元素是不能修改的，而可变列表是用 mutableListOf()方法创建的，我们在这里改变或修改列表的元素。
**科特林程序列表包含整数–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    val a = listOf('1', '2', '3')
    println(a.size)
    println(a.indexOf('2'))
    println(a[2])
}
```

**输出:**

```
3
1
3
```

**科特林程序列表包含字符串–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>) {
    //creating list of strings
    val a = listOf("Ram", "Shyam", "Raja", "Rani")
    println("The size of the list is: "+a.size)
    println("The index of the element Raja is: "+a.indexOf("Raja"))
    println("The element at index "+a[2])
    for(i in a.indices){
        println(a[i])
    }
}
```

**输出:**

```
The size of the list is: 4
The index of the element Raja is: 2
The element at index Raja
Ram
Shyam
Raja
Rani
```

### Kotlin 中列表元素的索引–

列表的每个元素都有一个索引。第一个元素的索引为零(0)，最后一个元素的索引为
len–1，其中“len”是列表的长度。

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>)
{
    val numbers = listOf(1, 5, 7, 32, 0, 21, 1, 6, 10)

    val num1 = numbers.get(0)
    println(num1)

    val num2 = numbers[7]
    println(num2)

    val index1 = numbers.indexOf(1)
    println("The first index of number is $index1")

    val index2 = numbers.lastIndexOf(1)
    println("The last index of number is $index2")

    val index3 = numbers.lastIndex
    println("The last index of the list is $index3")
}
```

**输出:**

```
1
6
The first index of number is 0
The last index of number is 6
The last index of the list is 8
```

### 第一个和最后一个元素–

我们可以检索列表的第一个和最后一个元素，而无需使用 get()方法。
考虑到前面的例子，如果我们在第 17 行
之后包含以下代码

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>)
{
    val numbers = listOf(1, 5, 7, 32, 0, 21, 1, 6, 10)
    println(numbers.first())
    println(numbers.last())
}
```

**输出:**

```
1
10
```

### 列出迭代方法–

它是一个个访问列表元素的过程。
在科特林有几种方法可以做到这一点。

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>)
{
    val names = listOf("Gopal", "Asad", "Shubham", "Aditya",
        "Devarsh", "Nikhil", "Gagan")

    // method 1
    for (name in names) {
        print("$name, ")
    }
    println()

    // method 2
    for (i in 0 until names.size) {
        print("${names[i]} ")
    }
    println()

    // method 3
    names.forEachIndexed({i, j -> println("names[$i] = $j")})

    // method 4
    val it: ListIterator<String> = names.listIterator()
    while (it.hasNext()) {
        val i = it.next()
        print("$i ")
    }
    println()
}
```

**输出:**

```
Gopal, Asad, Shubham, Aditya, Devarsh, Nikhil, Gagan, 
Gopal Asad Shubham Aditya Devarsh Nikhil Gagan 
names[0] = Gopal
names[1] = Asad
names[2] = Shubham
names[3] = Aditya
names[4] = Devarsh
names[5] = Nikhil
names[6] = Gagan
Gopal Asad Shubham Aditya Devarsh Nikhil Gagan 
```

**说明:**

```
for (name in names) {

        print("$name, ")
    }
```

for 循环遍历列表。在每个循环中，变量“name”指向列表中的下一个元素。

```
for (i in 0 until names.size) {

        print("${names[i]} ")
    }
```

此方法使用列表的大小。直到关键字创建列表索引的范围。

```
names.forEachIndexed({i, j -> println("namess[$i] = $j")})
```

使用 forEachIndexed()方法，我们循环遍历在每次迭代中都有可用索引和值的列表。

```
val it: ListIterator = names.listIterator()

    while (it.hasNext()) {

        val i = it.next()
        print("$i ")
    }
```

这里我们使用一个列表迭代器来遍历列表。

### 对列表中的元素进行排序-

以下示例显示了如何按升序或降序对列表进行排序。

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>)
{
    val list = listOf(8, 4, 7, 1, 2, 3, 0, 5, 6 )

    val asc = list.sorted()
    println(asc)

    val desc = list.sortedDescending()
    println(desc)
}
```

**输出:**

```
[0, 1, 2, 3, 4, 5, 6, 7, 8]
[8, 7, 6, 5, 4, 3, 2, 1, 0]
```

**说明:**

```
val asc = list.sorted()
```

sorted()方法按升序对列表进行排序。

```
val desc = list.sortedDescending()
```

sortedDescending()方法按降序对列表进行排序。

### Contains()和 containsAll()函数–

此方法检查列表中是否存在元素。

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main(args: Array<String>)
{
    val list = listOf(8, 4, 7, 1, 2, 3, 0, 5, 6 )

    val res = list.contains(0)

    if (res)
        println("The list contains 0")
    else
        println("The list does not contain 0")

    val result = list.containsAll(listOf(3, -1))

    if (result)
        println("The list contains 3 and -1")
    else
        println("The list does not contain 3 and -1")
}
```

**输出:**

```
The list contains 0
The list does not contain 3 and -1
```

**说明:**

```
val res = list.contains(0)
```

检查列表是否包含 0，并返回真或假(她的真)，存储在 RES
中

```
 val result = list.containsAll(listOf(3, -1))
```

检查列表是否包含 3 和-1。