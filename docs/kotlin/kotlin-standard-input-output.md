# 科特林标准输入/输出

> 原文:[https://www.geeksforgeeks.org/kotlin-standard-input-output/](https://www.geeksforgeeks.org/kotlin-standard-input-output/)

在本文中，我们将在这里讨论如何在 Kotlin 中获取输入以及如何在屏幕上显示输出。Kotlin 标准输入/输出操作用于将字节或字节流序列从输入设备(如键盘)传输到系统的主存储器，并从主存储器传输到输出设备(如显示器)。

在 Java 中，我们使用 System.out.println(消息)在屏幕上打印输出，但是在 Kotlin 中，println(消息)用于打印。

### 科特林输出–

Kotlin 标准输出是将字节流从主存储器流向输出设备的基本操作。您可以在系统屏幕上输出任何数据类型整数、浮点和任何模式或字符串。
可以使用以下任一功能在屏幕上显示输出。

```kt
print() function 
println() function
```

这是标准输出的 Kotlin 程序。

## 我的锅

```kt
fun main(args: Array<String>)
{
    print("Hello, Geeks! ")
    println("This is Kotlin tutorial.")
}
```