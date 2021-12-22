# 安卓动态复选框示例

> 原文:[https://www . geesforgeks . org/dynamic-checkbox-in-Android-with-examples/](https://www.geeksforgeeks.org/dynamic-checkbox-in-android-with-examples/)

安卓为用户交互提供了各种各样的小部件，CheckBox 就是其中之一。[**复选框**](https://www.geeksforgeeks.org/checkbox-in-kotlin/)**是一种特殊的按钮，有两种状态，可以选中也可以不选中。它们作为一个简单的工具从用户那里收集信息，没有太多的麻烦。它们通常用于在任务管理应用程序中将事情标记为由用户完成。**

**![](img/caca6ab2a8fe60f844e54051c28a1abb.png)**

**可能会出现这样的情况:我们可能不知道要在构建时显示的小部件的所有属性，并且可能必须动态分配这些值。谢天谢地，安卓支持在运行时创建小部件。让我们看看如何在 Kotlin 中动态创建 CheckBox，而不是在[构建时](https://www.geeksforgeeks.org/checkbox-in-kotlin/)创建 CheckBox。**

#### **方法**

****第一步:创建新项目****

**要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目。](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)**

****第二步:修改 activity_main.xml****

**在动态添加复选框之前，需要预先定义一个布局来容纳复选框。为了使应用程序保持简单，请为演示应用程序选择覆盖整个屏幕的线性布局。**

## **可扩展标记语言**

```kt
<?xml version="1.0" encoding="utf-8"?>

<!--This LinearLayout will serve as the root 
    container to hold the checkbox
    It will fully occupy the device screen and
    will place the checkbox at its center-->
<LinearLayout
    android:id="@+id/root_layout"
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center">

</LinearLayout>
```

****第 3 步:将字符串添加到 strings.xml****

**最好不要使用硬编码字符串，让我们在应用程序中也这样做。**

## **可扩展标记语言**

```kt
<resources>
   <string name="app_name">GFG | Dynamic Checkbox Demo</string>
   <string name="geek_message">TODO: Become A Geek</string>
</resources>
```

**该字符串可以在 MainActivity.kt 文件中使用以下命令引用:**

```kt
getString(R.string.geek_message) 
```

****第 4 步:使用 MainActivity.kt 文件****

**从 MainActivity.kt 文件中引用布局。这可以使用下面一行代码来完成:**

> **val layout = findViewById <linearlayout>（R.id.root_layout）</linearlayout>**

**现在在 MainActivity.kt 文件中创建新的 CheckBox，并设置其布局参数。布局参数是必需的，因为它们描述了 CheckBox 将如何与布局交互。**

> **val geekBox = CheckBox(此处)
> geek box . layout parameters = linear layout . layout parameters(linear layout . layout parameters . wrap _ content，view group . layout params . wrap _ content)的值**

**设置一个监听器，在用户切换复选框时显示[吐司](https://www.geeksforgeeks.org/android-toast-in-kotlin/)信息。最后，使用下面一行代码将创建的 CheckBox 添加到布局中。**

> **layout.addView(geekBox)**

## **我的锅**

```kt
package org.geeksforgeeks.dynamic_checkbox

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.ViewGroup
import android.widget.CheckBox
import android.widget.LinearLayout
import android.widget.Toast

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // References the root LinearLayout from 
        // the activity_main layout file
        val layout = findViewById<LinearLayout>(R.id.root_layout)

        // Create a new Checkbox at run-time
        val geekBox = CheckBox(this)

        // Define the layout properties and text for our check box
        geekBox.layoutParams = LinearLayout.LayoutParams(
          LinearLayout.LayoutParams.WRAP_CONTENT, 
          ViewGroup.LayoutParams.WRAP_CONTENT)
        geekBox.text = getString(R.string.geek_message)

        // Set-up a listener to show a Toast message when 
        // the check box is toggled.
        geekBox.setOnCheckedChangeListener{
          _, isChecked ->  Toast.makeText(this, 
                                          if (isChecked) "Congratulations!" + 
                                                          "You Are A Geek Now" 
                                          else "Don't Give Up", 
                                          Toast.LENGTH_SHORT).show() }

        // Add our created check box to the root 
        // layout for it to be displayed
        layout.addView(geekBox)
    }   
}
```

#### **输出:**

**<video class="wp-video-shortcode" id="video-468619-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20200813104516/GFG_Dynamic_Checkbox_OP.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20200813104516/GFG_Dynamic_Checkbox_OP.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20200813104516/GFG_Dynamic_Checkbox_OP.mp4)</video>**