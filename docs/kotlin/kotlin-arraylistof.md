# 框中的数组列表 Of()

> 哎哎哎:# t0]https://www . geeksforgeeks . org/kot Lin-ArrayList of/

ArrayList()是 [Kotlin ArrayList](https://www.geeksforgeeks.org/kotlin-list-arraylist/) 类的函数，用于创建新的 arrayList。数组列表是可变的，这意味着我们可以修改数组列表的内容。

**语法:**

```kt
fun  arrayListOf()

```

它用于创建一个空的新数组列表。

```kt
fun  arrayListOf(vararg elements: T)

```

它用于使用提供的元素创建新的数组列表。

**示例 1: Kotlin 程序制作新的空 ArrayList。**

```kt
fun main(args : Array<String>) {
    var arrList = arrayListOf<String>()
    println(arrList.isEmpty())
    println("ArrayList : ${arrList}")
}
```

**输出:**

```kt
true
ArrayList : []

```

**示例 2:使用字符串元素制作新数组列表的 Kotlin 程序**

```kt
fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Python", "JavaScript")
    println(arrList.isEmpty())
    println("ArrayList : ${arrList}")
}
```

**输出:**

```kt
false
ArrayList : [Java, Python, JavaScript]

```

**示例 3:使用任意数据类型的元素创建新数组列表的 Kotlin 程序**

```kt
fun main(args : Array<String>) {
    var arrList = arrayListOf<Any>(1, 2, 3, "GeeksforGeeks", 100.0)
    println(arrList.isEmpty())
    println("ArrayList : ${arrList}")
}
```

**输出:**

```kt
false
ArrayList : [1, 2, 3, GeeksforGeeks, 100.0]

```

## 财产

kotlin 中的 ArrayList 有一个属性，即**大小**。它返回数组列表中的元素数量。

**示例:**

```kt
fun main(args : Array<String>) {
    var arrList = arrayListOf<String>();
    println(arrList.size);
    arrList.add("GeeksforGeeks");
    println(arrList.size);
}
```

**输出:**

```kt
0
1

```

## 功能

数组列表类有以下功能:

**add(element):** 此函数用于将指定的元素添加到 ArrayList 中。

```kt
fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Python");
    println(arrList);
    arrList.add(0, "Kotlin");
    println(arrList);    
}
```

**输出:**

```kt
[]
[GeeksforGeeks]

```

**add(index，element):** 此函数用于将元素添加到 ArrayList 提供的索引中。

```kt
fun main(args : Array<String>) {
    var arrList = arrayListOf<String>();
    println(arrList);
    arrList.add("GeeksforGeeks");
    println(arrList);    
}
```

**输出:**

```kt
[Java, Python]
[Kotlin, Java, Python]

```

**add all(element collection):**此函数用于将指定的元素集合添加到数组列表中。

```kt
fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin");
    println(arrList);    
    arrList.addAll(listOf("Python", "JavaScript"));
    println(arrList);
}
```

**输出:**

```kt
[Java, Kotlin]
[Java, Kotlin, Python, JavaScript]

```

**addAll(index，elementCollection):** 该函数用于将指定的元素集合添加到所提供索引处的 ArrayList 中。

```kt
fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin");
    println(arrList);    
    arrList.addAll(1, listOf("Python", "JavaScript"));
    println(arrList);
}
```

**输出:**

```kt
[Java, Kotlin]
[Java, Python, JavaScript, Kotlin]

```

**clear():** 此函数用于从数组列表中移除所有元素。

```kt
fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin");
    println(arrList);    
    arrList.clear();
    println(arrList);
}
```

**输出:**

```kt
[Java, Kotlin]
[]

```

**包含(元素):**该函数用于检查数组列表中是否存在元素。如果找到的话，它返回真**，否则返回假**

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin");
    println(arrList.contains("Kotlin"));
}**
```

******输出:******

```kt
**true** 
```

******contains all(element collection):**此函数用于检查数组列表中是否存在元素集合。如果找到的话，它返回真**，否则返回假******

```kt
****fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "JavaScript");
    var checkList = listOf("Python", "Java");
    println(arrList.containsAll(checkList));
}****
```

********输出:********

```kt
**true** 
```

******get(index):** 该函数用于从数组列表中检索指定索引处的元素****

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "JavaScript");
    println(arrList.get(1));
}**
```

******输出:******

```kt
**Kotlin** 
```

******indexOf(元素)**该函数返回数组列表中指定元素第一次出现的索引。如果数组列表中没有元素，则返回-1****

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "Kotlin");
    println(arrList.indexOf("Kotlin"));
}**
```

******输出:******

```kt
**1** 
```

******lastIndexOf(元素)**该函数返回数组列表中指定元素最后一次出现的索引。如果数组列表中没有元素，则返回-1****

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "Kotlin");
    println(arrList.lastIndexOf("Kotlin"));
}**
```

******输出:******

```kt
**3** 
```

******remove(element)** 此函数用于从数组列表中移除指定元素的单个实例。如果元素出现在数组列表中并被移除，则返回**真**，否则返回**假******

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "Kotlin");
    println(arrList.remove("Kotlin"));
    println(arrList);
}**
```

******输出:******

```kt
**true
[Java, Python, Kotlin]** 
```

******remove all(element collection)**此函数用于从数组列表中移除元素的集合。如果元素集合被移除，则返回**真**，否则返回**假******

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "Kotlin");
    var delList = listOf("Java", "Kotlin");
    println(arrList.removeAll(delList));
    println(arrList);
}**
```

******输出:******

```kt
**true
[Python]** 
```

******removeAt(index):** 该函数用于通过元素在数组列表中的位置来移除元素。如果元素集合被移除，则返回**真**，否则返回**假******

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "Kotlin");
    println(arrList.removeAt(3));
    println(arrList);
}**
```

******输出:******

```kt
**Kotlin
[Java, Kotlin, Python]** 
```

******set(index，element)** 此函数用于将一个元素添加到 ArrayList 中的指定位置。****

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "Kotlin");
    arrList.add(1, "PHP");
    println(arrList);
}**
```

******输出:******

```kt
**[Java, PHP, Kotlin, Python, Kotlin]** 
```

******toArray()** 该函数用于将数组列表转换为类型为**数组**的数组。****

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "Kotlin");
    var arr = arrList.toArray();
    for (i in arr) {
        println(i);
    }
}**
```

******输出:******

```kt
**Java
Kotlin
Python
Kotlin** 
```

******toString()** 这个函数用来获取 ArrayList 对象的字符串表示。****

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "Kotlin");
    var arr = arrList.toString();
    println(arr);
}**
```

******输出:******

```kt
**[Java, Kotlin, Python, Kotlin]** 
```

******isEmpty()** 如果数组列表为空，则该函数返回**真**，否则返回**真******

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Kotlin", "Python", "JavaScript");
    println(arrList.isEmpty());
}**
```

******输出:******

```kt
**false** 
```

## ****数组列表的遍历****

****我们可以使用以下方法遍历数组列表。****

******用于循环(索引方式)******

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Python", "JavaScript", "Kotlin");
    for (index in 0..arrList.size-1) {
        println("${index} => ${arrList.get(index)}");
    }
}**
```

******输出:******

```kt
**0 => Java
1 => Python
2 => JavaScript
3 => Kotlin** 
```

******用于循环(元素方式)******

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Python", "JavaScript", "Kotlin");
    for (value in arrList) {
        println(value);
    }
}**
```

******输出:******

```kt
**Java
Python
JavaScript
Kotlin** 
```

******边循环边使用******

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Python", "JavaScript", "Kotlin");
    var i = 0;
    while (i < arrList.size) {
        println(arrList.get(i))
        i++;
    }
}**
```

******输出:******

```kt
**Java
Python
JavaScript
Kotlin** 
```

******使用迭代器******

```kt
**fun main(args : Array<String>) {
    var arrList = arrayListOf<String>("Java", "Python", "JavaScript", "Kotlin");
    var itr = arrList.iterator();
    while (itr.hasNext()) {
        println(itr.next());
    }
}**
```

******输出:******

```kt
**Java
Python
JavaScript
Kotlin** 
```