# 科特林数据类

> 原文:[https://www.geeksforgeeks.org/kotlin-data-classes/](https://www.geeksforgeeks.org/kotlin-data-classes/)

我们经常创建类来保存一些数据。在这样的类中，一些*标准函数*通常可以从数据中推导出来。在科特林，这种类型的类被称为*数据类*，并被标记为**数据**。

**数据示例:**

```kt
data class Student(val name: String, val roll_no: Int)
```

编译器会自动派生以下函数:

*   等于()
*   hashCode()
*   toString()
*   复制()

### 创建数据类的规则–

数据类必须满足以下要求以确保一致性:

*   主构造函数需要至少有一个参数。
*   所有主构造器参数需要标记为*值*或*值*。
*   数据类不能是抽象的、开放的、密封的或内部的。
*   数据类只能实现接口。

### toString()

此函数返回数据类中定义的所有参数的字符串。
**例:**

```kt
fun main(args: Array<String>) 
{
    //declaring a data class 
    data class man(val roll: Int,val name: String,val height:Int)

    //declaring a variable of the above data class 
    //and initializing values to all parameters

    val man1=man(1,"man",50)

    //printing all the details of the data class
    println(man1.toString());
}
```

**输出:**

```kt
man(roll=1, name=man, height=50)

```

**注意:**
编译器只对自动生成的函数使用主构造函数内部定义的属性。
不包括在类体中声明的属性。

**示例:**

```kt
fun main(args: Array<String>) 
{
    //declaring a data class 
    data class man(val name: String)
    {
        //property declared in class body
        var height: Int = 0;
    }

    //declaring a variable of the above data class and 
    //initializing values to all parameters

    val man1=man("manish")
    //class body properties must be assigned uniquely
    man1.height = 70

    //this method prints the details of class that 
    //are declared in primary constructor
    println(man1.toString());

    //printing the height of man1 
    println(man1.height);
}
```

**输出:**

```kt
man(name=manish)
70

```

这里*高度*不被 toString()函数使用。

### 复制()

有时我们需要复制一个对象，它的某些属性发生一些变化，而其他属性保持不变。
在这种情况下**复制**()功能被使用。
**属性副本()**

*   它复制主构造函数中定义的所有参数或成员
*   如果已定义，两个对象可以具有相同的主参数值和不同的类体值

**副本声明()**

```kt
fun copy(name: String = this.x, age: Int = this.y) = user(x, y)
```

其中**用户**为数据类:用户(String，Int)。

**例**

```kt
fun main(args: Array<String>) 
{
    //declaring a data class 
    data class man(val name: String, val age: Int)
    {
        //property declared in class body
        var height: Int = 0;
    }

    val man1 = man("manish",18)

    //copying details of man1 with change in name of man
    val man2 = man1.copy(name="rahul")

    //copying all details of man1 to man3
    val man3 = man1.copy();

    //declaring heights of individual men
    man1.height=100
    man2.height=90
    man3.height=110

    //man1 & man3 have different class body values,
    //but same parameter values

    //printing info all 3 men
    println("${man1} has ${man1.height} cm height")
    println("${man2} has ${man2.height} cm height")
    println("${man3} has ${man3.height} cm height")

}
```

**输出:**

```kt
man(name=manish, age=18) has 100 cm height
man(name=rahul, age=18) has 90 cm height
man(name=manish, age=18) has 110 cm height

```

### hashCode()和 equals()

*   **哈希码**()函数返回对象的*哈希码*值。
*   **等于**()如果两个对象具有相同的内容，并且其工作方式类似于“==”，但是对于**浮点**和**双**值的工作方式不同，则该方法返回 true。

**hashCode()的声明:**

```kt
open fun hashCode(): Int

```

**hashCode()**的属性

*   在同一对象上声明两次的两个哈希代码将相等。
*   如果两个对象按照**等于**()的方法相等，那么返回的哈希码
    也将相同

```kt
fun main(args: Array<String>) 
{
    //declaring a data class 
    data class man(val name: String, val age: Int)

    val man1 = man("manish",18)
    val man2 = man1.copy(name="rahul")
    val man3 = man1.copy();

    val hash1=man1.hashCode();
    val hash2=man2.hashCode();
    val hash3=man3.hashCode();

    println(hash1)
    println(hash2)
    println(hash3)

    //checking equality of  these hash codes
    println("hash1 == hash 2 ${hash1.equals(hash2)}")
    println("hash2 == hash 3 ${hash2.equals(hash3)}")
    println("hash1 == hash 3 ${hash1.equals(hash3)}")

}
```

**输出:**

```kt
835510190
-938448478
835510190
hash1 == hash 2 false
hash2 == hash 3 false
hash1 == hash 3 true

```

**说明:**
*man1* 和 *man2* 的对象内容相同，所以是相等的，因此具有相同的哈希码值。