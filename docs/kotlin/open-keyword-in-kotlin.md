# 在 Kotlin

中打开关键字

> 原文:[https://www.geeksforgeeks.org/open-keyword-in-kotlin/](https://www.geeksforgeeks.org/open-keyword-in-kotlin/)

**关键字**是编程语言中一些预定义的或特定的保留字，每个保留字都有与之相关的特定特征。几乎所有帮助我们使用编程语言功能的单词都包含在关键字列表中。所以你可以想象关键词列表不会是一个小列表，而“open”关键词也是其中之一，所以这篇文章也是基于 open 关键词。现在让我们试着理解 kotlin 中的“open”关键字。众所周知，kotlin 是一种现代的、高度推荐的安卓应用开发语言。因为它确实让安卓 app 的开发变得容易了很多，而且我们都应该知道它也是对 java 编程语言的修改，那么为什么不通过与 java 的对比来理解“open”这个关键词呢。即我们可以用什么来代替 java 中的“open”关键字。所以基本上 java 有一个名为“ **final** 的关键词。但它的工作原理与“**开启**”关键词完全相反，所以让我们快速了解一下[“final”关键词。](https://www.geeksforgeeks.org/final-keyword-in-java/)希望大家都知道，不知道也不用担心。

> “final”关键字在 java 中的使用大多与类和方法(函数)一起作为:
> 
> **final method** :一个不能被覆盖的方法。
> 
> **最终类**:不能扩展的类。

但是，Kotlin 有一个特殊的功能，即**类**和**方法**默认不为**扩展**打开，这意味着它们默认是最终类或最终函数。这意味着 Kotlin 中的开放类和方法相当于 Java 中 final 的反义词，开放方法是可重写的，开放类在 Kotlin 中是可扩展的。

> **注意**:您的类被隐式声明为开放的，因为它是抽象的，因此您不能直接创建该类的实例。

### 例子

**例 1:类**的扩展

现在我们知道 kotlin 默认情况下拥有最终的一切。所以，如果我们试图扩展这个类，那么编译器会显示一个错误。

## 科特林

```
class Geeks
class student:Geeks()
```

```
error: This type is final, so it cannot be inherited
```

**要使一个类开放进行扩展，我们应该使用“开放”关键字作为:**

## 柯特林

```
// mark the class with "open"
open class Geeks
class student:Geeks()
```

**示例 2:函数(方法)的覆盖**

与类相同，函数(方法)在默认配置中不能被覆盖，即使包含函数的类是打开的

## 【科特林】

```
open class geeks{
  fun student():string ="alok"
}
class batch: geeks() {
  override fun student():string = "ashish"
}
```

该代码将显示一个错误

```
error: 'student' in 'geeks' is final and cannot be overridden
```

**要在子类中覆盖一个方法，我们应该使用“open”关键字作为:**

## 柯特林

```
open class geeks{
 // mark the function with open 
 open fun student():string ="alok"
}
class batch: geeks() {
  override fun student():string = "ashish"
}
```

现在我们的代码是正确的。