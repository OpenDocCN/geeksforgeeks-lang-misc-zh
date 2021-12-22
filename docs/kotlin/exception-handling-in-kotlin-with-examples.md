# 科特林异常处理示例

> 原文:[https://www . geeksforgeeks . org/exception-handling-in-kot Lin-with-examples/](https://www.geeksforgeeks.org/exception-handling-in-kotlin-with-examples/)

异常是运行时出现的错误，它会中断程序的执行流程。基本上，异常是运行时发生的不想要的事件。我们处理这种错误的方法叫做异常处理。

#### **异常类型**

1.  **Checked Exception:** 在编译时发生的异常，或者我们可以说在编译时检查的异常叫做 Checked Exception。示例— **异常**、**某文件相关异常**等
2.  **未检查异常:**运行时发生的异常称为未检查异常。示例— **出界** **例外**。

> **注意:**在科特林中，我们只有未检查的异常，这些异常只能在运行时发现。

#### **如何处理异常？**

我们有一些关键词可以帮助我们处理异常。

> 1.  **Try** //This will try to find the exception.
> 2.  **Throw** //If an exception is found, it will throw an exception.
> 3.  **After catching** //throwing, it will catch the exception and execute its own body.

我们还有一个关键词叫做**最后**，不管有没有异常，它都会一直执行。在这里，我们有一些总是需要执行的重要代码。

> **注意:**如果程序通过 **exitProcess(Int)** 或 **abort()** 退出，则**最后**将不会执行。

#### **如何使用**试捕**最后？**

```kt
try
{
  // your code which
  // may throw an exception
}
catch(ex : ExceptionName)
{
  // Exception handle code
}
finally
{
  // this will execute every time
  // either we found exception or not
}
```

**示例 1:** 除以零

## 我的锅

```kt
fun main()
{
    try
      {
      // calling the function
      divide(10, 0) 
    }
    catch (ex : Exception)
    {
      // or you can also write your
      // own handle here
      println(ex.message) 
    }
}

// function which may give exception
fun divide(a : Int, b : Int)
{
    if (b == 0)
        throw Exception("Divide by zero") 
    // even if you didn't write
    // this throw it will work fine.
    println("Division is :" + a / b)
}
```

**输出:**

```kt
Divide by zero

```

**示例 2:** 让我们使用 try-catch 和 finally 来尝试相同的代码。

## 我的锅

```kt
fun main()
{
    // first try block
    try 
    {
      // didn't throw any exception
      divide(20, 10) 
    }
    catch (ex : Exception)
    {
      // or you can also write your
      // own handle here
      println(ex.message) 
    }
    finally 
    {
      println("I'm executed")
    }

    // 2nd try block
    try 
    {
      // throw an exception
      divide(10, 0) 
    }
    catch (ex : Exception)
    {
      // or you can also write your
      // own handle here
      println(ex.message) 
    }
    finally 
    {
      println("I'm executed")
    }
}

fun divide(a : Int, b : Int)
{
    if (b == 0)
        throw Exception("Divide by zero") 
    println("Division is :" + a / b)
}
```

**输出:**

```kt
Division is : 2
I'm executed
Divide by zero
I'm executed

```

请注意，在上面的示例中，finally 在两种情况下都执行，无论是否发生异常。