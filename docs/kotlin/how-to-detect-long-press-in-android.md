# 安卓系统如何检测长按？

> 原文:[https://www . geeksforgeeks . org/如何检测长按式安卓/](https://www.geeksforgeeks.org/how-to-detect-long-press-in-android/)

长按是指按下触摸屏上的物理按钮或点击虚拟按钮，并按住一两秒钟。长按或长按用于触摸屏、智能手机、平板电脑和智能手表，增加了用户界面的灵活性。典型的“短按”或“短按”执行一个操作，而短时间按住同一个按钮会激活另一个操作。长按可以让你获取一些信息，从网上下载照片，编辑图片等等。

### **我们在哪里可以使用这个功能？**

如上所述，长压机可用于许多应用，其中一些列举如下:

1.  获取信息
2.  下载照片
3.  编辑图片
4.  文本视图上的复制、剪切、粘贴操作

通过这篇文章，我们想扩展我们关于长按一个 [**按钮**](https://www.geeksforgeeks.org/button-in-kotlin/) **以及在安卓系统中查看一个** [**文本视图**](https://www.geeksforgeeks.org/textview-in-kotlin/) **的知识。我们已经实现了一种方法，该方法将检测特定持续时间内的长按，如果满足标准，将生成[吐司](https://www.geeksforgeeks.org/android-what-is-toast-and-how-to-use-it-with-examples/)。注意，我们要用 **Kotlin** 语言来实现这个项目。**

### 长按按钮

要检测安卓系统中长时间按下按钮的情况，请执行以下步骤:

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

转到代表应用程序用户界面的 **activity_main.xml** 文件，并创建一个长按会生成吐司的按钮。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--This button has to be long-clicked-->
    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="hold" />

</RelativeLayout>
```

**第 4 步:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.os.Bundle
import android.widget.Button
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declare a button
        val mBtn = findViewById<Button>(R.id.btn)

        // implement a setOnLongClickListener to the 
          // button that creates a Toast and
        // returns true when actually long-pressed
        mBtn.setOnLongClickListener {
            Toast.makeText(applicationContext, "Button Long Pressed", Toast.LENGTH_SHORT).show()
            true
        }
    }
}
```

### **输出:在仿真器上运行**

<video class="wp-video-shortcode" id="video-497175-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001104133/Screen-Recording-2020-09-23-at-14.12.56.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201001104133/Screen-Recording-2020-09-23-at-14.12.56.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001104133/Screen-Recording-2020-09-23-at-14.12.56.mp4)</video>

### 长按视图

要检测安卓系统屏幕上的长按，请执行以下步骤:

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。与 **活动 _main.xml** 文件无关。所以保持文件原样。(假设默认情况下每个新项目都会在布局中创建一个文本视图)

**步骤 2:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.os.Bundle
import android.view.GestureDetector
import android.view.GestureDetector.SimpleOnGestureListener
import android.view.MotionEvent
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        // Do Nothing
    }

    // GestureDetecctor to detect long press
    private val gestureDetector = GestureDetector(object : SimpleOnGestureListener() {
        override fun onLongPress(e: MotionEvent) {

            // Toast to notify the Long Press
            Toast.makeText(applicationContext, "Long Press Detected", Toast.LENGTH_SHORT).show()
        }
    })

    // onTouchEvent to confirm presence of Touch due to Long Press
    override fun onTouchEvent(event: MotionEvent?): Boolean {
        return gestureDetector.onTouchEvent(event)
    }
}
```

### **输出:在仿真器上运行**

<video class="wp-video-shortcode" id="video-497175-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001104019/Screen-Recording-2020-09-23-at-14.00.47.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20201001104019/Screen-Recording-2020-09-23-at-14.00.47.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001104019/Screen-Recording-2020-09-23-at-14.00.47.mp4)</video>