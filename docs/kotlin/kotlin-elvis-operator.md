# 柯特林猫王符(？:)

> 原文:[https://www.geeksforgeeks.org/kotlin-elvis-operator/](https://www.geeksforgeeks.org/kotlin-elvis-operator/)

**猫王符(？:)**用于返回非空值，即使条件表达式为空。它也用于检查值的空值安全性。

在某些情况下，我们可以声明一个可以保存空引用的变量。如果一个变量 st 包含空引用，在程序中使用 st 之前，我们将检查它的可空性。如果变量 st 被发现不为 null，那么它的属性将使用其他非 null 值。

```kt
// Kotlin Program without using Elvis Operator
fun main(args: Array<String>)
{  
var st: String? = null 
var st1: String? = "Geeks for Geeks" 
var len1:  Int = if (st != null) st.length else -1 
var len2:  Int = if (st1 != null) st1.length else -1 
println("Length of st is ${len1}")  
println("Length of st1 is ${len2}")  
}  
```

**输出:**

```kt
Length of st is -1
Length of st1 is 15

```

```kt
// Kotlin Program using Elvis Operator
fun main(args: Array<String>)
{    
var st: String? = null 
var st1: String? = "Geeks for Geeks" 
var len1:  Int = st ?.length ?: -1 
var len2:  Int = st1 ?.length ?:  -1 

println("Length of st is ${len1}")  
println("Length of st1 is ${len2}")  
} 
```

**输出:**

```kt
Length of st is -1
Length of st1 is 15

```