# Java 互操作性——从 Kotlin 调用 Java

> 原文:[https://www . geesforgeks . org/Java-互操作性-调用-java-from-kotlin/](https://www.geeksforgeeks.org/java-interoperability-calling-java-from-kotlin/)

因为开发 Kotlin 时考虑到了与 [Java](https://www.geeksforgeeks.org/java/) 的互操作性。它使得从内部使用 Java 代码变得更加容易。一个柯特林[类](https://www.geeksforgeeks.org/kotlin-class-and-objects/)或者一个[函数](https://www.geeksforgeeks.org/kotlin-functions/)可以简单的引用 [Java 类](https://www.geeksforgeeks.org/classes-objects-java/)及其方法。

### Java 中的获取器和设置器–

Java 类中定义的所有类型的 getters 和 setters 在 Kotlin 中表示为属性。因此，要访问 Java 类的数据成员的获取器和设置器，它必须作为属性在 Kotlin 中引用。
T3】Java 文件申报为 myjava.javaT5】

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// Java class
public class myjava {
  private int value;
  public int getValue(){
       return value;
  }
  public void setValue(int value){
       this.value = value;
  }
}
```

**柯特林文件声明为 mykotlin.kt**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// Kotlin file
fun main(){
   val obj = myjava()
   obj.value = 5 // This will call the setter function
   println(obj.value) // This will call the getter function
}
```

**输出:**

```kt
5
```

### 方法–

从 Kotlin 内部调用 Java 方法是一个简单的概念。在 Java 和 Kotlin 中，要提供的参数类型是相同的，函数的返回类型也是如此。此规则的唯一例外是 void 返回类型。Java 中那些有 void 返回类型的函数，在 Kotlin 中返回一个**单元**类型。因此，该值可以存储在 Kotlin 中，因为 Unit 作为一种类型存在。
T3】Java 文件申报为 myjava.javaT5】

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// Java code
public class myjava {
    public int add(int a, int b){
        return a+b;
    }
}
```

**柯特林文件声明为 mykotlin.kt**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// Kotlin file
fun main(args: Array<String>) {
    val obj = myjava()
    val ans = obj.add(4, 5)
    println("The sum of two numbers is "+ans)
}
```

**输出:**

```kt
The sum of two numbers is 9
```

**注意–**Kotlin 的一些关键字在 Java 中很容易被用作有效的标识符。例如——任何、密封的、物体等。**如果碰巧是这种情况，那么在科特林中使用标识符，用一个倒勾字符(`)将它们括起来。**
例如，如果一个 Java 类 XYZ 恰好有一个名为 any 的方法，那么这个方法可以在 Kotlin 中调用为:

```kt
obj.`any`() // obj is the instance of the class XYZ
```

### 静态成员–

Java 中一个类的静态成员变成了 Kotlin 中一个伴随对象的成员。但是，这些伴随对象不能直接在表达式中使用。要访问，其成员使用 Java 中定义的成员的完全限定名。
T3】Java 文件申报为 myjava.javaT5】

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// Java Code
package mypackage;
    public class myjava {
    public static void display() {
        System.out.println("Call successful")
    }
}
```

**柯特林文件声明为 mykotlin.kt**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// declare kotlin package
package myktpackage
// import java class using java package
import mypackage.myjava 

fun main(args: Array<String>) {
    // calling static member of java class
    val str = myjava.display()
    println(str)
}
```

**输出:**

```kt
Call successful
```

### Java 数组–

Kotlin 支持一种**不变的**形式的数组，即特定类型的数组不能赋给 Kotlin 中任何类型的数组，这与可以赋给 Object 类型数组的 Java 数组不同。
另外，Kotlin 不支持将子类类型的数组分配给超类类型的数组。
现在，由于 Kotlin 不提供基元类型的数组，所以它提供了几个专门的类来表示 Java 中基元类型的数组。这些类与 Array 类没有任何关系，为了获得最佳性能，它们被编译成基本的 java 数组。无论数组的使用方式如何，这种到字节码的转换都不会引入额外的开销。
**Java 文件声明为 myjava.java**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// Java Code
public class myjava {
    int result = 0;
    public int compute(int[] array)
    {
        for(int a: array){
            result = result + a;
        }
        return result;
    }
}
```

**柯特林文件声明为 mykotlin.kt**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// Kotlin code
fun main(args: Array<String>) {
    // Kotlin code
    val obj = myjava()
    val array = intArrayOf(1, 2, 3, 4, 5, 6)
    var sum = obj.compute(array)
    println("The sum of an array is "+sum)
}
```

**输出:**

```kt
The sum of an array is 21
```

### java varargs

Java 支持函数中变长参数的概念，即当一个函数的参数数量事先未知，但其类型已知时，我们声明一个 varargs 参数。Kotlin 不提供 varargs 参数，但是，要想在 Java 中完全运行，**它支持一个特殊的扩展运算符(*)来调用具有 varargs 参数的函数。**
**Java 文件宣称为 myjava.java**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// Java code
public class myjava {
    public void myfunc(String str,int... numbers) {
        System.out.println("Passed string is " + str);
        for (int n : numbers) {
            System.out.print(" "+n);
        }
    }
}
```

**柯特林文件声明为 mykotlin.kt**

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
// Kotlin code
fun main(args: Array<String>) {
    val obj = myjava()
    val array = intArrayOf(10, 20, 30)
    obj.myfunc("Geeks", *array)
}
```

**输出:**

```kt
Passed string is Geeks
 10 20 30
```

### Java 和 Kotlin 映射类型–

Kotlin 中的类型不同于 Java 中的类型。然而，为了保持互操作性，Kotlin 提供了从 Java 类型到 Kotlin 类型的映射。这种映射发生在编译时，并且没有观察到运行时性能的显著变化。
**Java 原语类型映射到以下原语类型:**

<figure class="table">

| **Java 类型** | 科特林型 |
| 字节 | 盆地。字节 |
| 短的 | 科特林。短的 |
| （同 Internationalorganizations）国际组织 | kotlin.Int |
| 长的 | 我的天啊 |
| 茶 | 科特林！科特林！Char(字符) |
| 漂浮物 | 科特林，浮起来 |
| 两倍 | 科特林！科特林！双份 |
| 布尔 | kotlin.Boolean |

</figure>

**Java . lang 包中定义的一些内置类也映射到了 Kotlin 类。**T3】

<figure class="table">

| **Java 类型** | 科特林型 |
| java.lang.Object | 科特林。任何！ |
| java.lang .可克隆 | 科特林。可克隆！ |
| Java . lang . compatible | 科特林。可比！ |
| java.lang.Enum | 科特林，枚举！ |
| java.lang.annotation | 科特林。批注！ |
| java.lang.CharSequence | 科特林！科特林！CharSequence(顺序) |
| java.lang.String | 科特林，字符串！ |
| java.lang.Number | 科特林。号码！ |
| java.lang.Throwable | 科特林。可投掷！ |

</figure>

**Java 原语数据类型的装箱类型被映射到 Kotlin 中的可空类型。**T3】

<figure class="table">

| **Java 类型** | 科特林型 |
| java.lang.Byte | 盆地。字节？ |
| java.lang.Short | 科特林。短？ |
| java.lang.Integer | -是吗？ |
| java.lang.Long | -是啊？ |
| java.lang .字符 | 科特林！科特林！查尔？ |
| java.lang.Float | 科特林浮？ |
| java.lang.Double | 科特林！科特林！双份？ |
| java.lang.Boolean | 科特林布尔？ |

</figure>