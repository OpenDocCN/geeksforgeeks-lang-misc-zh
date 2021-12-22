# 安卓在科特林淡入淡出

> 原文:[https://www . geesforgeks . org/Android-淡入淡出-in-kotlin/](https://www.geeksforgeeks.org/android-fade-in-out-in-kotlin/)

在**安卓**中，动画是为了使用户界面更具交互性、清晰和美观而添加的视觉效果。淡入和淡出动画用于在设定的时间间隔内修改任何视图的外观，以便用户可以被告知我们的应用程序中正在发生的变化。
在本文中，我们将讨论如何在科特林创建淡入淡出动画。

<figure class="table">

| XML 属性 | 描述 |
| --- | --- |
| 安卓:持续时间 | 它用于指定动画的持续时间 |
| 安卓:fromAlpha | 这是动画的起始 alpha 值，
其中 1.0 表示完全不透明，0.0 表示完全透明 |
| 安卓:toAlpha | 这是结束 alpha 值 |
| android:id | 设置视图的唯一 id |

</figure>

第一步是在安卓工作室创建一个新的项目。为此，请遵循以下步骤:

*   单击文件，然后单击新建，然后单击**新建**项目，并给出您喜欢的名称
*   然后，选择 **Kotlin** 语言支持，点击下一步按钮。
*   选择最小 SDK，无论您需要什么
*   选择**清空**活动，然后点击完成。

之后，我们需要设计我们的布局。为此，我们需要处理 XML 文件。进入 app > res >布局，粘贴如下代码:

## 修改 activity_main.xml 文件

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
              xmlns:app="http://schemas.android.com/apk/res-auto"
              xmlns:tools="http://schemas.android.com/tools"
              android:layout_width="match_parent"
              android:layout_height="match_parent"
              tools:context=".MainActivity" android:orientation="vertical">

    <TextView
            android:id="@+id/textView"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="GeeksForGeeks"
            android:layout_centerInParent="true"
            android:textSize="30sp"
            android:textStyle="bold" />

    <Button
            android:id="@+id/fade_in"
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:text="Fade In"
            android:layout_marginTop="140dp"
            android:layout_marginLeft="100dp" />
    <Button
            android:id="@+id/fade_out"
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:layout_marginTop="140dp"
            android:layout_toRightOf="@+id/fade_in"
            android:text="Fade Out"
            android:textAllCaps="false" />

</RelativeLayout>
```

## 添加动漫文件夹

在这个文件夹中，我们将添加用于制作动画的 XML 文件。为此，请转到 **app/res** 右键，然后选择，安卓资源目录，并将其命名为**动漫**。
再次右键点击这个动漫文件夹，选择动漫资源文件，命名为**淡入**。同样，也创建**淡出. xml** 并粘贴以下代码。
**淡入淡出**

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    android:interpolator="@android:anim/linear_interpolator">
    <alpha
        android:duration="2000"
        android:fromAlpha="0.1"
        android:toAlpha="1.0" />
</set>
```

**淡出 T2】**

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    android:interpolator="@android:anim/linear_interpolator">
    <alpha
        android:duration="2000"
        android:fromAlpha="1.0"
        android:toAlpha="0.1" />
</set>
```

## 修改 MainActivity.kt 文件

打开 app/src/main/Java/your package name/main activity . kt，进行如下更改:

## Java 语言(一种计算机语言，尤用于创建网站)

```
package com.geeksforgeeks.myfirstKotlinapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.os.Handler
import android.view.View
import android.view.animation.AnimationUtils
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        //setting button onClickListener
        fade_in.setOnClickListener {
        textView.visibility = View.VISIBLE
        //loading our custom made animations
        val animation = AnimationUtils.loadAnimation(this, R.anim.fade_in)
        //starting the animation
        textView.startAnimation(animation)
    }
    fade_out.setOnClickListener {
        val animation = AnimationUtils.loadAnimation(this, R.anim.fade_out)
        textView.startAnimation(animation)
        //textview will be invisible after the specified amount
        // of time elapses, here it is 1000 milliseconds
        Handler().postDelayed({
            textView.visibility = View.GONE
        }, 1000)
    }
}
}
```

## AndroidManifest.xml 文件

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="i.apps.fadeinout">

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

<video class="wp-video-shortcode" id="video-362233-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20191123220618/fadein1.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20191123220618/fadein1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20191123220618/fadein1.mp4)</video>