# 科特林的枚举类

> 原文:[https://www.geeksforgeeks.org/enum-classes-in-kotlin/](https://www.geeksforgeeks.org/enum-classes-in-kotlin/)

在编程中，有时需要类型只有特定的值。为此，引入了枚举的概念。枚举是常数的命名列表。
在 Kotlin 中，像许多其他编程语言一样，一个**枚举**有它自己的专用类型，表示某个东西有许多可能的值。与 [Java 枚举](https://www.geeksforgeeks.org/enum-in-java/)不同，Kotlin 枚举是**类**。

**关于*列举*科特林–**类的一些要点

*   枚举常量不仅仅是常量的集合——它们有属性、方法等
*   每个枚举常数都充当类的独立实例，并用逗号分隔。
*   枚举通过为常量分配预定义的名称来增加代码的可读性。
*   无法使用构造函数创建枚举类的实例。

枚举是通过在[类](https://www.geeksforgeeks.org/kotlin-class-and-objects/)前面使用**枚举**关键字来定义的，如下所示:-

```
enum class DAYS{
  SUNDAY,
  MONDAY,
  TUESDAY,
  WEDNESDAY,
  THURSDAY,
  FRIDAY,
  SATURDAY
}

```

### 正在初始化枚举–

在 Kotlin 中，枚举也可以像 Java 枚举一样有一个构造函数。由于枚举常量是枚举类的实例，常量可以通过将特定值传递给主[构造函数](https://www.geeksforgeeks.org/kotlin-constructor/)来初始化。

下面是一个为卡片指定颜色的示例–

```
enum class Cards(val color: String) {
    Diamond("black"),
    Heart("red"),
}

```

我们可以使用–

```
val color = Cards.Diamond.color
```

### 枚举属性和方法–

正如在 Java 和其他编程语言中一样，Kotlin 枚举类有一些内置的属性和函数，程序员可以使用。这里看一下主要的属性和方法。

**属性–**

1.  **序数:**该属性存储常量的序数值，通常是从零开始的索引。
2.  **名称:**该属性存储常量的名称。

**方法–**

1.  **值**:该方法返回枚举类中定义的所有常量的列表。
2.  **valueOf** :该方法返回枚举中定义的枚举常量，与输入字符串匹配。如果枚举中不存在常量，则会引发 IllegalArgumentException。

**在 Kotlin 中演示枚举类的示例–**

```
enum class DAYS {
    SUNDAY,
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY
}
fun main()
{
    // A simple demonstration of properties and methods
    for (day in DAYS.values()) {
        println("${day.ordinal} = ${day.name}")
    }
    println("${DAYS.valueOf(" WEDNESDAY ")}")
}
```

**输出:**

```
0 = SUNDAY
1 = MONDAY
2 = TUESDAY
3 = WEDNESDAY
4 = THURSDAY
5 = FRIDAY
6 = SATURDAY
WEDNESDAY

```

### 枚举类属性和函数–

因为枚举类在 Kotlin 中定义了一个新的类型。此类类型可以有自己的属性和函数。属性可以给**一个默认值**，但是，如果没有提供，那么每个常量应该为属性定义自己的值。在函数的情况下，它们通常在伴随对象中定义，因此它们不依赖于类的特定实例。然而，它们也可以在没有伴随对象的情况下定义。

**演示科特林中属性和功能的示例**

```
// A property with default value provided
enum class DAYS(val isWeekend: Boolean = false){
    SUNDAY(true),
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    // Default value overridden
    SATURDAY(true);

    companion object{
        fun today(obj: DAYS): Boolean {
            return obj.name.compareTo("SATURDAY") == 0 || obj.name.compareTo("SUNDAY") == 0
        }
    }
}

fun main(){
    // A simple demonstration of properties and methods
    for(day in DAYS.values()) {
        println("${day.ordinal} = ${day.name} and is weekend ${day.isWeekend}")
    }
    val today = DAYS.MONDAY;
    println("Is today a weekend ${DAYS.today(today)}")
}
```

**输出:**

```
0 = SUNDAY and is weekend true
1 = MONDAY and is weekend false
2 = TUESDAY and is weekend false
3 = WEDNESDAY and is weekend false
4 = THURSDAY and is weekend false
5 = FRIDAY and is weekend false
6 = SATURDAY and is weekend true
Is today a weekend false

```

### 作为匿名类的枚举–

枚举常量还通过实现它们自己的函数以及重写类的抽象函数，表现为匿名类。最重要的是每个枚举常量都必须被覆盖。

```
// defining enum class
enum class Seasons(var weather: String) {
    Summer("hot"){
        // compile time error if not override the function foo()
        override fun foo() {              
            println("Hot days of a year")
        }
    },
    Winter("cold"){
        override fun foo() {
            println("Cold days of a year")
        }
    },
    Rainy("moderate"){
        override fun foo() {
            println("Rainy days of a year")
        }
    };
    abstract fun foo()
}
// main function
fun main(args: Array<String>) {
    // calling foo() function override be Summer constant
    Seasons.Summer.foo() 
}
```

**输出:**

```
Hot days of a year
```

### 当表达式带有枚举类时*的用法–*

当枚举类与表达式中的[相结合时，Kotlin 中枚举类的一个很大的优势就发挥出来了。优点是因为枚举类限制了一个类型可以取的值，所以当与 when 表达式一起使用并且提供了所有常量的定义时，就完全不需要 **else 子句了**。事实上，这样做会从编译器中生成一个警告。](https://www.geeksforgeeks.org/kotlin-when-expression/)

```
enum class DAYS{
    SUNDAY,
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY;
}

fun main(){
    when(DAYS.SUNDAY){
        DAYS.SUNDAY -> println("Today is Sunday")
        DAYS.MONDAY -> println("Today is Monday")
        DAYS.TUESDAY -> println("Today is Tuesday")
        DAYS.WEDNESDAY -> println("Today is Wednesday")
        DAYS.THURSDAY -> println("Today is Thursday")
        DAYS.FRIDAY -> println("Today is Friday")
        DAYS.SATURDAY -> println("Today is Saturday")
        // Adding an else clause will generate a warning
    }
}
```

**输出:**

```
Today is Sunday

```