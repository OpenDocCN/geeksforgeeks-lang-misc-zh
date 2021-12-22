# 柯特林介绍

> 原文:[https://www.geeksforgeeks.org/introduction-to-kotlin/](https://www.geeksforgeeks.org/introduction-to-kotlin/)

**Kotlin** 是 JetBrains 开发的一种静态类型的通用编程语言，已经构建了像 IntelliJ IDEA、PhpStorm、Appcode 等世界级的 ide。它于 2011 年由 JetBrains 首次引入，是 JVM 的一种新语言。Kotlin 是面向对象的语言，是一种比 Java“更好的语言”，但仍然可以与 Java 代码完全互操作。

Kotlin 由谷歌赞助，2017 年宣布为**安卓开发**的官方语言之一。

**柯特林示例–**

```
fun main()
{
    println("Hello Geeks");
}
```

**柯特林的主要特征:**

1.  **静态类型化**–静态类型化是一种编程语言特性，意味着每个变量和表达式的类型在编译时都是已知的。虽然它是静态类型语言，但它不需要您显式指定您声明的每个变量的类型。
2.  **Data Classes**– In Kotlin, there are Data Classes which lead to auto-generation of boilerplate like equals, hashCode, toString, getters/setters and much more.

    考虑以下示例–

    ```
    /*     Java Code     */
    class Book {
        private String title;
        private Author author;
        public String getTitle()
        {
            return title;
        }
        public void setTitle(String title)
        {
            this.title = title;
        }
        public Author getAuthor()
        {
            return author;
        }
        public void setAuthor(Author author)
        {
            this.author = author;
        }
    }
    ```

    但是在科特林，只有一行用来定义上面的类

    ```
    /* Kotlin Code */
    data class Book(var title:String, var author:Author)

    ```

3.  **简洁**–它大大减少了用其他面向对象编程语言编写的额外代码。
4.  **Safe** – It provides the safety from most annoying and irritating NullPointerExceptions by supporting nullability as part of its system.
    Every variable in Kotlin is non-null by default.

    ```
    String s = "Hello Geeks"    // Non-null 

    ```

    如果我们试图赋予 s 空值，那么它会产生编译时错误。所以，

    ```
    s = null                    // compile time error

    ```

    要将空值赋给任何字符串，应该将其声明为可空。

    ```
    String nullableStr? = null  // compiles successfully

    ```

    length()函数也对可空字符串禁用。

5.  **与 java 互操作**–Kotlin 运行在 Java 虚拟机(JVM)上，因此完全可以与 Java 互操作。我们可以很容易地访问使用来自 kotlin 的 java 代码和来自 java 的 kotlin 代码。
6.  **Functional and Object Oriented Capabilities** – Kotlin has rich set of many useful methods which includes higher-order functions, lambda expressions, operator overloading, lazy evaluation, operator overloading and much more.
    Higher order function is a function which accepts function as a parameter or returns a function or can do both.

    **高阶函数示例–**

    ```
    fun myFun(company: String,product: String, fn: (String,String) -> String): Unit {
        val result = fn(company,product)
        println(result)
    }

    fun main(args: Array){
        val fn:(String,String)->String={org,portal->"$org develops $portal"}
        myFun("JetBrains","Kotlin",fn)
    }

    ```

    **输出:**

    ```
    JetBrains develops Kotlin
    ```

7.  **智能强制转换**–它显式地强制转换不可变的值，并将该值自动插入其安全强制转换中。
    如果我们试图访问一个可空类型的字符串(字符串？= "BYE ")如果没有安全转换，它将生成编译错误。

    ```
    fun main(args: Array){
        var string: String? = "BYE"          
            print(string.length)       // compile time error
        }
    }

    ```

    ```
    fun main(args: Array){
        var string: String? = "BYE"
        if(string != null) {               // smart cast
            print(string.length) 
        }
    }

    ```

8.  **编译时间**–性能更高，编译时间快。
9.  **工具友好型**–具有出色的工具支持。任何 Java IdeS——IntelliJ IDEA、Eclipse 和 Android Studio 都可以用于 Kotlin。我们也可以从命令行运行 Kotlin 程序。

**科特林语言优势:**

*   易于学习–Basic 几乎类似于 java。如果有人用 java 工作，那么很容易理解。
*   Kotlin 是多平台的——所有 Java IdeS 都支持 Kotlin，因此您可以编写程序并在任何支持 JVM 的机器上执行它们。
*   比 Java 安全多了。
*   它允许通过使用高级框架在新的 Kotlin 项目中使用 Java 框架和库，而不需要在 Java 中更改整个项目。
*   Kotlin 编程语言，包括编译器、库和所有工具，是完全免费和开源的，可在 github 上获得。这里是 Github[https://github.com/JetBrains/kotlin](https://github.com/JetBrains/kotlin)的链接

**柯特林语言的应用:**

*   你可以用柯特林来构建安卓应用。
*   Kotlin 还可以编译成 JavaScript，并使其可用于前端。
*   它也是为 web 开发和服务器端开发而设计的。