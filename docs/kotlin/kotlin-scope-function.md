# 科特林–范围功能

> 原文:[https://www.geeksforgeeks.org/kotlin-scope-function/](https://www.geeksforgeeks.org/kotlin-scope-function/)

Kotlin 标准库中有几个函数有助于在对象上下文中执行代码块。使用 lambda 表达式在对象上调用这些函数会创建一个临时范围。这些函数称为**范围函数**。我们可以在没有名称的情况下访问这些函数的对象。听起来很困惑！让我们看一个例子，

**例:不使用范围函数**

## 我的锅

```
class Company() {
    lateinit var name: String
    lateinit var objective: String
    lateinit var founder: String
}

fun main() {
    // without using scope function

    // creating instance of Company Class
    val gfg = Company() 

    // initializing members of the class
    gfg.name = "GeeksforGeeks"
    gfg.objective = "A computer science portal for Geeks"
    gfg.founder = "Sandeep Jain"

    println(gfg.name)
}
```

**输出:**

```
GeeksforGeeks
```

**示例:使用范围函数**

## 我的锅

```
class Company() {
    lateinit var name: String
    lateinit var objective: String
    lateinit var founder: String
}

fun main() {
    // using scope function
    val gfg = Company().apply {
        // don't need to use object
        // name to refer members
        name = "GeeksforGeeks"
        objective = "A computer science portal for Geeks"
        founder = "Sandeep Jain"
    }
    println(gfg.name)
}
```

**输出:**

```
GeeksforGeeks
```

### 说明

您一定注意到了，当我们不使用作用域函数时，我们需要每次都写对象名来引用类的成员。在使用作用域函数时，我们可以直接引用没有对象名的成员。这是使用范围函数的方法之一。我们将在本文中了解更多关于它们的信息。

## **范围功能**

每个范围函数都有明确定义的用例，尽管它们几乎都有相同的结果。现在让我们看看每个作用域函数及其用例:

### 使用范围函数的应用

范围函数使代码更加**清晰**、**可读**、**简洁**，这是 Kotlin 语言的主要特点。

### 范围函数的类型

范围函数有五种类型:

1.  让
2.  奔跑
3.  随着
4.  应用
5.  也

这些功能中的每一个本质上都非常相似，只有细微的差别。决定使用哪个函数和什么时候使用通常是令人困惑的。因此，我们需要知道这些功能和它们的用例之间有什么不同。

**这些功能的差异:**

这些功能主要有两个区别:

1.  **引用上下文对象的方式**(即使用‘this’或‘it’关键字)
2.  **返回值**(即返回“上下文对象”或“lambda 结果”)

> **注意:** Context 对象是指我们在其上使用范围函数的对象。正如我们前面的例子——“gfg”是我们的上下文对象

**范围功能表:**

<figure class="table">

| 

功能

 | 

对象引用

 | 

返回值

 |
| --- | --- | --- |
| 

让

 | 它 | λ结果 |
| 

奔跑

 | 这 | λ结果 |
| 

随着

 | 这 | λ结果 |
| 

应用

 | 这 | 上下文对象 |
| 

也

 | 它 | 上下文对象 |

</figure>

### 1.字母函数

```
Context object  :   it 
Return value    :   lambda result
```

**用例:**

let 函数通常用于提供空安全调用。使用**安全呼叫接线员(？。)**带‘let’为空安全。它只使用非空值执行该块。

**示例:**

## 我的锅

```
fun main() {
    // nullable variable a
    // with value as null
    var a: Int? = null
    // using let function
    a?.let {
        // statement(s) will
        // not execute as a is null
        print(it)
    }
    // re-initializing value of a to 2
    a = 2
    a?.let {
        // statement(s) will execute
        // as a is not null
        print(a)
    }
}
```

**输出:**

```
2
```

**说明:**

如您所见，当“a”的值为“null”时，让函数简单地避开代码块。因此，解决了程序员最大的噩梦-**NullPointerException。**

### 2.应用函数

```
Context object   :    this
Return value     :    context object
```

**用例:**

顾名思义——“将这些应用于对象”。它可以用来操作接收器对象的成员，主要是初始化成员。

**示例:**

## 我的锅

```
class Company() {
    lateinit var name: String
    lateinit var objective: String
    lateinit var founder: String
}

fun main() {
    Company().apply {
        // same as founder = “Sandeep Jain”
        this.founder = "Sandeep Jain" 
        name = "GeeksforGeeks"
        objective = "A computer science portal for Geeks"
    }
}
```

### 3.带功能

```
Context object  :   this
Return value    :   lambda result
```

**用例:**

建议使用“with”在不提供 lambda 结果的情况下调用上下文对象上的函数。

**示例:**

## 我的锅

```
class Company() {
    lateinit var name: String
    lateinit var objective: String
    lateinit var founder: String
}

fun main() {
    val gfg = Company().apply {
        name = "GeeksforGeeks"
        objective = "A computer science portal for Geeks"
        founder = "Sandeep Jain"
    }

    // with function
    with(gfg) {
        // similar to println( "${this.name}" )
        println(" $name ")
    }
}
```

**输出:**

```
GeeksforGeeks
```

### 4.运行函数

```
Context object   :    this
Return value     :    lambda result
```

“run”函数可以说是“let”和“with”函数的组合。

**用例:**

当对象 lambda 包含初始化和返回值计算时使用。使用 run，我们可以执行空安全调用以及其他计算。

**示例:**

## 我的锅

```
class Company() {
    lateinit var name: String
    lateinit var objective: String
    lateinit var founder: String
}

fun main(args: Array<String>) {
    println("Company Name : ")
    var company: Company? = null
    // body only executes if 
    // company is non-null
    company?.run {     
        print(name)
    }
    print("Company Name : ")
    // re-initialize company
    company = Company().apply {
        name = "GeeksforGeeks"
        founder = "Sandeep Jain"
        objective = "A computer science portal for Geeks"
    }
    // body executes as 
    // 'company' is non-null
    company?.run {     
        print(name)
    }
}
```

**输出:**

```
Company Name : 

Company Name : GeeksforGeeks
```

**说明:**

当“公司”值为空时，运行的主体将被忽略。当它为非空时，主体执行。

### 5.也起作用

```
Context object   :    it
Return value     :    context object
```

**用例:**

当我们初始化对象成员时，它用于我们必须执行附加操作的地方。

**示例:**

## 我的锅

```
fun main() {
    // initialized
    val list = mutableListOf<Int>(1, 2, 3)

    // later if we want to perform 
    // multiple operations on this list
    list.also {
        it.add(4)
        it.remove(2)
        // more operations if needed
    }
    println(list)
}
```

**输出:**

```
[1, 3, 4]
```

### 对象引用

范围函数中有两种对象引用方式:

**1。这**

我们可以通过 lambda receiver 关键字–**这个**来引用上下文对象。**这个**关键字在**的【运行】、【配合】、【应用】**功能中做对象引用。

**示例:**

## 我的锅

```
Company().apply {
   // same as : name = "GeeksforGeeks"
   this.name = "GeeksforGeeks"   
   this.founder = "Sandeep Jain"
   this.objective = "A computer science portal for Geeks" 
}
```

> **注意:**我们可以排除**这个**关键字来指代类的成员。

**2。它**

let’和‘还’函数将对象的上下文作为 **lambda 参数。**

**示例:**

## 我的锅

```
Company().let {
   it.name = "GeeksforGeeks"
   it.founder = "Sandeep Jain"
   it.objective = "A computer science portal for Geeks"
}
```