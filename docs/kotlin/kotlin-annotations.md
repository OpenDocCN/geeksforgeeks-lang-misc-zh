# 科特林注释

> 原文:[https://www.geeksforgeeks.org/kotlin-annotations/](https://www.geeksforgeeks.org/kotlin-annotations/)

注释是 Kotlin 的一个特性，它允许程序员将补充信息嵌入到源文件中。然而，这些信息不会改变程序的动作。在开发和部署过程中，各种工具都会用到这些信息。
注释最常包含以下参数，这些参数必须是编译时常数:

*   基本类型(整型、长型等)
*   用线串
*   列举
*   班级
*   其他注释
*   上述类型的数组

### 应用注释–

我们可以通过在一个代码元素前面加上@符号来应用注释。例如，如果我们想要应用一个名为 Positive 的注释，那么如果我们想要编写注释 Pos
，那么我们应该编写以下内容

```
@Positive val i: Int
```

参数可以在括号中传递给注释，类似于函数调用。

```
@Allowedlanguage("Kotlin")
```

当一个注释作为参数在另一个注释中传递时，我们应该省略 **@** 符号。这里我们已经通过了 **Replacewith()** 注释作为参数。

```
@Deprecated("This function is deprecated, use === instead", ReplaceWith("this === other"))
```

当标注参数是类对象时，我们应该在类名中添加**:class**为:

```
@Throws(IOException::class)
```

### 声明注释–

要声明一个注释，class 关键字的前缀是 annotation 关键字。本质上，注释声明不能包含任何代码。在声明我们的自定义注释时，我们应该指定它们可能应用于哪些代码元素，以及它们应该存储在哪里。
最简单的标注不包含参数–

```
annotation class MyClass
```

需要参数的注释与具有主构造函数的类非常相似–

```
annotation class Suffix(val s: String)
```

### 注释构造函数–

我们也可以注释一个类的构造函数。这可以通过对构造函数声明使用 constructor 关键字并在它前面放置注释来实现。

```
class MyClass@Inject constructor(dependency: MyDependency) {  
//. . .   
}
```

### 注释属性–

我们可以通过向属性添加注释来注释类的属性。在下面的示例中，我们假设如果名称的值是 Kotlin 或 Java，那么 Lang 实例是有效的。

```
class Lang (
    @Allowedlanguages(["Java","Kotlin"]) val name: String)
}
```

### 一些内置注释–

Kotlin 还提供了某些内置注释，用于为用户定义的注释提供更多属性。准确地说，这些注释用于注释注释。
**@ Target–**
这个标注指定了可以应用标注的地方，比如类、函数、构造函数、类型参数等。当注释应用于类的主构造函数时，构造函数关键字在构造函数之前指定。
**示例演示@Target 注释**

## Java 语言(一种计算机语言，尤用于创建网站)

```
@Target(AnnotationTarget.CONSTRUCTOR, AnnotationTarget.LOCAL_VARIABLE)
annotation class AnnotationDemo2

class ABC @AnnotationDemo2 constructor(val count:Int){
    fun display(){
        println("Constructor annotated")
        println("Count is $count")
    }
}
fun main(){
    val obj =  ABC(5)
    obj.display()
    @AnnotationDemo2 val message: String
    message = "Hello"
    println("Local parameter annotated")
    println(message)
}
```

**输出:**

```
Constructor annotated
Count is 5
Local parameter annotated
Hello
```

**@ Retention–**
这个注解指定了注解的可用性，即注解是保留在源文件中，还是在运行时可用，等等。它的必需参数必须是具有以下元素的注释保留枚举的实例:

*   来源
*   二进制的
*   运行时间

**演示@Retention 注释的示例:**

## Java 语言(一种计算机语言，尤用于创建网站)

```
//Specifying an annotation with runtime policy
@Retention(AnnotationRetention.RUNTIME)
annotation class AnnotationDemo3

@AnnotationDemo3 fun main(){
    println("Main function annotated")
}
```

**输出:**

```
Main function annotated
```

**@ Repeatable–**
这个注释允许用同一个注释多次注释一个元素。根据 Kotlin 1.3 的当前版本，此注释只能在保留策略设置为 SOURCE 的情况下使用。
**示例演示@可重复**

## Java 语言(一种计算机语言，尤用于创建网站)

```
@Repeatable
@Retention(AnnotationRetention.SOURCE)
annotation class AnnotationDemo4 (val value: Int)

@AnnotationDemo4(4)
@AnnotationDemo4(5)
fun main(){
    println("Repeatable Annotation applied on main")
}
```

**输出:**

```
Repeatable Annotation applied on main
```