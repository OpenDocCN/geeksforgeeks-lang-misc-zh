# 科特林 Hello World 节目

> 原文:[https://www . geesforgeks . org/hello-world-program-in-kot Lin/](https://www.geeksforgeeks.org/hello-world-program-in-kotlin/)

**你好，世界！**是任何编程语言的第一个基础程序。让我们用 Kotlin 编程语言编写第一个程序。

**世界你好科特林的程序–**

打开您最喜欢的编辑器记事本或 notepad++并用以下代码创建一个名为 firstapp.kt 的文件。

```kt
// Kotlin Hello World Program
fun main(args: Array<String>) {
    println("Hello, World!")
}

```

您可以在命令行编译器中编译程序。

```kt
$ kotlinc firstapp.kt
```

现在运行程序，在命令行编译器中查看输出。

```kt
$kotlin firstapp.kt
Hello, World!

```

可以在 *Intellij IDEA* 中运行程序，如[设置环境](https://www.geeksforgeeks.org/kotlin-environment-setup-with-intellij-idea/)一文所示。

### 关于“你好，世界！”程序–

**第一行:**
第一行是被编译器忽略的注释。注释是在程序中添加的，目的是使源代码更容易被读者理解。

Kotlin supports two type of comments –

1.  **单行评论**

    ```kt
                   // single line comment

    ```

2.  **可磨线 comment**

    ```kt
                  /*   This is 
                       multi line 
                       comment 
                 */

    ```

**第 2 行:**
第 2 行定义主要功能

```kt
 fun main(args: Array<String>) {
    // ...
}

```

`main()`功能是每个程序的入口点。kotlin start fun 关键字中的所有函数后跟函数名(这里 main 是名称)、参数列表、可选返回类型和函数体({ ……)。} ).
在这种情况下，`main` 函数包含参数——字符串和返回单元的数组。在 java 中，单位类型对应于 void，这意味着函数不返回值。

**第三行:**
第三行是一个语句，它打印“你好，世界！”到程序的标准输出。

```kt
println("Hello, World!")

```

像其他现代编程语言一样，分号在 Kotlin 中是可选的。