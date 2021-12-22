# Kotlin 异常处理|尝试、接球、投球，最后

> 原文:[https://www . geeksforgeeks . org/kot Lin-异常处理-尝试-捕获-抛出-最后/](https://www.geeksforgeeks.org/kotlin-exception-handling-try-catch-throw-and-finally/)

异常是指在程序执行期间(即运行时)发生的不必要或意外的事件，它会中断程序指令的正常流动。异常处理是一种技术，使用它我们可以处理错误，并防止运行时崩溃，从而停止我们的程序。

有两种类型的例外–

1.  **已检查异常**–通常在方法上设置并在编译时检查的异常，例如 IOException、FileNotFoundException 等
2.  **未检查的异常**–通常由于逻辑错误而在运行时检查的异常，例如 NullPointerException、ArrayIndexOutOfBoundException 等

### 科特林例外–

在 Kotlin 中，我们只有未检查的异常，并且只能在运行时捕获。所有的异常类都是**可投掷**类的后代。

我们一般使用**抛出**-表达式，来抛出一个异常对象–

```
throw Exception("Throw me")
```

一些常见的例外是:

*   **NullPointerException:** 当我们试图调用 null 对象上的属性或方法时抛出。
*   **算术异常:**对数字进行无效算术运算时抛出。被零除。
*   **SecurityException:** 抛出表示安全违规。
*   **arrayindextofboundexception:**当我们试图访问数组的无效索引值时抛出。

**抛出算术异常的柯特林程序–**

```
fun main(args : Array<String>){
    var num = 10 / 0      // throws exception
    println(num)
}
```

**输出:**

```
Exception in thread "main" java.lang.ArithmeticException: / by zero
```

在上面的程序中，我们用值 **10/0** 初始化了 **`num`** 变量，但是我们知道在算术中不允许被零除。当我们试图运行程序时，它抛出了一个异常。

为了解决这个问题，我们必须使用 try-catch 块。

### Kotlin 试抓块–

在 Kotlin 中，我们在程序中使用 try-catch 块进行异常处理。try 块包含负责引发异常的代码，catch 块用于处理异常。该块必须在 main 或其他方法中写入。Try block 后面应该跟 catch block 或 finally block，或者两者都跟。

**尝试捕获块的语法–**

```
try {
   // code that can throw exception
} catch(e: ExceptionName) {
   // catch the exception and handle it
}

```

**使用 try-catch 块进行算术异常处理的 Kotlin 程序–**

```
import kotlin.ArithmeticException

fun main(args : Array<String>){
    try{
        var num = 10 / 0
    }
    catch(e: ArithmeticException){
        // caught and handles it
        println("Divide by zero not allowed")
    }
}
```

**输出:**

```
Divide by zero not allowed
```

**说明:**
在上面的程序中，我们使用了试捕块。可以抛出异常的 **`num`** 变量被包含在 try 块的大括号内，因为算术中没有定义除零。异常被 catch 块捕获并执行 **`println()`** 语句。

### Kotlin try-catch 块作为表达式–

正如我们已经知道的，表达式总是返回值。我们可以在程序中使用 kotlin try-catch 块作为**表达式**。表达式返回的值将是 try 块的最后一个表达式或 catch 块的最后一个表达式。如果代码中出现异常，catch 块将返回该值。

**使用 try-catch 作为表达式的 Kotlin 程序–**

```
fun test(a: Int, b: Int) : Any {
    return try {
        a/b
        //println("The Result is: "+ a / b)
    }
    catch(e:Exception){
        println(e)
        "Divide by zero not allowed"
    }
}
// main function
fun main(args: Array<String>) {
    // invoke test function
    var result1 = test(10,2  ) //execute try block
    println(result1)
    var result = test(10,0 )   // execute catch block
    println(result)
}
```

**输出:**

```
5
java.lang.ArithmeticException: / by zero
Divide by zero not allowed

```

在上面的代码中，我们使用了 try-catch 作为表达式。在程序顶部声明一个函数测试，并使用 try-catch 块返回一个值。我们已经从主方法中调用了 **`test`** 函数，并传递了参数值(10，2)测试函数评估参数并返回尝试值 **(10/2 = 5)** 。但是在下一次调用中，我们传递了 **(b=0)** ，这一次异常被捕获并返回捕获块的表达式。

### 科特林终于挡住–

在 Kotlin 中，finally 块总是被执行，而不管 catch 块是否处理了异常。所以它被用来执行重要的代码语句。
我们也可以使用 finally block 和 try block，并从那里跳过 catch block。

**带有 try 块的最终块的语法–**

```
try {
   // code that can throw exception
} finally {
   // finally block code
}

```

**使用最终块和尝试块的柯特林程序–**

```
fun main(args : Array<String>){
    try{
        var ar = arrayOf(1,2,3,4,5)
        var int = ar[6]
        println(int)
    }
  finally {
        println("This block always executes")
    }
}
```

**输出:**

> 这个块总是在线程“main”中执行
> 异常

在上面的程序中，我们对 finally 块使用了 try，并跳过了 catch 块。这里，异常不是由 catch 块处理，而是执行 finally 块。

**带有 try-catch 块的最终块的语法–**

```
try {
   // code that can throw exception
} catch(e: ExceptionName) {
   // catch the exception and handle it.
} finally {
  // finally block code
}

```

我们也可以使用 try、catch 和 finally 将所有块放在一起。
**柯特林程序的使用最后用试捕块来阻止-**

```
fun main (args: Array<String>){  
    try {  
        var int = 10 / 0  
        println(int)  
    } catch (e: ArithmeticException) {  
        println(e)  
    } finally {  
        println("This block always executes")  
    }  
}  
```

**输出:**

```
java.lang.ArithmeticException: / by zero
This block always executes

```

### Kotlin throw 关键字–

在 Kotlin 中，我们使用 throw 关键字来抛出一个显式异常。它还可以用于引发自定义异常。

**使用 throw 关键字的 Kotlin 程序–**

```
fun main(args: Array<String>) {
    test("abcd")
    println("executes after the validation")
}
fun test(password: String) {
    // calculate length of the entered password and compare
    if (password.length < 6)
        throw ArithmeticException("Password is too short")
    else
        println("Strong password")
}
```

**输出:**

```
Exception in thread "main" java.lang.ArithmeticException: Password is too short
```