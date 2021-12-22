# Android 中的滚动视图

> 原文:[https://www.geeksforgeeks.org/scrollview-in-android/](https://www.geeksforgeeks.org/scrollview-in-android/)

在[安卓](https://www.geeksforgeeks.org/introduction-to-android-development/)中，ScrollView 是一个视图组，用于制作可垂直滚动的视图。滚动视图只包含一个直接子视图。为了在滚动视图中放置多个视图，需要将一个视图组(如[线性布局](https://www.geeksforgeeks.org/android-linearlayout-in-kotlin/))作为直接子视图，然后我们可以在其中定义多个视图。滚动视图仅支持垂直滚动，因此为了创建水平滚动视图，使用了[水平滚动视图](https://www.geeksforgeeks.org/horizontalscrollview-in-kotlin/)。

#### 滚动视图的 XML 属性

<figure class="table">

| 

属性

 | 

描述

 |
| --- | --- |
| android:fillViewport(填充视口) | 定义 scrollview 是否应拉伸其内容以填充视口。 |

</figure>

**继承属性**:

**从框架布局**

<figure class="table">

| 

属性

 | 

描述

 |
| --- | --- |
| 安卓:测量儿童 | 确定在测量时是测量所有子级还是只测量那些处于可见或不可见状态的子级。默认为 false。 |

</figure>

**从视图**

<figure class="table">

| 

属性

 | 

描述

 |
| --- | --- |
| 安卓:阿尔法 | 视图的 alpha 属性，值介于 0(完全透明)和 1(完全不透明)之间。 |
| 安卓:背景 | 用作背景的图画。 |
| 安卓:可点击 | 定义此视图是否对单击事件做出反应。 |
| android:contentDescription | 定义简要描述视图内容的文本。 |
| android:id | 为此视图提供一个标识符名称，以便以后使用 View.findViewById()或 Activity.findViewById()检索它。 |
| Android:isscrollcontent | 如果视图将用作滚动容器，则设置此选项，这意味着可以调整视图的大小以缩小整个窗口，从而为输入法留出空间。 |
| android:minHeight | 定义视图的最小高度。 |
| 安卓:minWidth | 定义视图的最小宽度。 |
| android:onClick | 单击视图时要在该视图的上下文中调用的方法的名称。 |
| 安卓:填充 | 以像素为单位设置所有四条边的填充。 |
| android:卷轴列 | 定义滚动时应显示或不显示哪些滚动条。 |

</figure>

**来自视图组**

<figure class="table">

| 

属性

 | 

描述

 |
| --- | --- |
| Android:addstatfromchildren | 设置该视图组的可绘制状态是否也包括其子视图组的可绘制状态。 |
| android:动画布局更改 | 定义布局中的更改是否应导致布局转换运行。 |
| android:剪辑子项 | 定义子对象是否被限制在其边界内绘制。 |
| android:剪辑加载 | 定义如果填充不为零，视图组是否将剪切其子视图并将任何边缘效果调整到其填充。 |
| android:布局动画 | 定义第一次布局视图组时要使用的布局动画。 |
| android:布局模式 | 定义此视图组的布局模式。 |
| android:拆分运动事件 | 设置在触摸事件分派期间，此视图组是否应该拆分运动事件以分离子视图。 |

</figure>

### 方法

这个例子演示了使用 Kotlin 在安卓系统中创建一个 ScrollView 的步骤。

**第一步:创建新项目**

1.  单击文件，然后单击新建= >新建项目。
2.  为项目模板选择“空活动”。
3.  选择语言作为 Kotlin。
4.  根据您的需要选择最小的软件开发工具包。

**第二步:修改字符串. xml**

在 **strings.xml** 文件中添加一些字符串，在应用程序中显示这些字符串。

<gfg-tab role="tab" slot="tab" id="gfg-tab-0">strings.xml </gfg-tab> <gfg-panel role="tabpanel" slot="panel" id="gfg-panel-0" data-code-lang="xml">```
<resources>
    <string name="app_name">gfgapp_scrollview</string>
    <string name="scrolltext">Kotlin is a statically typed,
                 general-purpose programming language developed
                 by JetBrains, that has built world-class IDEs 
                 like IntelliJ IDEA, PhpStorm, Appcode, etc.
                 It was first introduced by JetBrains in 2011 
                 and a new language for the JVM. Kotlin is 
                 object-oriented language, and a “better language” 
                 than Java, but still be fully interoperable
                 with Java code. Kotlin is sponsored by Google, 
                 announced as one of the official languages for 
                 Android Development in 2017\. 
                 Advantages of Kotlin language:
                 Easy to learn – Basic is almost similar to java.
                 If anybody worked in java then easily understand
                 in no time. Kotlin is multi-platform – Kotlin is
                 supported by all IDEs of java so you can write 
                 your program and execute them on any machine
                 which supports JVM. It’s much safer than Java.
                 It allows using the Java frameworks and libraries 
                 in your new Kotlin projects by using advanced 
                 frameworks without any need to change the whole
                 project in Java. Kotlin programming language, 
                 including the compiler, libraries and all the
                 tooling is completely free and open source and
                 available on github. Here is the link for 
                 Github https://github.com/JetBrains/kotlin 
                 Applications of Kotlin language:
                 You can use Kotlin to build Android Application. 
                 Kotlin can also compile to JavaScript, and making
                 it available for the frontend. It is also designed 
                 to work well for web development and server-side 
                 development.Kotlin is a statically typed, general-purpose
                 programming language developed by JetBrains that 
                 has built world-class IDEs like IntelliJ IDEA, 
                 PhpStorm, Appcode, etc. It was first introduced
                 by JetBrains in 2011.Kotlin is object-oriented 
                 language and a better language than Java, but still
                 be fully interoperable with Java code. A constructor
                 is a special member function that is invoked when 
                 an object of the class is created primarily to initialize
                 variables or properties. A class needs to have a constructor
                 and if we do not declare a constructor, then the compiler
                 generates a default constructor.
                 Kotlin has two types of constructors –
                 Primary Constructor
                 Secondary Constructor
                 A class in Kotlin can have at most one primary
                 constructor, and one or more secondary constructors. 
                 The primary constructor
                 initializes the class, while the secondary 
                 constructor is used
                 to initialize the class and introduce some extra logic.
                 Explanation:
                 When we create the object add for the class then 
                 the values 5 and 6
                 passes to the constructor. The constructor 
                 parameters a and b 
                 initialize with the parameters 5 and 6 respectively.
                 The local variable c contains the sum of variables. 
                 In the main, we access the property of 
                 constructor using ${add.c}.
                 Explanation:
                 Here, we have initialized the constructor 
                 parameters with some
                 default values emp_id = 100 and emp_name = “abc”.
                 When the object emp is created we passed the values for
                 both the parameters so it prints those values.
                 But, at the time of object emp2 creation, 
                 we have not passed
                 the emp_name so initializer block uses 
                 the default values and
                 print to the standard output.</string>
</resources>
```</gfg-panel>