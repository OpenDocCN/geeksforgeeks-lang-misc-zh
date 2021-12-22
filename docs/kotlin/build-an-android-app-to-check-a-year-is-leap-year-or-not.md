# 建一个安卓应用检查一年是不是闰年

> 原文:[https://www . geesforgeks . org/build-an-Android-app-to-check-a-year-is-leap-year-or-not/](https://www.geeksforgeeks.org/build-an-android-app-to-check-a-year-is-leap-year-or-not/)

在这篇文章中，我们将学习如何让一个应用程序检查一年是否是闰年。在此之前，我们需要有一个什么是闰年的概念？如果一年是:

1.  400 的倍数
2.  4 的倍数而不是 100 的倍数

那么这一年就是闰年。

### 算法

*   如果一年能被 400 整除，那么它就是闰年。
*   否则，如果一年能被 100 整除，那就不是闰年。
*   否则，如果一年能被 4 整除，那么它就是闰年。
*   否则就不是闰年。

现在我们将为此制作一个应用程序。所以，如果我们发现一年是不是闰年，我们会显示一个[吐司](https://www.geeksforgeeks.org/android-what-is-toast-and-how-to-use-it-with-examples/)。

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:background="@color/teal_200">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Leap year or Not"
        android:textColor="@color/black"
        android:textSize="26sp"
        app:layout_constraintBottom_toTopOf="@+id/textView"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.491" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Enter a year to check it is leap year or not"
        android:textColor="@color/black"
        android:textSize="18sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.494"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.4" />

    <EditText
        android:id="@+id/etYear"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:hint="ENTER THE YEAR"
        android:inputType="number"
        app:layout_constraintEnd_toEndOf="@+id/textView"
        app:layout_constraintStart_toStartOf="@+id/textView"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <Button
        android:id="@+id/btnCheck"
        android:layout_width="149dp"
        android:layout_height="50dp"
        android:layout_margin="10dp"
        android:layout_marginTop="16dp"
        android:backgroundTint="@color/black"
        android:text="Check"
        android:textColor="@color/teal_700"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="@+id/etYear"
        app:layout_constraintHorizontal_bias="0.496"
        app:layout_constraintStart_toStartOf="@+id/etYear"
        app:layout_constraintTop_toBottomOf="@+id/etYear"
        app:layout_constraintVertical_bias="0.113" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**第三步:使用**T2【主活动. kt】文件

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。这里我们将绑定视图并编写应用程序的逻辑。

## 我的锅

```
package com.ayush.gfg_leap_year

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.Toast

class MainActivity : AppCompatActivity() {
  lateinit var btnCheck : Button
  lateinit var etYear : EditText

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Binding the views
        btnCheck = findViewById(R.id.btnCheck)
        etYear = findViewById(R.id.etYear)

        btnCheck.setOnClickListener {
            val year = etYear.text.toString().toInt()
            if (year % 400 == 0)
                Toast.makeText(this," Leap Year ", Toast.LENGTH_LONG).show()

            // Else If a year is multiple of 100,
            // then it is not a leap year
            else if (year % 100 == 0)
                Toast.makeText(this,"Not A Leap Year ", Toast.LENGTH_LONG).show()

            // Else If a year is multiple of 4,
            // then it is a leap year
            else if (year % 4 == 0)
                Toast.makeText(this," Leap Year ", Toast.LENGTH_LONG).show()
            // else it is a leap year
            else
                Toast.makeText(this,"Not A Leap Year ", Toast.LENGTH_LONG).show()
        }
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-690053-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210930040040/t_video6244594114344518691.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210930040040/t_video6244594114344518691.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210930040040/t_video6244594114344518691.mp4)</video>