# 柯特林中的“const”和“val”有什么区别？

> 原文:[https://www . geeksforgeeks . org/const-和-val-in-kotlin 有什么区别/](https://www.geeksforgeeks.org/whats-the-difference-between-const-and-val-in-kotlin/)

在 Kotlin 中，和其他编程语言一样，属性可以是可变的(可变的)或不可变的(不可变的)。为了声明一个不可变的属性，我们使用了 const 和 val 这两个术语。开发人员经常对何时使用这些短语感到困惑。在本文中，我们将研究科特林中常量和值之间的区别。

### “const”在柯特林中的使用

const 关键字用于声明本质上不可变的属性，即只读属性。这些值只有在运行时才知道，因此，在运行时没有值可以分配给常量变量。要成为常量属性，属性必须满足以下要求:

1.  Must be at the top level, or a member of an object or companion object.
2.  You should start with a primitive data type.
3.  There is no custom getter, so you can't assign a constant variable to a function or class, because this variable will be initialized at run time instead of compile time.

### “val”在柯特林中的使用

const 和 val 之间的主要区别在于 val 属性也可以在运行时初始化。因此，您可以将 val 变量分配给方法或类。

**示例:**

## 我的锅

```kt
const val gfgName = "Geeksforgeeks" // goes well
val coursename = "Android" // goes well

const val gfgName = getgfgName() // not goes well
val coursename = getcoursename() // not goes well
```

上面例子中的不可变变量是 gfgName。使用 const 时，直接赋值就可以了；但是，试图从某个函数 getgfgame 赋值将导致错误，因为该值将在运行时而不是编译时赋值。然而，在 val 的情况下，这两种情况都是可以接受的。

### 既然“val”就够了，为什么还要用“const”？

在最后一个例子中，我们看到 val 变量的值在运行时初始化，在编译时初始化。那么，为什么在 val 足够的时候使用 const 呢？让我们看看另一个真实世界的安卓例子，看看 const 和 val 是如何使用的:

## 【科特林】

```kt
GeeksforGeeksClass {
    companion object {   
        const val IMAGE_EXTENSION = ".jpg"   
        val LOGONAME: String
        get() = "Geeks" + System.currentTimeMillis() + IMAGE_EXTENSION
    }
}
```

> **geek tip:**在上面的例子中，我们在伴随对象中声明 const 值 IMAGE_EXTENSION，并使用自定义 getter 将 FILENAME 变量初始化为 val。

因为文件扩展名总是相同的，所以它被定义为常量变量。但是，文件名将根据我们应用文件名的基本原理进行修改。在这个例子中，我们用当前时间命名文件。你不能一开始就给它一个值，因为这个值是在运行时获得的。所以我们要用瓦尔。

## 科特林

```kt
public final String getIMAGENAME() {
   return "Geeks" + System.currentTimeMillis() + ".jpg";
}
```

在上面的例子中，我们在伴随对象中声明了常量值 FILE EXTENSION，并使用自定义 getter 将 FILENAME 变量初始化为 val。因为文件扩展名总是相同的，所以它被定义为常量变量。但是，文件名将根据我们应用文件名的基本原理进行修改。在这个例子中，我们用当前时间命名文件。你不能一开始就给它一个值，因为这个值是在运行时获得的。所以我们要用瓦尔。

在这里，变量 IMAGE_EXTENSION 已经被它的值“所取代。jpg”，表示该值已经内联，因此在运行时访问该变量没有开销。这就是用 const 代替 val 的好处。