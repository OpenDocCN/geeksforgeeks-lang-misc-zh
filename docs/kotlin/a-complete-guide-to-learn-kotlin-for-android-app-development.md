# 安卓应用开发 Kotlin 学习完整指南

> 原文:[https://www . geesforgeks . org/a-complete-learn-guide-kot Lin-for-Android-app-development/](https://www.geeksforgeeks.org/a-complete-guide-to-learn-kotlin-for-android-app-development/)

Kotlin 是一种静态类型的、跨平台的、通用的 JVM 编程语言，由 JetBrains 开发。这是一种带有类型推断的语言，并且与 Java 完全互操作。Kotlin 是简洁而富于表现力的编程，因为它减少了样板代码。自谷歌 I/O 2019 年以来，安卓开发一直是 Kotlin-first。Kotlin 与 Android Studio 无缝集成，许多公司正在将整个代码库从 Java 迁移到 Kotlin。异步任务在 Kotlin 中使用 coroutines 无缝实现。所以这里是学习 Kotlin 的完整指南，专门针对安卓应用程序开发。

![Learn Kotlin For Android App Development](img/6218a15ac2de076f7517cb72e7a81cc7.png)

所以在本文中，我们已经介绍了以下内容:

1.  **柯特林编程语言基础**
2.  **柯特林**中的条件语句(控制流)
3.  **柯特林**中的功能编程
4.  **柯特林编程语言的集合**
5.  **柯特林的面向对象编程概念**
6.  **柯特林异常处理**
7.  **科特林零安全**
8.  **科特林范围功能**
9.  **Kotlin 与 Java 的互操作性**
10.  科特林 cor routes
11.  **杂项**
12.  **完成科特林教程**

### 安卓应用开发 Kotlin 学习分步指南

**柯特林编程语言基础**

*   [柯特林简介](https://www.geeksforgeeks.org/introduction-to-kotlin/)-关于柯特林编程语言的介绍性讨论。包含 Kotlin 编程语言的优点和应用。
*   [用 Intellij IDEA 设置 Kotlin 环境](https://www.geeksforgeeks.org/kotlin-environment-setup-with-intellij-idea/)–设置 IDE，准备好用 Kotlin 开始编程之旅。
*   [科特林 Hello World 节目](https://www.geeksforgeeks.org/hello-world-program-in-kotlin/)–了解科特林首个“Hello World”节目。很简单。

```
fun main(args: Array<String>) {
    println("Hello, World!")
}
```

*   [科特林数据类型](https://www.geeksforgeeks.org/kotlin-data-types/)–科特林中的基本数据类型是一种原始数据类型，其他所有数据类型都是引用类型，如数组和字符串。
*   [柯特林变量](https://www.geeksforgeeks.org/kotlin-variables/)**–柯特林中**可变的**和**不可变的**数据类型。**

****柯特林**中的条件语句(控制流)**

*   **[柯特林 if-else 表达式](https://www.geeksforgeeks.org/kotlin-if-else-expression/)–柯特林中的基本 if-else 控制流语句。了解 **if** 、 **if-else** 、 **if-else-if** 阶梯、**嵌套式 if。****
*   **[Kotlin when expression](https://www.geeksforgeeks.org/kotlin-when-expression/)–**when**it**取代了其他语言如 Java 的 **switch** 运算符。我们不要求在每个案例的结尾都有一个中断声明。****
*   ****[科特林边循环](https://www.geeksforgeeks.org/kotlin-while-loop/)–**边循环**在科特林。****
*   ****[科特林边做边循环](https://www.geeksforgeeks.org/kotlin-do-while-loop/)–**边做边**在科特林循环。****
*   ****[科特林 for loop](https://www.geeksforgeeks.org/kotlin-for-loop/)–在科特林中，for loop 相当于 **foreach** loop。****

******柯特林**中的功能编程****

*   ****[柯特林函数](https://www.geeksforgeeks.org/kotlin-functions/)–函数的基础及其在柯特林中的声明。****
*   ****[Kotlin |默认和命名参数](https://www.geeksforgeeks.org/kotlin-default-and-named-argument/)–使函数的参数可选。即在调用函数时是否传递参数。****
*   ****[Lambdas 表达式和匿名函数](https://www.geeksforgeeks.org/kotlin-lambdas-expressions-and-anonymous-functions/)–Kotlin Lambdas 的语法与 Java Lambdas 类似。没有名称的函数称为匿名函数。****
*   ****[Kotlin Inline 函数](https://www.geeksforgeeks.org/kotlin-inline-functions/)–有趣的 **inline** 关键字，它最终请求编译器不要分配内存，而只是在调用位置复制该函数的内联代码。****
*   ****[Kotlin 中缀函数标注](https://www.geeksforgeeks.org/kotlin-infix-function-notation/)–标有**中缀**关键字的函数也可以使用**中缀标注来调用，也就是**不使用括号和点来调用。****
*   ****[柯特林高阶函数](https://www.geeksforgeeks.org/kotlin-higher-order-functions/)–柯特林函数可以存储在变量和数据结构中，作为参数传递给其他高阶函数，也可以从其他高阶函数返回。****

******柯特林编程语言的集合******

*   ****[科特林集合](https://www.geeksforgeeks.org/kotlin-collections/)–一个集合通常包含多个相同类型的对象，集合中的这些对象被称为元素或项目。****
*   ****[Kotlin list:Arraylist](https://www.geeksforgeeks.org/kotlin-list-arraylist/)–动态数组声明我们可以增加或减少数组的大小作为先决条件。****
*   ****[Kotlin 列表:listOf()](https://www.geeksforgeeks.org/kotlin-list-listof/)–Kotlin 有两种类型的列表，不可变列表(不可修改)和可变列表(可修改)。****
*   ****[Kotlin Set:setOf()](https://www.geeksforgeeks.org/kotlin-set-setof/)–Kotlin Set 接口是一个通用的无序元素集合，不包含重复的元素。****
*   ****[Kotlin mutalesetof()](https://www.geeksforgeeks.org/kotlin-mutablesetof-method/)–**setOf()**是不可变的，意味着它只支持只读功能，**mutalesetof()**是可变的，意味着它同时支持读和写。****
*   ****[Kotlin hashSetOf()](https://www.geeksforgeeks.org/kotlin-hashsetof/) 它实现了设置接口。hashSetOf()是一个函数，它返回一个可变的 hashSet，可以读写。****
*   ****[柯特林映射:Mapof()](https://www.geeksforgeeks.org/kotlin-map-mapof/)–映射以由一个键和值组成的对的形式保存数据。****
*   ****[Kotlin Hashmap](https://www.geeksforgeeks.org/kotlin-hashmap/)–基于 Kotlin 哈希表的 MutableMap 接口的实现。它以键和值对的形式存储数据。****

******柯特林的面向对象编程概念******

*   ****[Kotlin 类和对象](https://www.geeksforgeeks.org/kotlin-class-and-objects/)–**类**和**对象**是面向对象编程语言的基本概念。这些支持继承、抽象等 OOPs 概念。****
*   ****[Kotlin 嵌套类和内部类](https://www.geeksforgeeks.org/kotlin-nested-class-and-inner-class/)–一个类在另一个类中声明，那么它被称为嵌套类。****
*   ****[科特林设置器和获取器](https://www.geeksforgeeks.org/kotlin-setters-and-getters/)–**设置器**用于设置任何变量的值，**获取器**用于获取该值。Getter 和 Setter 是在代码中自动生成的。****
*   ****[Kotlin |类属性和自定义访问器](https://www.geeksforgeeks.org/kotlin-class-properties-and-custom-accessors/)–因此，访问器方法–提供了一个 getter 和一个 setter 来让给定类的客户端访问数据。****
*   ****[Kotlin 构造函数](https://www.geeksforgeeks.org/kotlin-constructor/)–主构造函数初始化类，而次构造函数用于初始化类并引入一些额外的逻辑。****
*   ****[Kotlin 可见性修饰符](https://www.geeksforgeeks.org/kotlin-visibility-modifiers/)–可见性修饰符用于将类、对象、接口、构造函数、函数、属性及其设置器的可访问性限制在一定的级别。****
*   ****[科特林继承](https://www.geeksforgeeks.org/kotlin-inheritance/)–**继承**支持代码重用。它允许将现有类(基类)的功能继承到新类(派生类)中。****
*   ****[Kotlin 接口](https://www.geeksforgeeks.org/kotlin-interfaces/)–接口是 Kotlin 提供的自定义类型，不能直接实例化。****
*   ****[Kotlin 数据类](https://www.geeksforgeeks.org/kotlin-data-classes/)–我们经常创建类来保存其中的一些数据。在这样的类中，一些标准函数通常可以从数据中导出。****
*   ****[科特林密封类](https://www.geeksforgeeks.org/kotlin-sealed-classes/)–正如单词**密封**所暗示的，密封类符合受限或有界的类层次结构。****
*   ****[柯特林抽象类](https://www.geeksforgeeks.org/kotlin-abstract-class/)–一个**抽象**类不能实例化。这意味着我们不能为抽象类创建对象。****
*   ****[Kotlin](https://www.geeksforgeeks.org/enum-classes-in-kotlin/)–**Enum**中的 Enum 类有自己的专门化类型，表示某个东西有多个可能的值。与 Java 枚举不同，Kotlin 枚举是类。****
*   ****[柯特林扩展函数](https://www.geeksforgeeks.org/kotlin-extension-function/)–当一个函数被添加到现有的类中时，它被称为扩展函数。****
*   ****[Kotlin 泛型](https://www.geeksforgeeks.org/kotlin-generics/)–允许定义可使用不同数据类型访问的类、方法和属性，同时保持对编译时类型安全性的检查。****

******柯特林异常处理******

*   ****[Kotlin 异常处理|尝试、捕捉、抛出，最后是](https://www.geeksforgeeks.org/kotlin-exception-handling-try-catch-throw-and-finally/)–异常是在程序执行期间(即运行时)发生的不想要的或意外的事件。****
*   ****[Kotlin 嵌套尝试块和多个 catch 块](https://www.geeksforgeeks.org/kotlin-nested-try-block-and-multiple-catch-block/)–当内部 try-catch 块中发生异常而内部 catch 块没有处理时，嵌套 try-catch 块的要求就出现了。****

******科特林零安全******

*   ****[科特林空安全](https://www.geeksforgeeks.org/kotlin-null-safety/)–科特林的类型系统旨在消除代码中空引用的危险，因为这是一个十亿美元的错误。****
*   ****[Kotlin |类型检查和智能转换](https://www.geeksforgeeks.org/kotlin-type-checking-and-smart-casting/)–这是一种在运行时检查变量类型的方法。****
*   ****[柯特林|显式类型转换](https://www.geeksforgeeks.org/kotlin-explicit-type-casting/)–柯特林还提供了使用安全转换操作符 as 进行类型转换的功能。如果无法进行强制转换，它将返回 null，而不是引发 ClassCastException 异常。****

******科特林范围功能******

*   ****[柯特林–作用域函数](https://www.geeksforgeeks.org/kotlin-scope-function/)–我们可以访问这些函数的对象，而无需其名称。****
*   ****[Kotlin | apply vs with](https://www.geeksforgeeks.org/kotlin-apply-vs-with/)–最容易混淆的 Scope 函数之间的区别，通过示例了解。****

******Kotlin 与 Java 的互操作性******

*   ****[Java 互操作性——从 Java](https://www.geeksforgeeks.org/java-interoperability-calling-kotlin-from-java/) 调用 Kotlin——开发 Kotlin 时，它只在 JVM 上工作，因此它提供了一整套功能，使得从 Java 调用 Kotlin 变得非常容易。****
*   ****[Java 互操作性——从 Kotlin](https://www.geeksforgeeks.org/java-interoperability-calling-java-from-kotlin/) 调用 Java——Java 类中定义的所有类型的 getter 和 setter 在 Kotlin 中都表示为属性。****

****科特林 cor routes****

*   ****[暂停功能在 Kotlin Coroutines 中](https://www.geeksforgeeks.org/suspend-function-in-kotlin-coroutines/)–暂停功能是可以启动、暂停和恢复的功能。****
*   ****[柯特林协同函数中的运行阻塞，示例](https://www.geeksforgeeks.org/runblocking-in-kotlin-coroutines-with-example/)–运行阻塞是协同函数。通过不提供任何上下文，它将在主线程上运行。****
*   ****[Kotlin Coroutines 中的作业、等待、取消](https://www.geeksforgeeks.org/jobs-waiting-cancellation-in-kotlin-coroutines/)–如何等待 coroutine，以及如何取消 coroutine。每当新的协同程序启动时，它都会返回一个作业。****
*   ****[启动 vs Kotlin Coroutines 中的异步](https://www.geeksforgeeks.org/launch-vs-async-in-kotlin-coroutines/)–创建 Coroutines 不会分配新线程。相反，它们使用预定义的线程池和智能调度来决定下一步执行哪个任务以及以后执行哪个任务。****
*   ****[with context in Kotlin Coroutines](https://www.geeksforgeeks.org/withcontext-in-kotlin-coroutines/)–**with context**不过是写异步的另一种方式，在这种方式下，不必写 await()。****

******杂项******

*   ****[Kotlin 注释](https://www.geeksforgeeks.org/kotlin-annotations/)–注释是 Kotlin 的一个特性，允许程序员将补充信息嵌入到源文件中。****
*   ****[Kotlin 反射](https://www.geeksforgeeks.org/kotlin-reflection/)–除了 Java 反射 API 之外，Kotlin 还以简单的功能风格提供了自己的一套反射 API。****
*   ****[柯特林中的委托](https://www.geeksforgeeks.org/delegation-in-kotlin/)–委托控制任何对象从一个实例到另一个实例的权力/权限分配。****
*   ****[Kotlin](https://www.geeksforgeeks.org/delegated-properties-in-kotlin/)中的委派属性–委派的定义是将任何权力或权力授予另一个人(老板将任务分配给其员工)来执行不同的工作。****

****完整的 Kotlin 教程，可以参考这篇文章: [**Kotlin 编程语言**](https://www.geeksforgeeks.org/kotlin-programming-language/)****