# 如何在安卓系统中编程检测屏幕触摸事件？

> 原文:[https://www . geesforgeks . org/如何在安卓系统中以编程方式检测屏幕触摸事件/](https://www.geeksforgeeks.org/how-to-detect-touch-event-on-screen-programmatically-in-android/)

检测到触摸确认屏幕功能正常。响应触摸是开发人员要处理的事情。由于安卓设备有一个基于触摸的输入，事情是通过触摸的应用来编程的。为了在应用程序中显式调用方法，必须识别触摸动作。这样的方法可以有特殊的功能。使用此类特殊功能的常见应用有:

1.  **游戏:**大多数游戏都带有触摸监听器，可以在不同的触摸应用上调用不同的功能。
2.  **锁屏:**锁屏一般是基于触摸移动的，一次轻击并不能解锁设备。相反，用户必须做出图案或刷卡来解锁设备。例如:基于模式的锁，刷卡锁。

注意，我们将使用 **Kotlin** 语言来实现这个项目。

### 检测屏幕上的触摸

要检查安卓系统屏幕上是否有触摸动作，我们将按照以下步骤操作:

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。没有对 **activity_main.xml** 文件进行更改。

**步骤 2:使用 MainActivity.kt 文件**

最后转到 **MainActivity.kt** 文件，参考下面的代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.os.Bundle
import android.view.MotionEvent
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.MotionEventCompat

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        // Do Nothing
    }

    // create an override function onTouchEvent that takes
    // in the MotionEvent and returns a boolean value
    override fun onTouchEvent(event: MotionEvent): Boolean {
        return when (MotionEventCompat.getActionMasked(event)) {

            // Display a Toast whenever a movement is captured on the screen
            MotionEvent.ACTION_MOVE -> {
                Toast.makeText(applicationContext, "Action was MOVE", Toast.LENGTH_SHORT).show()
                true
            }
            else -> super.onTouchEvent(event)
        }
    }
}
```

### 输出:在物理设备上运行

<video class="wp-video-shortcode" id="video-497173-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20200928203119/Move-online-video-cutter.com-1.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20200928203119/Move-online-video-cutter.com-1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20200928203119/Move-online-video-cutter.com-1.mp4)</video>

### 在子类视图中检测触摸

要检查在安卓屏幕上显示的特定视图中是否有触摸移动，我们将遵循以下步骤:

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

转到代表应用程序 UI 的 **activity_main.xml** 文件，创建一个 [LinearLayout](https://www.geeksforgeeks.org/android-linearlayout-in-kotlin/) ，给它一个深色背景，没有其他元素，这样我们就可以看到触摸的观感。下面是**activity _ main . XML**文件的代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main_view"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--View (Sub-Class) where OnTouchListener is implemented-->
    <LinearLayout
        android:id="@+id/view1"
        android:layout_width="300sp"
        android:layout_height="400sp"
        android:layout_centerInParent="true"
        android:background="@color/colorPrimaryDark"
        android:orientation="horizontal">
    </LinearLayout>

</RelativeLayout>
```

**第三步:使用 MainActivity.kt 文件**

最后转到 **MainActivity.kt** 文件，参考下面的代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.annotation.SuppressLint
import android.os.Bundle
import android.view.MotionEvent
import android.view.View
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.MotionEventCompat

class MainActivity : AppCompatActivity() {
    @SuppressLint("ClickableViewAccessibility")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // View (Sub-Class) where onTouchEvent is implemented
        val v1 = findViewById<View>(R.id.view1)

        // OnTouchListener on the selected view
        v1.setOnTouchListener { v, event ->

            return@setOnTouchListener when (MotionEventCompat.getActionMasked(event)) {
                MotionEvent.ACTION_DOWN -> {

                    // Make a Toast when movements captured on the sub-class
                    Toast.makeText(applicationContext, "Move", Toast.LENGTH_SHORT).show()
                    true
                }
                else -> false
            }
        }
    }
}
```

### 输出:在物理设备上运行

<video class="wp-video-shortcode" id="video-497173-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20200928222108/Subclass-online-video-cutter.com-1.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20200928222108/Subclass-online-video-cutter.com-1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20200928222108/Subclass-online-video-cutter.com-1.mp4)</video>

### 检测多个视图上的触摸

要检查安卓屏幕上显示的多个视图中是否有触摸移动，我们将遵循以下步骤:

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

转到代表应用程序 UI 的 **activity_main.xml** 文件，创建一个 [LinearLayout](https://www.geeksforgeeks.org/android-linearlayout-in-kotlin/) ，给它一个深色背景，没有其他元素，这样我们就可以看到触摸的观感。下面是**activity _ main . XML**文件的代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main_view"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--View (Sub-Class) where OnTouchListener is implemented-->
    <LinearLayout
        android:id="@+id/view1"
        android:layout_width="300sp"
        android:layout_height="400sp"
        android:layout_centerInParent="true"
        android:background="@color/colorPrimaryDark"
        android:orientation="horizontal">
    </LinearLayout>

</RelativeLayout>
```

**第三步:使用 MainActivity.kt 文件**

最后转到 **MainActivity.kt** 文件，参考下面的代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.annotation.SuppressLint
import android.os.Bundle
import android.view.MotionEvent
import android.view.View
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.MotionEventCompat

class MainActivity : AppCompatActivity() {
    @SuppressLint("ClickableViewAccessibility")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // mainView is nothing but the parent activity_main layout
        // subView is a explicitly declared Linear 
        // Layout and occupies a minor part of the screen
        val mainView = findViewById<View>(R.id.main_view)
        val subView = findViewById<View>(R.id.view1)

        // OnTouchListener on the Screen
        mainView.setOnTouchListener { v, event ->
            return@setOnTouchListener when (MotionEventCompat.getActionMasked
                (event)) {
                MotionEvent.ACTION_DOWN -> {
                    if (isInside(subView, event)) {
                        Toast.makeText(applicationContext, "Inside", Toast.LENGTH_SHORT).show()
                    }
                    if (!isInside(subView, event)) {
                        Toast.makeText(applicationContext, "Outside", Toast.LENGTH_SHORT).show()
                    }
                    true
                }
                else -> false
            }
        }
    }

    // V shall be the subclass i.e. the subView declared in onCreate function
    // This functions confirms the dimensions of the view (subView in out program)
    private fun isInside(v: View, e: MotionEvent): Boolean {
        return !(e.x < 0 || e.y < 0 || e.x > v.measuredWidth ||
                e.y > v.measuredHeight)
    }
}
```

### 输出:在物理设备上运行

<video class="wp-video-shortcode" id="video-497173-3" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20200928222625/outside-the-class-online-video-cutter.com-1.mp4?_=3">[https://media.geeksforgeeks.org/wp-content/uploads/20200928222625/outside-the-class-online-video-cutter.com-1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20200928222625/outside-the-class-online-video-cutter.com-1.mp4)</video>