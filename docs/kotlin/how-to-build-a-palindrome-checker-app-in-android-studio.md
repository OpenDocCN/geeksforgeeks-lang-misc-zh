# 如何在安卓工作室搭建回文检查器 App？

> 原文:[https://www . geesforgeks . org/how-build-a-回文-checker-app-in-Android-studio/](https://www.geeksforgeeks.org/how-to-build-a-palindrome-checker-app-in-android-studio/)

在本文中，我们将使用 Kotlin 和 XML 在 android Studio 中构建一个回文检查器 Android 应用程序。该应用程序将检查输入的单词是否是回文，如果输入的单词是回文，那么将显示一条吐司消息“输入的单词是回文”，否则吐司的消息将是“输入的单词不是回文”。

<video class="wp-video-shortcode" id="video-591013-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210413003926/Palindrome.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210413003926/Palindrome.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210413003926/Palindrome.mp4)</video>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:在进入编码部分之前，你首先要做一些前置任务**

**添加颜色:**在你的 **colors.xml** 文件中添加深绿色和白色。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="colorPrimary">#6200EE</color>
    <color name="colorPrimaryDark">#3700B3</color>
    <color name="colorAccent">#03DAC5</color>
    <color name="white">#DFFAF7</color>
    <color name="DarkGreen">#216A33</color>
</resources>
```

**更改主题:**将主题更改为 **styles.xml** 文件中的 NoActionBar。

## 可扩展标记语言

```kt
<resources>
    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
        <!-- Customize your theme here. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
        <item name="colorAccent">@color/colorAccent</item>
    </style>
</resources>
```

**制作渐变背景:**新建一个 drawing able Resource 文件，在 drawing able 目录内命名为“background.xml”，并在其中写入下面的代码。请参考安卓中的[渐变背景。](https://www.geeksforgeeks.org/how-to-create-animatedgradient-in-android/)

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">

    <item>
        <shape>
            <gradient android:angle="90" 
                android:startColor="#ABE89E"
                android:centerColor="#388E3C"
                android:endColor="#00796B"
                />
        </shape>
    </item>
</selector>
```

**步骤 3:使用 activity_main.xml 文件**

该文件包含一个显示我们应用标题的[文本视图](https://www.geeksforgeeks.org/textview-in-kotlin/)，一个从用户处获取输入的[编辑文本](https://www.geeksforgeeks.org/android-edittext-in-kotlin/)视图，以及一个[按钮](https://www.geeksforgeeks.org/button-in-kotlin/)视图，点击该按钮，应用将检查输入的单词是否为回文。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/background"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="GFG Palindrome Checker"
        android:textColor="@color/white"
        android:textSize="35sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.548"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <EditText
        android:id="@+id/editText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_horizontal"
        android:layout_marginTop="128dp"
        android:gravity="center_vertical"
        android:hint="Enter the Word"
        android:textColor="@color/white"
        android:textColorHint="@color/white"
        android:textSize="40sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.659"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <Button
        android:id="@+id/ButtonCheck"
        android:layout_width="128dp"
        android:layout_height="58dp"
        android:background="#fff"
        android:text="Check"
        android:textColor="@color/white"
        android:textSize="25dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editText"
        app:layout_constraintVertical_bias="0.095" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**第 4 步:使用 MainActivity.kt 文件**

在 MainActivity 类中，我们将创建一个函数“**ispalindome()**”，该函数将字符串值作为参数并返回一个布尔值，如果字符串是回文，它将返回 True，如果字符串不是回文，它将返回 False。现在，在 onCreate 函数内部，我们将在 ButtonCheck 上调用 setOnClickListener 方法，在它内部，我们将 editText 的文本值作为参数传递给“ispalindrome()”函数，如果返回值为 True，我们将显示一条消息“输入的单词不是回文”，如果返回值为 False，我们将显示一条消息“输入的单词不是回文”的 [Toast](https://www.geeksforgeeks.org/android-what-is-toast-and-how-to-use-it-with-examples/) 。下面是 **MainActivity.kt** 文件的代码。

## 我的锅

```kt
import android.os.Bundle
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        ButtonCheck.setOnClickListener {
            val text = editText.text.toString()
            if (ispalindrome(text)) {
                Toast.makeText(this, "Entered word is palindrome ", Toast.LENGTH_SHORT).show()

            } else {

                Toast.makeText(this, "Entered word is not a Palindrome", Toast.LENGTH_SHORT).show()

            }
        }
    }

    private fun ispalindrome(text: String): Boolean {
        val reverseString = text.reversed().toString()
        return text.equals(reverseString, ignoreCase = true)
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-591013-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210413004133/palindome_full.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210413004133/palindome_full.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210413004133/palindome_full.mp4)</video>