# 科特林哈希塞夫()

> 哎哎哎:# t0]https://www . geeksforgeeks . org/kot Lin-hashsetf/

[Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) HashSet 是一个通用的无序元素集合，它不包含重复的元素。它实现了 set 接口。 **hashSetOf** ()是一个返回可变 hashSet 的函数，可以读写。HashSet 类使用哈希机制存储所有元素。

**语法:**

```kt
fun <T> hashSetOf(vararg elements: T): HashSet<T>
```

它用给定的元素返回一个新的 HashSet，但不保证存储时指定的顺序。

**hashSetOf()**

## 科特林

的例子

```kt
fun main(args: Array<String>)
{

    //declaring a hash set of integers
    val seta = hashSetOf(1,2,3,3);
    //printing first set
    println(seta)

    //declaring a hash set of strings
    val setb = hashSetOf("Geeks","for","geeks");
    println(setb);

}
```