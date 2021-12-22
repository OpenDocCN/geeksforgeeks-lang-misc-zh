# 如何提高/降低安卓中 FadingTextView 的淡入淡出率？

> 原文:[https://www . geeksforgeeks . org/如何在 android 中增加-减少-衰减-fading textview-rate/](https://www.geeksforgeeks.org/how-to-increase-decrease-fading-rate-of-fadingtextview-in-android/)

**先决条件:** [如何在安卓](https://www.geeksforgeeks.org/how-to-add-fading-textview-animation-in-android/)中添加渐变 TextView 动画

[**TextView**](https://www.geeksforgeeks.org/textview-widget-in-android-using-java-with-examples/) 是用户界面组件的基本构建模块。它用于设置文本并将其显示给用户。它是一个非常基本的组件，使用了很多。一个**渐变文本视图**是一个每几秒钟自动改变其内容的文本视图。所以现在的问题是**为什么要提高/降低 FadingTextView** 的衰落率。这完全取决于屏幕上显示的元素。这与应用的美观性有关。带有灰色或黑色文本的较慢淡入淡出的文本视图可用于显示某些消息。类似地，带有红色文本的更快淡入淡出的文本视图可用于显示警告或错误消息。这完全取决于开发者想要展示什么。通过本文，我们实现了一个模型来演示这个功能是如何工作的。人们可以相应地利用这一功能。注意，我们要用 **Kotlin** 语言来实现这个项目。

### 接近

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:向**T2【构建】文件添加依赖关系

设置完成后，转到 app [**build.gradle**](https://www.geeksforgeeks.org/android-build-gradle/) 并添加以下依赖项。立即同步项目。

> 实现' com.tomer:fadingtextview:2.5 '

**步骤 3:使用 activity_main.xml 文件**

接下来，转到 **activity_main.xml** 文件，该文件代表项目的 UI。我们已经添加了一个 FadingTextView 元素来显示渐变文本和一个按钮，因此每当用户点击按钮时，渐变速度就会相应地增加/减少。下面是**activity _ main . XML**文件的代码。代码中添加了注释，以更详细地理解代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--FadingTextView element-->
    <com.tomer.fadingtextview.FadingTextView
    android:id="@+id/fadingTextView"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_centerInParent="true"
    android:gravity="center"
    android:textSize="30sp"
    />

    <!--A button to increase or Decrease fading rate-->  
     <Button
    android:id="@+id/btnStart"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_centerHorizontal="true"
    android:layout_below="@id/fadingTextView"
    android:text="Faster or Slower"/>

</RelativeLayout>
```

**第 4 步:使用 MainActivity.kt 文件**

最后，转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

**用于增加衰落率(更快):**

## 我的锅

```kt
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import com.tomer.fadingtextview.FadingTextView
import java.util.concurrent.TimeUnit

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Strings to display in the FadingTextView
        val texts = arrayOf("Welcome!", "Hello", "Geek")

        // Declaring FadingTextView
        val ftv = findViewById<FadingTextView>(R.id.fadingTextView)

        // Set the text array to FadingTextView (ftv)
        ftv.setTexts(texts)

        var timeout:Long = 1000

        // setTimeout(Long or Double value only, TimeUnit)
        // TimeUnits: HOURS, MINUTES, SECONDS, MILLISECONDS
          // For every 1000 Milliseconds, the text in FTV will change
        ftv.setTimeout(timeout,TimeUnit.MILLISECONDS)

        // btn to increase the change rate or make things faster.
        val btn = findViewById<Button>(R.id.btnStart)

        btn.setOnClickListener{

          // Setting timeout to the half of the current
          timeout /= 2

            ftv.setTimeout(timeout,TimeUnit.MILLISECONDS)

            // Toast that displays current Timeout
            Toast.makeText(applicationContext,"Changes every $timeout Milliseconds", Toast.LENGTH_SHORT).show()
        } 
    }
}
```

### **输出:在仿真器上运行**

<video class="wp-video-shortcode" id="video-496167-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001102748/Fast.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201001102748/Fast.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001102748/Fast.mp4)</video>

**用于降低衰落率(较慢):**

## 我的锅

```kt
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import com.tomer.fadingtextview.FadingTextView
import java.util.concurrent.TimeUnit

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Strings to display in the FadingTextView
        val texts = arrayOf("Welcome!", "Hello", "Geek")

        // Declaring FadingTextView
        val ftv = findViewById<FadingTextView>(R.id.fadingTextView)

        // Set the text array to FadingTextView (ftv)
        ftv.setTexts(texts)

        var timeout:Long = 1

        // setTimeout(Long or Double value only, TimeUnit)
        // TimeUnits: HOURS, MINUTES, SECONDS, MILLISECONDS
          // For every 1 Milliseconds, the text in FTV will change
        ftv.setTimeout(timeout,TimeUnit.MILLISECONDS)

        // btn to decrease the change rate or make things slower.
        val btn = findViewById<Button>(R.id.btnStart)

        btn.setOnClickListener{
         // Setting timeout to twice of the current 
          timeout *= 2

            ftv.setTimeout(timeout,TimeUnit.MILLISECONDS)

            // Toast that displays current Timeout
            Toast.makeText(applicationContext,"Changes every $timeout Milliseconds", Toast.LENGTH_SHORT).show()
        }
    }
}
```

### **输出:在仿真器上运行**

<video class="wp-video-shortcode" id="video-496167-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001102834/Slow.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20201001102834/Slow.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001102834/Slow.mp4)</video>