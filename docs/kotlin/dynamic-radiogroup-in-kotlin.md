# 科特林动态电台群

> 原文:[https://www.geeksforgeeks.org/dynamic-radiogroup-in-kotlin/](https://www.geeksforgeeks.org/dynamic-radiogroup-in-kotlin/)

在**安卓**中，单选组用于设置单选按钮。如果在单选按钮组中选择了一个单选按钮，则会自动取消选择所有其他单选按钮。

在本文中，我们将讨论如何在 Kotlin 中以编程方式创建一个 RadioGroup。

让我们首先在安卓工作室创建一个项目。为此，请遵循以下说明:

*   点击文件，然后**新建**，然后新建项目，给你喜欢的名字
*   然后，选择 **Kotlin** 语言支持，点击下一步按钮。
*   选择最小 SDK，无论您需要什么
*   选择空活动，然后点击**完成**。

之后，我们需要设计我们的布局。为此，我们需要处理 XML 文件。转到应用>资源>布局并粘贴以下代码:

## 修改 activity_main.xml 文件

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:gravity="center"
        android:id="@+id/layout"
        android:layout_height="match_parent"
        tools:context=".MainActivity">

</RelativeLayout>
```

## MainActivity.kt 公司

下一步是对我们的无线电组进行编码。打开 app/src/main/Java/your package name/main activity . kt，粘贴以下代码:

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
package com.geeksforgeeks.myfirstKotlinapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.ViewGroup
import android.widget.RadioButton
import android.widget.RadioGroup
import android.widget.RelativeLayout
import android.widget.Toast

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val layout = findViewById<RelativeLayout>(R.id.layout)

        // Create RadioButton Dynamically
        val geek1 = RadioButton(this)
        //setting height and width
        geek1.layoutParams = RelativeLayout.LayoutParams(ViewGroup.LayoutParams.WRAP_CONTENT, ViewGroup.LayoutParams.WRAP_CONTENT)
        geek1.setText(R.string.java) //setting text of first radio button
        geek1.id = 0

        val geek2 = RadioButton(this)
        geek2.layoutParams = RelativeLayout.LayoutParams(ViewGroup.LayoutParams.WRAP_CONTENT, ViewGroup.LayoutParams.WRAP_CONTENT)
        geek2.setText(R.string.python) ////setting text of second radio button
        geek2.id = 1

        // Create RadioGroup Dynamically
        val radioGroup = RadioGroup(this)
        val params = RelativeLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.WRAP_CONTENT)
        params.setMargins(40, 0, 0, 0)
        radioGroup.layoutParams = params

        //adding button to the radio group container
        radioGroup.addView(geek1)
        radioGroup.addView(geek2)
        layout.addView(radioGroup)

        radioGroup.setOnCheckedChangeListener { group, checkedId ->
            var text = getString(R.string.Chose)
            text += " " + getString(if (checkedId == 0) {
                R.string.java
            } else {
                R.string.python
            })
            Toast.makeText(applicationContext, text, Toast.LENGTH_SHORT).show()
        }

    }
}
```

上面的代码仍然会产生一些错误，因为我们使用了一些已经在另一个文件中声明的字符串，要解决这些问题，请将以下代码片段添加到**app/RES/values/strings . XML**

## 可扩展标记语言

```kt
<resources>
    <string name="app_name">My Application</string>
    <string name="java">Java</string>
    <string name="python">Python</string>
    <string name="Choose">You selected:</string>

</resources>
```

## AndroidManifest.xml

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
<?xml version="1.0" encoding="utf-8"?>
<manifest package="com.tutorialwing.dynamicradiogroup"
xmlns:android="<a class="vglnk" href="http://schemas.android.com/apk/res/android" rel="nofollow">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>

                <category android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>
        </activity>
    </application>

</manifest>
```

## 作为模拟器运行:

<video class="wp-video-shortcode" id="video-362222-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20191121225724/Group.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20191121225724/Group.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20191121225724/Group.mp4)</video>