# Kotlin 中的动态自动完成文本视图

> 原文:[https://www . geeksforgeeks . org/dynamic-autocompletetextview-in-kot Lin/](https://www.geeksforgeeks.org/dynamic-autocompletetextview-in-kotlin/)

安卓**自动完成文本视图**是一个可编辑的文本视图，当用户开始输入文本时，它会显示一个建议列表。当用户开始输入时，会出现一个基于输入字符的下拉菜单，在阈值限制中定义，用户可以从列表中选择一个项目来替换文本。

自动完成文本视图是编辑文本类的一个子类，因此我们可以根据自己的需求轻松继承编辑文本的所有属性。

下拉列表将使用数据适配器获得，这些建议只有在输入阈值限制中定义的最小字符数后才会出现。**阈值限制**用于定义用户必须键入的最小字符数，以查看建议的下拉列表。

在 android 中，我们可以通过两种方式创建一个 AutoCompleteTextView 控件，要么在 XML 文件中手动创建，要么在 Activity 文件中以编程方式创建。

首先，我们按照以下步骤创建一个**新项目**:

1.  点击文件，然后**新建** = > **新项目**。
2.  之后加入 Kotlin 支持，点击下一步。
3.  根据方便选择最小 SDK，点击下一步按钮。
4.  然后选择**清空**活动= > **下一个** = > **完成**。

## 在 activity_main.xml 文件中使用 LinearLayout

在这个文件中，我们只使用线性布局并设置它的属性。

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/linear_layout"
    android:gravity = "center">

</LinearLayout>
```

## 在 strings.xml 文件中创建建议列表

在这里，我们将指定活动的名称，并定义可以在活动的不同位置使用的其他字符串。另一件重要的事情是，我们将定义 **string_array** ，它包含**自动完成文本视图**的建议列表的项目。

```
<resources>
    <string name="app_name">DynamicAutoCompleteTextView</string>
    <string name="hint">Please type language...</string>
    <string name="submit">Submit</string>
    <string name="submitted_lang">Submitted language:</string>

    <string-array name="Languages">
        <item>Java</item>
        <item>Kotlin</item>
        <item>Swift</item>
        <item>Python</item>
        <item>Scala</item>
        <item>Perl</item>
        <item>Javascript</item>
        <item>Jquery</item>
    </string-array>

</resources>
```

## 在 MainActivity.kt 文件中创建自动完成文本视图和按钮

首先，我们声明两个变量*自动文本视图*和*按钮*来创建小部件并设置它们的属性。

```
val autotextView = AutoCompleteTextView(this)
val button = Button(this)

```

并使用在线形布局中添加自动图文视图和按钮

```
val linearLayout = findViewById(R.id.linear_layout)
   // Add AutoCompleteTextView and button to LinearLayout
     linearLayout?.addView(autotextView)
     linearLayout?.addView(button) 
```

然后，我们声明另一种变量语言，从 strings.xml 文件中获取字符串数组的项。

```
val languages = resources.getStringArray(R.array.Languages)
```

创建一个适配器，并使用

```
val adapter = ArrayAdapter(this,
       android.R.layout.simple_list_item_1, languages)
       autotextView.setAdapter(adapter)

```

```
package com.geeksforgeeks.myfirstkotlinapp

import android.os.Bundle
import android.view.View
import android.view.ViewGroup
import android.widget.*
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        //create AutoCompleteTextView and button
        val autotextView = AutoCompleteTextView(this)
        val button = Button(this)
        val layoutParams = LinearLayout.LayoutParams(
            ViewGroup.LayoutParams.MATCH_PARENT,
            ViewGroup.LayoutParams.WRAP_CONTENT)
        autotextView.layoutParams = layoutParams
        button.layoutParams = layoutParams
        layoutParams.setMargins(30, 30, 30, 30)
        autotextView.setHint(R.string.hint)
        button.setText("Submit")

        val linearLayout = findViewById<LinearLayout>(R.id.linear_layout)
        // Add AutoCompleteTextView and button to LinearLayout
        linearLayout?.addView(autotextView)
        linearLayout?.addView(button)

        // Get the array of languages
        val languages = resources.getStringArray(R.array.Languages)
        // Create adapter and add in AutoCompleteTextView
        val adapter = ArrayAdapter(this,
            android.R.layout.simple_list_item_1, languages)
        autotextView.setAdapter(adapter)

        if (button != null) {
            button?.setOnClickListener(View.OnClickListener {
                val enteredText = getString(R.string.submitted_lang)+ " " +
                        autotextView.getText()
                Toast.makeText(this@MainActivity,
                    enteredText, Toast.LENGTH_SHORT).show()
            })
        }
    }
}
```

## AndroidManifest.xml 文件

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
package="com.geeksforgeeks.myfirstkotlinapp">

<application
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:supportsRtl="true"
    android:theme="@style/AppTheme">
    <activity android:name=".MainActivity">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />

            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
</application>

</manifest>
```

## 作为模拟器运行:

![](img/3e58ce0ad566ff7247b8be210f749228.png)![](img/1f5b8f67b40ce6a40bd797e2448c3de5.png)