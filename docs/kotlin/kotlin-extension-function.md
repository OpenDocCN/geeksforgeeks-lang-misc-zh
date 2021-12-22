# 科特林扩展功能

> 原文:[https://www.geeksforgeeks.org/kotlin-extension-function/](https://www.geeksforgeeks.org/kotlin-extension-function/)

Kotlin 让程序员能够通过**给现有的类增加更多的功能**，而无需继承它们。这是通过一个名为**扩展**的特性实现的。当一个函数被添加到现有的类中时，它被称为**扩展函数**。

要向类添加扩展函数，定义一个追加到类名的**新函数**，如下例所示:

```
package kotlin1.com.programmingKotlin.chapter1

// A sample class to demonstrate extension functions
class Circle (val radius: Double){
    // member function of class
    fun area(): Double{
        return Math.PI * radius * radius;
    }
}
fun main(){
    // Extension function created for a class Circle
    fun Circle.perimeter(): Double{
        return 2*Math.PI*radius;
    }
    // create object for class Circle
    val newCircle = Circle(2.5);
    // invoke member function
    println("Area of the circle is ${newCircle.area()}")
    //invoke extension function
    println("Perimeter of the circle is ${newCircle.perimeter()}")
}
```

**输出:**

```
Area of the circle is 19.634954084936208
Perimeter of the circle is 15.707963267948966

```

**解释:**
在这里，一个新的函数用点符号追加到类 **`Circle.perimeter()`** 中，它的返回类型是 Double。在主函数中，创建一个对象来实例化类 Circle，并在 **`println()`** 语句中调用该函数。当成员函数被调用时，它返回圆的面积，类似地，扩展函数返回圆的周长。

### 使用扩展函数的扩展库类–

Kotlin 不仅允许扩展用户定义的类，还允许扩展**库类**。扩展函数可以添加到库类中，并以类似于用户定义类的方式使用。

以下示例演示了为用户定义的类创建的扩展函数-

```
fun main(){

    // Extension function defined for Int type
    fun Int.abs() : Int{
        return if(this < 0) -this else this
    }

    println((-4).abs())
    println(4.abs())
}
```

**输出:**

```
4
4

```

**说明:**这里，我们已经使用扩展函数扩展了库函数。我们对整数值执行了模运算。我们已经传递了整数值-4 和 4，并获得了两者的正值。如果参数值小于 0，则返回-(值)，如果参数值大于 0，则返回相同的值。

### 扩展是静态解析的–

关于扩展函数需要注意的一点是它们是**静态解析的**，即执行哪个扩展函数完全取决于调用它的表达式的类型，而不是运行时表达式最终执行时解析的类型。

下面的例子将使上述论点变得清晰:

```
// Open class created to be inherited
open class A(val a:Int, val b:Int){
}

// Class B inherits A
class B():A(5, 5){}

fun main(){

    // Extension function operate defined for A
    fun A.operate():Int{
        return a+b
    }

    // Extension function operate defined for B
    fun B.operate():Int{
        return a*b;
    }

    // Function to display static dispatch
    fun display(a: A){
        print(a.operate())
    }

    // Calling display function 
    display(B())
}
```

**输出:**

```
10

```

**说明:**
如果你熟悉 Java 或者其他任何面向对象的编程语言，你可能会在上面的程序中注意到，由于**B 类**继承了**A 类**，传递给 display 函数的参数是**B 类**的一个实例。根据**动态方法调度**的概念，输出应该是 **25** ，但是由于扩展函数是静态解析的，所以在类型 a 上调用操作函数，因此输出是 10。

### 可空接收器–

扩展函数也可以定义为类类型**可空**。在这种情况下，当在扩展函数中添加对 null 的检查并返回适当的值时。

作为可空接收器的扩展函数示例–

```
// A sample class to display name name
class AB(val name: String){
    override fun toString(): String {
        return "Name is $name"
    }
}

fun main(){
    // An extension function as a nullable receiver
    fun AB?.output(){
        if(this == null){
            println("Null")
        }else{
            println(this.toString())
        }
    }

    val x = AB("Charchit")

    // Extension function called using an instance
    x.output()
    // Extension function called on null
    null.output()
}
```

**输出:**

```
Name is Charchit
Null

```

### 伴随对象扩展–

如果一个类包含伴随对象，那么我们也可以为伴随对象定义扩展函数和属性。

**伴随对象声明–**

```
class MyClass {
    // companion object declaration
    companion object {
        fun display(){
            println("Function declared in companion object")
        }
    }
}
fun main(args: Array<String>) {
   // invoking member function 
   val ob = MyClass.display()  
}
```

**输出:**

```
Function declared in companion object
```

就像调用伴随对象的常规成员函数一样，只使用类名作为限定符就可以调用扩展函数。
**伴随对象扩展示例–**

```
class MyClass {
    companion object {
        // member function of companion object
        fun display(str :String) : String{
            return str
        }
    }
} 
    // extension function of companion object
fun MyClass.Companion.abc(){
    println("Extension function of companion object")
}
fun main(args: Array<String>) {
    val ob = MyClass.display("Function declared in companion object")
    println(ob)
    // invoking the extension function 
    val ob2 = MyClass.abc()
}
```

**输出:**

```
Function declared in companion object
Extension function of companion object

```