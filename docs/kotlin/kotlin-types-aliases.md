# 柯特林类型别名

> 原文:[https://www.geeksforgeeks.org/kotlin-types-aliases/](https://www.geeksforgeeks.org/kotlin-types-aliases/)

假设您正在创建一个项目，其中您定义了两个名称相同但包不同的类，并且您必须同时使用它们。第二种一般需要使用全包名点类名格式。例如，我们有一个名为“课程”的类，一个在“com.gfg.apps”包中，另一个在“com.gfg_practice.apps”中，我们可以使用简单的导入来使用其中的一个，如果我们想使用第二个，我们必须使用完整的包名，如“com.gfg_practice.apps.courses”。
在[科特林](https://www.geeksforgeeks.org/introduction-to-kotlin/)中，我们对此有一个解决方案，命名为**类型别名**。类型别名为现有类型提供了一个替代名称(在我们的例子中，它是一个类)。
在上面的场景中，我们可以做到:

```
typealias course = com.gfg_practice.apps.courses 
```

并且可以在任何我们想要的地方使用包“com.gfg_practice.apps”中的课程，而无需每次使用时都定义较长的版本。
**科特林程序演示类型别名–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
// here we define a type alias named Login_details
// which will take two strings as parameters
typealias Login_detials = Pair <String, String>
fun main() {
    // we are setting two users but we don't
    // have to define Pair each time while using it
    val my_details = Login_detials("Username1", "Password1")
    //instead we can directly use our type alias Credentials.
    val my_details2 = Login_detials("Username2", "Password2")

    println(my_details)
    println(my_details2)
}
```

**输出:**

```
(Username1, Password1)
(Username2, Password2)
```

**科特林计划演示–**

## Java 语言(一种计算机语言，尤用于创建网站)

```
typealias Number<T> = (T) -> Boolean
// defined a type alias named Number,  > is used as a separator here

fun main() {
    //it is used to loop through each element of the below list
    val x: Number<Int> = { it > 0 }
    //filter method only print those element which
    // satisfies the condition (numbers > 0)
    println("Positive numbers in the list are: "
            +listOf(11, -1, 10, -25, 55 , 43, -7).filter(x))

}
```

**输出:**

```
Positive numbers in the list are: [11, 10, 55, 43]
```