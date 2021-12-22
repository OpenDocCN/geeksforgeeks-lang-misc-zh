# 如何在安卓中自定义吐司？

> 原文:[https://www . geesforgeks . org/how-customize-toast-in-Android/](https://www.geeksforgeeks.org/how-to-customize-toast-in-android/)

一条 [**吐司**](https://www.geeksforgeeks.org/toasts-android-studio/) 是一条反馈信息。它占用很少的显示空间，并且显示在活动的主要内容之上，并且仅在短时间内保持可见。在本文中，我们将学习如何在 android 中定制 Toast。因此，我们将通过制作一个简单的应用程序来显示吐司来理解这一点。

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择 **Java** 作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/button1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Show Toast"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**第三步:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 MainActivity.kt 文件的代码。代码中添加了注释，以更详细地理解代码。这里我们将绑定视图并编写应用程序的逻辑。

## 我的锅

```kt
import android.graphics.Color
import android.os.Bundle
import android.view.Gravity
import android.view.ViewGroup
import android.widget.Button
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    lateinit var btn: Button

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        btn = findViewById(R.id.button1)
        val text = "GeeksForGeeks"

        btn.setOnClickListener {
            showToast(text)
        }
    }

    private fun showToast(text: String) {

        val toast = Toast.makeText(this, text, Toast.LENGTH_SHORT)

        // Set the position of the toast
        toast.setGravity(Gravity.CENTER_HORIZONTAL, 0, 0) 

        val viewGroup = toast.view as ViewGroup?

          // Get the TextView of the toast
        val textView = viewGroup!!.getChildAt(0) as TextView 

        // Set the text size
        textView.textSize = 20f 

        // Set the background color of toast
        viewGroup!!.setBackgroundColor(Color.parseColor("#079A0F")) 

        // Display the Toast
        toast.show() 
    }
}
```

所以我们的应用已经准备好了。

**输出:**

<video class="wp-video-shortcode" id="video-692761-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20211005184532/video_2021-10-05_18-44-57.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20211005184532/video_2021-10-05_18-44-57.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20211005184532/video_2021-10-05_18-44-57.mp4)</video>