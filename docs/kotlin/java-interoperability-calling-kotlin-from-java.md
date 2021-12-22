# Java 互操作性——从 Java 调用 Kotlin

> 原文:[https://www . geesforgeks . org/Java-互操作性-调用-kotlin-from-java/](https://www.geeksforgeeks.org/java-interoperability-calling-kotlin-from-java/)

开发 Kotlin 时，它只在 **JVM** 上工作，因此它提供了一套完整的特性，使得从 Java 调用 Kotlin 变得非常容易。例如，可以很容易地创建 Kotlin 类的对象，并且可以在 Java 方法中调用它们的方法。但是，关于如何在 [Java](https://www.geeksforgeeks.org/java/) 中使用 Kotlin 代码，有一些规则。

### 科特林属性–

Kotlin 中的一个属性在 Java 中被定义为一个与该属性同名的**私有字段**，以及**一个 getter 和 setter 函数**，其中 *get* 和 *set* 被放在属性名称的前面。这个私有字段存在于从 kotlin 文件生成的 java 类中。
例如，属性 **var age: Int** 在 Java 中被编译为以下代码–

```
private int age;

public int getAge(){
  return age;
}
public void setAge(int age){
  this.age = value;
}
```

可以使用类的对象访问这些属性，方式与在 Java 中相同。但是，如果属性名称以**开头是**，那么在 *getter* 函数的名称中会跳过 get 关键字。

### 包级功能–

在一个包中的 Kotlin 文件中定义的所有函数在一个类中被编译成 Java 中的**静态方法**，该类的**类名是包名和文件名**的组合。

例如，如果有一个名为**Kotlinprograms**的包和一个名为 **firstProgram.kt** 的 kotlink 文件，内容如下。

```
// Kotlin file

package kotlinPrograms

class myClass {

  fun add(val a:Int, val b:Int): Int {
   return a+b;
 }
}
```

可以使用以下语法在 Java 中调用该函数:

```
// Java
new kotlinPrograms.firstProgram.myClass()
kotlinPrograms.FirstProgramkt.add(3, 5);

```

我们可以使用 **@JvmName** 注释来更改生成的 Java 类的名称。

```
// Kotlin file
@file : Jvmname("Sample")

package kotlinPrograms

class myClass {

  fun add(val a:Int, val b:Int): Int {
   return a+b;
 }
}
```

可以使用以下语法在 Java 中调用该函数:

```
// Java
new kotlinPrograms.firstProgram.myClass()
kotlinPrograms.Sample.add(3, 5);

```

但是，多个文件具有相同的名称在逻辑上是错误的。为了克服这个问题，Kotlin 为它的编译器提供了创建一个外观类的能力，这个外观类有一个特定的名称，并且包含来自所有同名文件的所有声明。为了能够创建这样一个外观类，所有文件中的注释**@ jvmmultipileclass**注释。

**例**

```
// Kotlin code
@file:JvmName("Sample")
@file:JvmMultiFileClass

package sample.example

fun print(){.......}
```

**另一个柯特林文件–**

```
// Kotlin code
@file:JvmName("Sample")
@file:JvmMultiFileClass

package sample.example

fun printString(){.......}
```

这两个函数都可以使用以下语法在 Java 中调用:

```
// Java calling statements
sample.example.Sample.print()
sample.example.Sample.printString()

```

### 静态字段–

Kotlin 中的**属性**在**命名对象或伴随对象**中声明，在 Java 中用作**静态字段**。要访问 Java 中的这些字段，必须使用 **@JvmField** 注释、lateinit 修饰符进行注释，或者必须使用 **const** 修饰符进行声明。

**例**:

```
// filename Program.kt

// Property in a companion object
class abc{
 companion object{
      @JvmField
      val x = 5;
  }
}

// A constant property
const val y = 5;
```

```
//Java Usage
abc.x
Programkt.y

```

### 静态方法–

在包级别定义的方法总是作为静态方法在 Java 文件中生成。如果使用 **@JvmStatic** 注释，则在**命名对象**和**伴随对象**中定义的方法也作为静态方法生成。这个注释将下面的函数声明为类函数。

**伴随对象示例**

```
// filename Programs.kt
class abc {
  companion object {
     @JvmStatic fun add(val a:Int, val b:Int):Int{
        return a+b;
      }
     fun sub(val a:Int, val b:Int):Int{
        return a-b;
      }
   }
}
```

```
//Java usage
abc.add(); // works fine
abc.sub(); // error: not a static method
abc.Companion.add(); // instance method remains
C.Companion.sub(); // the only way it works

```

同样，它也适用于命名对象。

### 实例字段–

Kotlin 提供了在 Java 中将属性用作实例字段的功能。为此，请使用 **@JvmField** 注释对属性进行注释。这些实例字段具有与 Kotlin 属性相同的可见性。但是，该属性必须有一个支持字段，并且不能用**私有**、**开放**、**常量**和**覆盖**修饰符来声明。

**例**

```
// Kotlin code
class ABC(c: Int){
 @JvmField val id = c
}
```

这个属性现在可以在 Java 中作为

```
ABC obj = new ABC(5);
System.out.println(obj.id);

```

### 选中的例外

**Kotlin 中的所有异常都没有被选中。**因此，Kotlin 函数的 Java 签名既不声明也不处理抛出的异常。为了克服这个问题，必须用指定将要抛出的异常的 **@Throws** 注释来注释 Kotlin 函数。在这种情况下，Java 签名也将声明要抛出的函数。

**例**

```
// A sample Kotlin function

// filename program.kt
package Sample

fun print(){
 throws IOException()
}
```

```
// Java code trying to call the above  function
try {
    Sample.Program.print(); 
    }
   // This statement causes error because does not declare IOexception in throws list
   catch(IOException e) { 
}

```

因此，为了解决错误，我们在顶部声明**@抛出**注释。

```
// Overcoming the problem with @Throws annotation
package Sample

@Throws(IOException::class)
fun print()
{
throws IOException()
}
```