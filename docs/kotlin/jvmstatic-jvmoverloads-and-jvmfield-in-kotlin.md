# Kotlin 中的 JvmStatic、JvmOverloads 和 JVM field

> 原文:[https://www . geeksforgeeks . org/JVM static-JVM overloads-and-JVM field-in-kot Lin/](https://www.geeksforgeeks.org/jvmstatic-jvmoverloads-and-jvmfield-in-kotlin/)

在本文中，我们将研究如何在当前的 Java 代码中使用 Kotlin 中的@JvmStatic、@JvmOverloads 和@JvmField 来利用 Kotlin 代码。您可以从 Java 代码调用 Kotlin 代码，反之亦然。本博客将专注于从 Java 代码中调用 Kotlin 代码。

## 科特林

```
// Kotlin Class
class GeeksforGeeks
// Calling from Kotlin
val article = Article()
```

## 爪哇

```
// Class in Java being called
Article geeksforgeeks = new Article();
```

正如您在前面的代码中所看到的，从 Java 代码中调用 Kotlin 代码相当简单，但有时却不是这样。在这些情况下，我们在 Kotlin 中利用@JvmStatic、@JvmOverloads 和@JvmField，使从 Java 调用 Kotlin 代码的人变得简单。

### @JvmStatic

包级函数在 Kotlin 中表示为静态方法。您还可以使用 Kotlin 中的@JvmStatic 注释为伴随对象或命名对象中指定的函数创建静态方法。举个例子:

## 我的锅

```
object GeeksforGeeks {
    fun useSomeLogic() {
        // your code goes here
    }
}
```

我们现在称科特林为:

## 科特林

```
GeeksforGeeks.useSomeLogic()
```

你需要从爪哇打一个这样的电话。

## 【Java】

```
GeeksforGeeks.INSTANCE.useSomeLogic();
```

> 如果我们不使用 INSTANCE，我们如何让它发挥作用？
> 
> **JvmStatic 就是答案。**

## 科特林

```
object GeeksforGeeks {
    @JvmStatic
    fun useSomeLogic() {
        // logic goes here
    }
}
```