# 双击安卓系统中的视图

> 原文:[https://www . geesforgeks . org/在安卓中双击查看/](https://www.geeksforgeeks.org/double-tap-on-a-view-in-android/)

检测双击，即每当用户双击任何视图时，如何检测它，并且根据该视图，可以添加对应于它的响应。这里显示了一个示例，其中检测到视图上的双击，并相应地以烤面包的形式添加响应。

**第一步:**在安卓工作室创建一个空活动。创建一个，遵循这篇文章-[https://www . geeksforgeeks . org/Android-如何创建-启动-一个新的项目-在 android-studio/](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/) 。检查选择的主要语言是否为**科特林。**

**步骤 2:**activity _ main . XML 中没有进行任何更改。因为已经存在一个 textview，所以双击的响应会添加到其中。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tvView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**步骤 3:** 在这一步中，为双击添加抽象类，并设置 onClickListener，它将使用抽象类。下面是 MainActivity.kt 类的代码。

## 我的锅

```kt
package org.geeksforgeeks.viewdoubletap

import android.os.Bundle
import android.view.View
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // In our case, we tap on Text View
        val view = findViewById<TextView>(R.id.tvView)

        // Double Click Listener implemented on the Text View
        view.setOnClickListener(object : DoubleClickListener() {
            override fun onDoubleClick(v: View?) {
                Toast.makeText(applicationContext,"Double Click",Toast.LENGTH_SHORT).show()
            }
        })

    }

    // Abstract class defining methods to check Double Click where Time Delay 
    // between the two clicks is set to 300 ms
    abstract class DoubleClickListener : View.OnClickListener {
        var lastClickTime: Long = 0
        override fun onClick(v: View?) {
            val clickTime = System.currentTimeMillis()
            if (clickTime - lastClickTime < DOUBLE_CLICK_TIME_DELTA) {
                onDoubleClick(v)
            }
            lastClickTime = clickTime
        }

        abstract fun onDoubleClick(v: View?)

        companion object {
            private const val DOUBLE_CLICK_TIME_DELTA: Long = 300 //milliseconds
        }
    }
}
```

#### 仿真器上的输出:

<video class="wp-video-shortcode" id="video-496607-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20201001115121/Screen-Recording-2020-09-23-at-14.39.09.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20201001115121/Screen-Recording-2020-09-23-at-14.39.09.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20201001115121/Screen-Recording-2020-09-23-at-14.39.09.mp4)</video>