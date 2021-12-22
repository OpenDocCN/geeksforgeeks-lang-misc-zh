# 柯特林函数变异示例

> 原文:[https://www . geeksforgeeks . org/kot Lin-function-variations-with-examples/](https://www.geeksforgeeks.org/kotlin-function-variations-with-examples/)

在 Kotlin 中定义函数时，我们有许多可选的注释。我们将逐一学习它们。

**在柯特林中定义函数:**

```kt
Visibility modifier fun functionName (argument name: type name, ...): return type{
  .....
  // function body
  .....
  return value
 }
```

通常，这是在 Kotlin 中定义函数的正确方式。

**例:**

```kt
private fun gfg1( a : Int, b :Int ): Int {
  var c : Int 
  c = a + b
  return c
}
```

现在我们来看看这个函数的变化。

### 可见性修改器

在柯特林中，我们在定义函数时，可以选择指定可见性修改器。如果在定义时没有提到它，默认情况下，它被认为是公共的。

**例:**

```kt
fun gfg2( a : Int, b :Int ): Int {
  var c : Int 
  c = a + b
  return c
}
```

gfg1()和 gfg2()都在做同样的工作，但是 gfg1 是一个私有函数，gfg2 是一个公共函数，因为我们没有提到它的 Visibility 修饰符。

### 单表达式函数

在 Kotlin 中，如果函数只有一个表达式，我们可以省略大括号。

**例:**

```kt
fun gfg3( a: Int , b :Int ) : Int  = a + b
```

我们用“=”符号代替大括号作为函数体。我们也可以省略 Single 表达式函数中的返回类型。

```kt
fun gfg4( a: Int , b :Int ) = a + b
```

gfg4()和 gfg3()相同。

### 返回类型

在 Kotlin 中，定义函数时，我们需要声明函数中返回的数据类型。如果我们什么都不返回，那么我们可以选择指定“**单位**”或者如果我们什么都不指定，Kotlin 会假设它是一个什么都不返回的函数。

**例:**

```kt
// declaring the return type as 
// unit as it isn't returning anything.
fun gfg5( a : Int): Unit {
  print(a)
}
// Here we have mention the return type,
// kotlin can infer the return type
fun gfg6( a : Int){
  print(a)
}
```

gfg5()和 gfg6()是相同的。

### 争吵

当我们在一个函数中有很多参数时，很难记住每个参数的位置。因此，这里我们可以使用**名称参数，**这里我们需要指定名称以及函数的值。我们可以更改值的顺序，该值将被分配给一个与值同名的参数。

**例:**

```kt
fun main( ){
    val res1 = gfg7( arg1 = 2, arg2 = 3) //using name argument 
    val res2 = gfg7( arg2 = 3, arg1 = 2 )  // sequence doesn't matter here.

}

fun gfg7( arg1 : Int, arg2 :Int ): Int {
  return arg1 + arg2
}
```