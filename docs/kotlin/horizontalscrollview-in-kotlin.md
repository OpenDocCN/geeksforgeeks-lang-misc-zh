# 科特林水平卷轴视图

> 哎哎哎:# t0]https://www . geeksforgeeks . org/horizontal scroll view-in-kot Lin/

在**安卓**滚动视图允许位于父视图组内的多个视图滚动。安卓应用程序中的滚动可以通过两种方式完成:垂直或水平。

在本文中，我们将讨论如何在 Kotlin 中创建一个水平滚动视图。

| XML 属性 | 描述 |
| --- | --- |
| android:fillViewport(填充视口) | 它定义水平滚动视图是否应该拉伸其内容以填充视口。 |
| 安卓:布局 _ 高度 | 设置水平滚动视图的高度 |
| 安卓:布局 _ 宽度 | 设置水平滚动视图的宽度 |
| android:src | 设置图像的背景 |
| android:id | 设置视图的唯一 id |

让我们首先在安卓工作室创建一个项目。为此，请遵循以下说明:

第一步是在安卓工作室创建一个新的项目。为此，请遵循以下步骤:

*   点击文件，然后**新建**然后新建项目，给你喜欢的名字
*   然后，选择 **Kotlin** 语言支持，点击下一步按钮。
*   选择最小 SDK，无论您需要什么
*   选择空活动，然后点击**完成**。

## 修改 activity_main.xml 文件

```
<?xml version="1.0" encoding="utf-8"?>
<HorizontalScrollView
        xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent">

    <LinearLayout
            android:layout_width="200dp"
            android:layout_height="200dp"
            android:layout_marginTop="20dp"
            android:orientation="horizontal">

        <ImageView
                android:id="@+id/image1"
                android:layout_width="200dp"
                android:layout_height="200dp"
                android:layout_marginRight="20dp"
                android:src="@mipmap/image1"/>

        <ImageView
                android:id="@+id/image2"
                android:layout_width="200dp"
                android:layout_height="200dp"
                android:layout_marginRight="20dp"
                android:src="@mipmap/image2"/>

        <ImageView
                android:id="@+id/image3"
                android:layout_width="200dp"
                android:layout_height="200dp"
                android:layout_marginRight="20dp"
                android:src="@mipmap/image3"/>

        <ImageView
                android:id="@+id/image4"
                android:layout_width="200dp"
                android:layout_height="200dp"
                android:layout_marginRight="20dp"
                android:src="@mipmap/image4"/>

    </LinearLayout>
</HorizontalScrollView>
```

## 添加图像

我们需要添加一些图像，可以用于滚动的目的。因此，我们必须将图像从本地计算机路径复制到 app/res/mipmap 文件夹。

**注意:**我们已经将图像添加到 mipmap 文件夹，而不是可绘制文件夹，因为图像的大小非常大。

## 在 MainActivity.kt 文件中创建水平滚动视图

打开 app/src/main/Java/your package name/main activity . kt 并进行以下更改:

```
package com.geeksforgeeks.myfirstKotlinapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}
```

## AndroidManifest.xml 文件

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="i.apps.hscrollview">

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
<video class="wp-video-shortcode" id="video-362250-1" width="284" height="480" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20191125223135/HScroll.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20191125223135/HScroll.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20191125223135/HScroll.mp4)</video>
</center>