# 柯特林正则表达式模式

> 原文:[https://www.geeksforgeeks.org/kotlin-regex-patterns/](https://www.geeksforgeeks.org/kotlin-regex-patterns/)

[正则表达式](https://www.geeksforgeeks.org/kotlin-regular-expression/)用于搜索文本和更高级的文本操作。正则表达式几乎是每种编程语言的基础部分，科特林也不例外。在[科特林](https://www.geeksforgeeks.org/introduction-to-kotlin/)中，正则表达式的支持是通过 Regex 类提供的。此类的对象表示正则表达式，可用于字符串匹配目的。

我们可以很容易地在不同种类的软件中找到正则表达式的使用，从最简单的到难以置信的复杂应用。

**柯特林正则表达式**
在柯特林中，我们用正则表达式构建正则表达式。

```
Regex("pen")
"pen".toRegex()
Regex.fromLiteral("pen")

```

模式定义了我们需要搜索或操作的文本。它由文本文字和元字符组成。元字符是控制正则表达式计算的特殊字符。例如，我们用\s 搜索空格。

在 Kotlin 中，下表给出了一些正则表达式模式。

| 模式 | 概念 | 例子 |
| ^ | 将字符串的第一个字符与给定的字符匹配 | x |
| $ | 将字符串的最后一个字符与给定的字符匹配 | x$ |
| 。 | 该模式匹配任何单个字符。 | ab。 |
| &#124; | 这被称为交替/或运算符。这结合了两种或多种模式。 | ^x &#124;一美元 |
| ？ | 这最多与前一个字符匹配一次。 | ab？ |
| + | 这至少与前一个字符匹配一次。 | abc+ |
| * | 这与前一个字符出现零次或更多次相匹配。 | xyz* |
| [pqr] | 这将匹配集合中的任何单个字符。 | [pqr] |
| [i-p] | 这匹配该范围内的任何单个字符。 | [i-p] |
| [^fsd] | 这意味着否定。它匹配除指定字符之外的任何字符。 | [^fsd] |
| \s | 这是匹配空格的字符类。 | \\s+(匹配一个或多个空白字符) |
| \w | 这是匹配任何构成单词的字符的字符类。 | \\w |

**注意:-** 首先我们已经创建了一个模式，然后我们可以使用其中一个函数来应用于文本字符串上的模式。这些函数包括 find()、findall()、replace()和 split()。

### Kotlin find()方法

它从指定的起始索引开始，返回输入中正则表达式的第一个匹配项。在 Kotlin 中，默认的开始索引是 0。

**使用查找方法的柯特林程序–**

```
fun main(args : Array<String>) {

    val company = "GeeksforGeeks : A computer science portal for students"

    val pattern = "science".toRegex()

    val found = pattern.find(company)

    val m = found?.value
    val index = found?.range

    println("$m found at indexes: $index")

}
```

**输出:**

```
science found at indexes: 27..33
```

### Kotlin findAll()方法

它返回给定输入字符串中所有正则表达式出现的序列。

**使用 findAll 方法的 Kotlin 程序–**

```
fun main(args : Array<String>) {

    val company = "GeeksforGeeks"

    val pattern = "Geeks".toRegex()

    val patt = pattern.findAll(company)

    patt.forEach { f ->
        val m = f.value
        val index = f.range
        println("$m indexes are: $index")
     }
}
```

**输出:**

```
Geeks indexes are: 0..4
Geeks indexes are: 8..1

```

### 点(。)元字符

点(。)元字符表示文本中的任何单个字符。
**科特林计划–**

```
fun main(args : Array<String>) {

    val names = listOf("GeeksforGeeks", "GeekyAnts", "McGeek")

    val pattern = "..Geek".toRegex()

    names.forEach { name ->
        if (pattern.containsMatchIn(name)) {
            println("$name matches")

        }
    }
}
```

**输出:**

```
GeeksforGeeks matches
McGeek matches

```