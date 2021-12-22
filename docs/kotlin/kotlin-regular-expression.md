# 柯特林正则表达式

> 原文:[https://www.geeksforgeeks.org/kotlin-regular-expression/](https://www.geeksforgeeks.org/kotlin-regular-expression/)

**正则表达式**几乎是每种编程语言的基础部分，科特林也不例外。在 Kotlin 中，对正则表达式的支持是通过**正则表达式**类提供的。此类的对象表示正则表达式，可用于字符串匹配目的。

```
class Regex
```

我们可以很容易地在不同种类的软件中找到正则表达式的使用，从最简单的到难以置信的复杂应用。
在本文之前先看一下[Java 中的正则表达式](https://www.geeksforgeeks.org/regular-expressions-in-java/)T3

### 构造函数–

1.  **< init >(模式:字符串)**:这个构造函数基于模式字符串创建一个正则表达式。

2.  **< init >(模式:String，选项:RegexOption)** :这个构造函数基于指定的模式和选项创建一个正则表达式。该选项是 RegexOption 枚举类的常量。

3.  **< init >(模式:字符串，选项:Set < RegexOption > )** :该构造函数基于指定的字符串模式和集合中指定的选项集创建正则表达式。

### 属性–

1.  **val 选项:Set < RegexOption >** :包含创建 regex 时要使用的选项集。

2.  **val 模式:字符串**:包含描述模式的字符串。

### Regex 函数–

**contains matchin()–**该函数返回一个布尔值，指示输入中是否存在我们的模式匹配。

```
fun containsMatchIn(input: CharSequence): Boolean
```

**演示柯特林中 containsMatchIn()函数的示例**

## Java 语言(一种计算机语言，尤用于创建网站)

```
fun main()
{
    // Regex to match any string starting with 'a'
    val pattern = Regex("^a")
    println(pattern.containsMatchIn("abc"))
    println(pattern.containsMatchIn("bac"))
}
```