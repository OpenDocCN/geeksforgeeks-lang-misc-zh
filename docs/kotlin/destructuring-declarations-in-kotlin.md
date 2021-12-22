# 破坏柯特林中的声明

> 原文:[https://www . geesforgeks . org/destruction-declarations-in-kot Lin/](https://www.geeksforgeeks.org/destructuring-declarations-in-kotlin/)

[Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) 以*析构声明*的形式，为程序员提供了一种处理类实例的独特方式。一个**析构声明**是一次创建并初始化多个变量的声明。
**例如:**

```
val (emp_id,salary) = employee
```

这多个变量对应于与实例关联的类的属性。这些变量可以按照您想要的任何方式独立使用。

```
println(emp_id+" "+salary)
```

析构声明基于**组件()**函数的概念。析构声明可以定义的变量的数量，类提供这些数量的组件函数，从组件 1()，组件 2()到组件 n()。默认情况下，科特林中的*数据类*实现组件功能。

编译为以下代码的析构声明:-

```
val emp_id = employee.component1()
val salary = employee.component2()

```

**从函数返回两个值的科特林程序–**

```
// A sample data class
data class Data(val name:String,val age:Int)

// A function returning two values
fun sendData():Data{
    return Data("Jack",30)
}

fun main(){
    val obj = sendData()
    //  Using instance to access properties
    println("Name is ${obj.name}")
    println("Age is ${obj.age}")

    // Creating two variables using  destructing declaration
    val (name,age) = sendData()
    println("Name is $name")
    println("Age is $age")

}
```

**输出:**

> 名字是杰克
> 年龄是 30
> 名字是杰克
> 年龄是 30

**注意:**如果要在析构声明中使用，组件函数定义必须在运算符关键字之前。

**未使用变量的下划线**
有时，您可能想要忽略析构声明中的一个变量。为此，用一个**下划线**代替它的名字。在这种情况下，不会调用给定变量的组件函数。

### lambdas 中的析构声明–

随着 **Kotlin 1.1** 的到来，析构声明语法也可以用于**λ参数**。如果一个 lambda 参数有一个 **Pair** 类型的参数或者其他声明组件函数的类型，那么我们可以通过将它们放在括号中来引入新的参数。规则与上面定义的相同。

**使用 lambda 参数的析构声明的 Kotlin 程序–**

```
fun main(){
    val map = mutableMapOf<Int,String>()
    map.put(1,"Ishita")
    map.put(2,"Kamal")
    map.put(3,"Kanika")
    map.put(4,"Minal")
    map.put(5,"Neha")
    map.put(6,"Pratyush")
    map.put(7,"Shagun")
    map.put(8,"Shashank")
    map.put(9,"Uday")
    map.put(10,"Vandit")
    println("Initial map is")
    println(map)
    // Destructuring a map entry into key and values
    val newmap = map.mapValues { (key,value) -> "Hello ${value}" }
    println("Map after appending Hello")
    println(newmap)
}
```

**输出:**

> 初始地图为
> {1=Ishita，2=Kamal，3=Kanika，4=Minal，5=Neha，6=Pratyush，7=Shagun，8 = Shashank，9=Uday，10=Vandit}
> 追加 Hello
> 后的地图{1=Hello Ishita，2=Hello Kamal，3=Hello Kanika，4=Hello Minal，5=Hello Neha，6=Hello Pratyush，7=Hello Shagun，8=Hello Shashank，9=Hello Uday，11

如果析构参数的一个组件没有被使用，我们可以用下划线替换它，以避免调用组件函数:

```
map.mapValues { (_,value) -> "${value}" }
```