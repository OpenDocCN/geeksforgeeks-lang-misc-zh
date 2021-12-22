# 科特林变量

> 原文:[https://www.geeksforgeeks.org/kotlin-variables/](https://www.geeksforgeeks.org/kotlin-variables/)

在 Kotlin 中，每个变量都应该在使用前声明。如果不声明变量，试图使用该变量会产生语法错误。变量类型的声明还决定了允许存储在内存位置的数据类型。

对于局部变量，变量的类型可以从初始化的值中推断出来。

```
var rollno = 55
var name = "Praveen"
println(rollno)
println(name)

```

上面我们有局部变量*rollino*，它的值是 55，它的类型是 Integer，因为文字类型是 **Int** ，另一个变量是 *name* ，它的类型是 **String** 。

在 Kotlin 中，变量使用两种类型声明–

1.  **Do not use the keyword **val** variably.**
***   Use the variable **var** keyword.**

### 不可变变量–

**不可变**也叫只读变量。因此，我们不能更改使用 *val* 关键字声明的变量的值。

```
val myName = "Gaurav"
myName = "Praveen"    // compile time error

// It gives error Kotlin Val cannot be reassigned

```

**注意:**不可变变量不是常量，因为可以用变量值初始化。这意味着不可变变量的值不需要在编译时知道，如果它是在重复调用的构造中声明的，它可以在每次函数调用时采用不同的值。

```
var myBirthDate = "02/12/1993"
val myNewBirthDate = myBirthDate
println(myNewBirthDate)

```

### 可变变量–

在**可变**变量中，我们可以改变变量的值。

```
var myAge = 25
myAge = 26            // compiles successfully
println("My new Age is ${myAge}")

```

**输出:**

```
My new Age is 26
```

**变量的作用域–**
变量只存在于代码块({…………)中。})声明的位置。您不能在循环外访问变量。同一个变量可以在嵌套循环中声明——因此，如果一个函数包含一个参数 x，并且我们在同一个循环中声明了一个新的变量 x，那么循环中的 x 与参数不同。

**命名约定–**
每个变量都应该使用**lower case**来命名。

```
val myBirthDate = "02/12/1994"

```