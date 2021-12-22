# 在安卓系统中输入事件，示例

> 原文:[https://www . geesforgeks . org/input-events-in-Android-with-example/](https://www.geeksforgeeks.org/input-events-in-android-with-example/)

在安卓系统中，有相当多的方法可以从用户与应用程序的交互中截取事件。当考虑界面内的事件时，方法是从用户交互的精确视图对象中捕获事件。视图类提供了尝试这样做的方法。在您将要用来组成布局的各种视图类中，您会注意到几个公共回调方法，它们看起来对用户界面事件很有用。当相应的动作在对象上发生时，这些方法被**安卓框架**调用。例如，当触摸视图(如按钮)时， **onTouchEvent()** 方法在其上被命名为对象。但是，要拦截这种情况，必须扩展类并重写方法。然而，扩展每个视图对象来处理这样的事件是不切实际的。这就是为什么视图类还包含一组带有回调的嵌套接口，您可以更容易地定义它们。这些被称为**事件监听器**的界面是你捕捉用户交互和你的用户界面的门票。

**例如**，如果一个按钮要回复点击事件，它必须注册才能查看。onClickListener 事件侦听器并实现相应的 onClick()回调方法。在应用程序中，当检测到按钮点击事件时，安卓框架将调用该特定视图的 on click()方法。

### 安卓事件监听器

**事件侦听器**是视图类中包含一个回调方法的接口。当用户与用户界面中的项目交互触发向侦听器注册的视图时，安卓框架将调用这些方法。事件侦听器接口中包括以下回调方法:

<figure class="table">

| 

方法

 | 

事件侦听器

 | 

描述

 |
| --- | --- | --- |
| **onClick()** | 视图(View)。onclick 侦听器 | 当用户用导航键或轨迹球触摸项目或聚焦在项目上并按下合适的“回车”键或按下轨迹球时，调用该方法。 |
| **onLongClick()** | 视图(View)。onload 单击列表 | 当用户触摸并按住该项目，或者用导航键或轨迹球聚焦在该项目上，并按下并按住适当的“回车”键，或者按下并按住轨迹球(一秒钟)时，就调用这个函数。

 |
| **就职()** | 查看。OnFocusChangeListener | 当用户使用导航键或轨迹球导航到项目上或离开项目时，就会调用这个函数。 |
| **大叔()** | 视图(View)。叔叔列表 | 当用户将注意力集中在项目上并按下或释放设备上的硬件键时，就会调用此方法。 |
| **本体()** | 查看。OnTouchListener | 当用户行为符合触摸事件时，包括按下、释放或屏幕上的任何移动手势(在项目的边界内)，就会调用此方法。 |
| **onCreateContextMenu()**

 | 视图(View)。oncreatecontext menu listener-建立相关内容功能表监听器 | 当上下文菜单正在构建时(由于持续的“长时间点击”)，这被调用。 |

</figure>

> **注:**
> 
> **onClick()回调不返回任何值**。但是 **onLongClick()** 、 **onKey()、** **onTouch()回调返回一个布尔值**，表示您只是消费了事件，不应该再继续下去；也就是说，返回 true 表示您已经处理了该事件，它应该在这里停止；如果您没有处理它和/或事件应该继续到任何其他点击监听器，返回 false。

### 安卓事件监听器注册

**事件注册**是事件处理程序向事件侦听器注册的过程，以便在事件侦听器触发事件时调用该处理程序。这个例子说明了如何注册一个按钮的点击监听器

## 我的锅

```kt
protected void onCreate(savedValues: Bundle) {
    ...
    val button: Button = findViewById(R.id.button)
    // Register the onClick listener 
    button.setOnClickListener { view ->
        // do something when the button is clicked
    }
    ...
}
```

### 安卓事件处理程序

当我们从视图构建定制组件时，事件处理程序对于定义几种回调方法非常有用。以下是安卓应用程序中一些常用的事件处理回调方法。

<figure class="table">

| 

方法

 | 

描述

 |
| --- | --- |
| **叔叔家()** | 当新的键事件发生时，调用此方法。 |
| **onKeyUp（）** | 当按键事件发生时，会呼叫这个方法。 |
| **反包风()** | 当轨迹球运动事件发生时，调用此方法。 |
| **本体容器()** | 当触摸屏运动事件发生时，调用此方法。 |
| **onFocusChanged()** | 当视图获得或失去焦点时，调用此方法。 |

</figure>

我们已经了解了事件侦听器、事件处理程序及其回调方法。现在我们将在我们的 android 应用程序中看到它们的实现。

### 安卓输入事件示例

让我们看看在安卓中实现**输入事件** **的方法。注意，我们将使用**柯特林**语言来实现这个项目。**

**第一步:在安卓工作室创建新项目**

要在安卓工作室创建新项目，请参考[如何在科特林的安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/how-to-create-project-in-android-studio-using-kotlin/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 XML 文件**

为了设计用户界面，代码以 XML 的形式出现在 **res\layout 文件夹**下。它们在活动文件中使用，一旦 XML 文件在活动范围内，就可以访问 XML 中的组件。下面是 **activity_main.xml 文件**的代码。代码中添加了注释，以更详细地理解代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <!-- This is the layout for the
         Button which user will click  -->
    <Button
        android:id="@+id/btnClick"
        android:layout_width="200dp"
        android:layout_height="70dp"
        android:layout_gravity="center"
        android:layout_marginTop="200dp"
        android:text="CLICK ME!"
        android:textSize="18sp"
        android:textStyle="bold" />

    <!-- This is the layout for the textView, On Click
         of Button the text will appear on the screen  -->
    <TextView
        android:id="@+id/textResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:layout_marginTop="50dp"
        android:textColor="#86AD33"
        android:textSize="25sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="@id/btnClick" />

</LinearLayout>
```

**步骤 3:使用主要活动文件**

下面是 **MainActivity.kt 文件**的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.os.Bundle
import android.view.View
import android.widget.Button
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Register OnClickListener for button
        // call Click Handler method
        findViewById<Button>(R.id.btnClick).setOnClickListener {
            displayTextOnButtonClick(it)
        }

        // Register OnLongClickListener for button
        // call Click Handler method
        // Return true to indicate that the event is consumed
        findViewById<Button>(R.id.btnClick).setOnLongClickListener {
            displayTextOnLongButtonClick(it)
            true
        }
    }

    // Click handler for the Click me button.
    // Display the text below Click me Button
    // Display text after Button click
    // It has No Return Value
    private fun displayTextOnButtonClick(view: View) {
        val text = findViewById<TextView>(R.id.textResult)
        text.text = "Button Clicked !"
    }

    // Click handler for the Click me button.
    // Display the text below Click me Button
    // Display text after Button click for a bit long time (1-2sec)
    private fun displayTextOnLongButtonClick(view: View) {
        val text = findViewById<TextView>(R.id.textResult)
        text.text = "Long Button Clicked !"
    }
}
```

### 输出:

<video class="wp-video-shortcode" id="video-529957-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201215234908/Input-Event-Video.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201215234908/Input-Event-Video.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201215234908/Input-Event-Video.mp4)</video>

### 结论

安卓通过事件监听器和回调方法的概念，弥合了用户界面和应用程序后端代码之间的鸿沟。安卓视图类定义了一组事件监听器，可以在视图对象上注册。每个事件侦听器还关联了一个回调方法。当一个事件发生在用户界面的视图上时，该事件被放入事件队列，并由安卓运行时以先进先出的方式进行处理。如果发生事件的视图注册了与事件类型匹配的侦听器，则调用相应的回调方法。然后，该代码在返回之前执行活动所需的任何任务。需要一些回调方法来返回一个布尔值，以指出事件是被使用还是需要传递给在视图上注册的任何其他事件侦听器。