# 安卓在科特林上下滑动

> 原文:[https://www . geesforgeks . org/Android-slide-up-down-in-kot Lin/](https://www.geeksforgeeks.org/android-slide-up-down-in-kotlin/)

在**安卓**中，动画是为了使用户界面更具交互性、清晰和美观而添加的视觉效果。

在本文中，我们将讨论如何在 Kotlin 中创建上滑/下滑动画。

| XML 属性 | 描述 |
| --- | --- |
| 安卓:持续时间 | 它用于指定动画的持续时间 |
| 安卓:fromYDelta | 这是要在动画开始时应用的 Y 坐标变化 |
| 安卓:玩具反斗城 | 这是要在动画结束时应用的 Y 坐标变化 |
| android:id | 设置视图的唯一 id |

第一步是在安卓工作室创建一个新的项目。为此，请遵循以下步骤:

*   单击文件，然后单击新建，然后单击**新建**项目，并给出您喜欢的名称
*   然后，选择 **Kotlin** 语言支持，点击下一步按钮。
*   选择最小 SDK，无论您需要什么
*   选择**清空**活动，然后点击完成。

之后，我们需要设计我们的布局。为此，我们需要处理 XML 文件。转到应用>资源>布局并粘贴以下代码:

## 修改 activity_main.xml 文件

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
            android:id="@+id/slide_up"
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:text="Slide Up"
            android:layout_marginTop="140dp"
            android:layout_marginLeft="100dp" />
    <Button
            android:id="@+id/slide_down"
            android:layout_width="100dp"
            android:layout_height="wrap_content"
            android:layout_marginTop="140dp"
            android:layout_toRightOf="@+id/slide_up"
            android:text="Slide Down"
            android:textAllCaps="false" />

</RelativeLayout>
```

## 添加动漫文件夹

在这个文件夹中，我们将添加用于制作动画的 XML 文件。为此，请转到 **app/res** 右键，然后选择，安卓资源目录，并将其命名为**动漫**。
再次右键点击这个动漫文件夹，选择动漫资源文件，命名为**上滑**。同样，也创建 **slide_down.xml** 并粘贴以下代码。

**slide_up.xml**

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <translate
            android:duration="1000"
            android:fromYDelta="0"
            android:toYDelta="-100%" />
</set>
```

**slide_down.xml**

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <translate
            android:duration="1000"
            android:fromYDelta="-100%"
            android:toYDelta="0" />
</set>
```

## 修改 MainActivity.kt 文件

打开 app/src/main/Java/your package name/main activity . kt 并进行以下更改:

```
package com.geeksforgeeks.myfirstKotlinapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.animation.AnimationUtils
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        //setting buttons onClickListener
        slide_down.setOnClickListener {
            //adding our custom made animation xml file
            val animation = AnimationUtils.loadAnimation(
                this, R.anim.fade_out)
            //appending animation to textView
            textView.startAnimation(animation)
        }
        slide_up.setOnClickListener {
            val animation = AnimationUtils.loadAnimation(
                this, R.anim.fade_in)
            textView.startAnimation(animation)
        }
    }
}
```

## AndroidManifest.xml 文件

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="i.apps.slideup">

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

<center>
<video class="wp-video-shortcode" id="video-362243-1" width="260" height="460" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20191124123100/slideUp.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20191124123100/slideUp.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20191124123100/slideUp.mp4)</video>
</center>