# 如何使用 Kotlin 在安卓中添加 RangeSeekbar？

> 原文:[https://www . geesforgeks . org/how-add-range seekbar-in-Android-using-kot Lin/](https://www.geeksforgeeks.org/how-to-add-rangeseekbar-in-android-using-kotlin/)

在本文中，RangeSeekbar 是在 android 的一个应用程序中实现的。安卓 [**Seekbar**](https://www.geeksforgeeks.org/seekbar-in-kotlin/) 是一种进度条。我们可以将 seekbar 从左向右拖动，反之亦然，从而改变当前进度。这里我们使用 RangeSeekbar 库在我们的应用程序中添加自定义 Seekbar。这个库为我们提供了各种各样的功能，比如步骤、模式、缩略图等，这使得它比安卓提供的 seekbar 更好。

### 方法

**步骤 1:** 在你的根[中添加支持库**build.gradle**T5】文件(不是你的模块 build . gradle 文件)。这个库 **jitpack** 是一个新颖的包存储库。它是为 JVM 而做的，这样在](https://www.geeksforgeeks.org/android-build-gradle/) [github](https://www.geeksforgeeks.org/ultimate-guide-git-github/) 和 [bigbucket](https://www.geeksforgeeks.org/bitbucket-vs-github-vs-gitlab/) 中存在的任何库都可以直接在应用程序中使用。

## 可扩展标记语言

```kt

allprojects {         
   repositories {         
      maven { url 'https://jitpack.io' }         
  }
}         
```

**第二步:**在 [**build.gradle**](https://www.geeksforgeeks.org/android-build-gradle/) 文件中添加支持库，并在依赖项部分添加依赖项。通过这个直接的范围，Seekbar 将被用在 XML 中。

## 可扩展标记语言

```kt

dependencies {         
         implementation 'com.github.Jay-Goo:RangeSeekBar:v3.0.0'         
}
```

**步骤 3:** 在**字符串. xml** 文件中创建一个字符串数组，该文件位于值文件夹中。

## strings.xml

```kt

<string-array name="levelArray">
        <item>Lv1</item>
        <item>Lv2</item>
        <item>Lv3</item>
        <item>Lv4</item>
        <item>Lv5</item>
    </string-array>
```

**第 4 步:**在 **activity_main.xml** 文件中添加以下代码。在这个文件中，seekbar 被添加到布局中，并且根据需要添加了重要的标签，如 steps、thumbDrawable、mode 等。

## activity_main.xml

```kt

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

 <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="228dp"
        android:textSize="18sp"
        android:text="Set difficulty for problem:-"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <com.jaygoo.widget.RangeSeekBar
        android:id="@+id/range_seekbar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:rsb_gravity="bottom"
        app:rsb_indicator_background_color="@color/colorProgress"
        app:rsb_indicator_height="30dp"
        app:rsb_indicator_width="50dp"
        app:rsb_mode="single"
        app:rsb_progress_color="@color/colorProgress"
        app:rsb_step_auto_bonding="true"
        app:rsb_step_color="@color/colorProgress"
        app:rsb_step_height="10dp"
        app:rsb_step_width="5dp"
        app:rsb_steps="4"
        app:rsb_thumb_drawable="@drawable/ic_baseline_brightness"
        app:rsb_tick_mark_layout_gravity="bottom"
        app:rsb_tick_mark_mode="other"
        app:rsb_tick_mark_text_array="@array/levelArray"
        app:rsb_tick_mark_text_margin="20dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**第五步:**在 **MainActivity.kt** 文件中添加以下代码。在这里**设置了一个带有 seekbar 的 changechangedlistener**。当用户更改 seekbar 栏时调用它，并显示更改进度的百分比。

## MainActivity.kt 公司

```kt
package org.geeksforgeeks.rangeseekbar

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Toast
import com.jaygoo.widget.OnRangeChangedListener
import com.jaygoo.widget.RangeSeekBar
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        //whenever we change progress of seekbar this function 
        //get invoked automatically.
        range_seekbar?.setOnRangeChangedListener(object : 
            OnRangeChangedListener {
            override fun onRangeChanged(
                     rangeSeekBar: RangeSeekBar, leftValue: Float,
                     rightValue: Float, isFromUser: Boolean) {
                Toast.makeText(this@MainActivity,
                    leftValue.toString(),Toast.LENGTH_LONG).show()
            }

            override fun onStartTrackingTouch(view: RangeSeekBar?,
                         isLeft: Boolean) {
            }

            override fun onStopTrackingTouch(view: RangeSeekBar?, 
                         isLeft: Boolean) {
            }
        })
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-451562-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20200713231823/2020_07_09_22_00_22_trim1.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20200713231823/2020_07_09_22_00_22_trim1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20200713231823/2020_07_09_22_00_22_trim1.mp4)</video>

*更多信息请参考* [*官方文档*](https://github.com/Jay-Goo/RangeSeekBar) *。*