# 科特林的平等评价

> 原文:[https://www . geesforgeks . org/equality-evaluation-in-kot Lin/](https://www.geeksforgeeks.org/equality-evaluation-in-kotlin/)

[Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) 提供了一个额外的功能，可以通过两种不同的方式比较特定类型的实例。这个特性使得 Kotlin 不同于其他编程语言。
两种类型的平等是–

*   结构平等
*   参照平等

### 结构平等–

通过 **==运算符**及其逆运算**检查结构相等性！=操作员**。默认情况下，包含 **x==y** 的表达式被转换为该类型的 **equals()** 函数的调用。

```kt
x?.equals(y) ?: (y === null)
```

声明如果 **x** 不等于空，它调用函数**等于(y)** ，否则如果 **x** 被发现为空，它将检查 **y** 是否参考等于空。
**注意–**当(x == null)时，它将自动转换为引用等式(x === null)，因此这里不需要代码优化。
因此，要在类型的实例上使用==该类型必须重写 equals()函数。**对于字符串，结构相等比较内容**。

### 参考等式–

柯特林中的参照等式是通过 **===运算符**及其逆运算符**来检查的！==操作员**。只有当一个类型的两个实例都指向内存中的相同位置时，该等式才返回 true。当在运行时转换为基元类型的类型上使用时，===检查被转换为==检查和！==支票被转换成！=检查。
**科特林程序，演示结构和参照的平等–**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
class Square(val side: Int) {
    override fun equals(other: Any?): Boolean {
        if(other is Square){
            return other.side == side
        }
        return false
    }
}
// main function
fun main(args :Array<String>) {
    val square1 = Square(5)
    val square2 = Square(5)
    // structural equality
    if(square1 == square2) {
        println("Two squares are structurally equal")
    }
    // referential equality
    if(square1 !== square2) {
        println("Two squares are not referentially equal")
    }
}
```

**输出:**

```kt
Two squares are structurally equal
Two squares are not referentially equal
```