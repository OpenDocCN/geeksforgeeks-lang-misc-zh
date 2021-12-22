# 柯特林|应用 vs 与

> 原文:[https://www.geeksforgeeks.org/kotlin-apply-vs-with/](https://www.geeksforgeeks.org/kotlin-apply-vs-with/)

### 科特林:**申请*

在 [Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) 中，apply 是特定类型的扩展函数，并将其范围设置为调用 apply 的对象。Apply 在表达式中的对象引用上运行，并在完成时返回对象引用。当然，它不是简单地设置属性，而是做更多的功能，并且能够在返回之前评估复杂的逻辑。最后，它返回同一个对象，只是做了一些修改。

> *   *Apply* is an extension function of type.*   An object reference is required to run into the expression.*   Also returns an object reference when completed.

**定义*适用* :**

```kt
inline fun  T.apply(block: T.() -> Unit): T 
{
    block()
    return this
}

```

**<u>应用</u>** 的例子

```kt
fun main(args: Array<String>)
{
    data class GFG(var name1 : String, var name2 : String,var name3 : String)
    // instantiating object of class
    var gfg = GFG("Geeks","for","hi")
    // apply function invoked to change the name3 value
    gfg.apply { this.name3 = "Geeks" }
    println(gfg)
}
```

**输出:**

```kt
GFG(name1=Geeks, name2=for, name3=Geeks)

```

在这里，GFG 班的第三名成员从“嗨”变成了“极客”。

### 柯特林::*带*

与*应用*一样，*与*也用于更改实例的属性。但是这里我们不需要对象引用来运行，即:我们不需要**点**运算符来引用。

 ***的定义同***

```kt
inline fun  with(receiver: T, block: T.() -> R): R 
{
    return receiver.block()
}

```

**<u>例*同*</u> 同**

```kt
fun main(args: Array<String>)
{
    data class GFG(var name1: String, var name2 : String,var name3 : String)
    var gfg = GFG("hello", "for","hi")
    // applying with function
    with(gfg)
    {
        name1 = "Geeks"
        name3 = "Geeks"
    }
    println(gfg)
}
```

**输出:**

```kt
GFG(name1=Geeks, name2=for, name3=Geeks)

```

这里我们*不需要任何**点**运算符，我们使用带有*扩展函数的*改变了 GFG 类对象的第一个和第三个变量的值。*

### apply 和 with 的区别

> 带有的*   **runs without an object, while **application** needs an object to run***   **The application** runs on the object reference, but with **it only takes it as the parameter**传递