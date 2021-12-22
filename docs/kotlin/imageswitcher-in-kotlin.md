# 科特林的图像开关

> 原文:[https://www.geeksforgeeks.org/imageswitcher-in-kotlin/](https://www.geeksforgeeks.org/imageswitcher-in-kotlin/)

安卓 **ImageSwitcher** 是一个用户界面小部件，它为图像提供平滑的过渡动画效果，同时在图像之间切换以在视图中显示。

ImageSwitcher 是 View Switcher 的一个子类，用于动画化一个图像并显示下一个图像。
一般来说，我们在 XML 布局中手动使用 ImageSwitcher 和在 Kotlin 文件中以编程方式使用 ImageSwitcher 两种方式。

我们应该定义一个 XML 组件，在我们的 android 应用程序中使用 *ImageSwitcher* 。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
<ImageSwitcher android:id="@+id/imgSw"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
</ImageSwitcher>
```

首先，我们按照以下步骤创建一个**新项目**:

1.  点击**文件**，然后**新建** = > **新建项目**。
2.  之后加入 Kotlin 支持，点击下一步。
3.  根据方便选择最小 SDK，点击下一步按钮。
4.  然后选择**清空**活动= > **下一个** = > **完成**。

## ImageSwitcher 小部件的不同属性

<figure class="table">

| XML 属性 | 描述 |
| --- | --- |
| android:id | 用于指定视图的 id。 |
| android:onClick | 用于指定单击此视图时的操作。 |
| 安卓:背景 | 用于设置视图的背景。 |
| 安卓:填充 | 用于设置视图的填充。 |
| 安卓:可见性 | 用于设置视图的可见性。 |
| Android:inam 动画 | 用于定义显示视图时使用的动画。 |
| android:动画 | 用于定义视图隐藏时使用的动画。 |
| Android:animated first view | 用于定义第一次显示视图动画时是否动画显示当前视图。 |

</figure>

## 修改 activity_main.xml 文件

在这个文件中，我们使用约束布局与图像切换器和按钮。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
   xmlns:android="http://schemas.android.com/apk/res/android"
   xmlns:app="http://schemas.android.com/apk/res-auto"
   android:layout_width="match_parent"
   android:layout_height="match_parent"
   android:orientation="vertical"
   android:id="@+id/constraint_layout">

   <ImageSwitcher
       android:id="@+id/imgSw"
       android:layout_width="match_parent"
       android:layout_height="250dp"
       android:layout_marginStart="8dp"
       android:layout_marginTop="8dp"
       android:layout_marginEnd="8dp"
       android:layout_marginBottom="36dp"
       app:layout_constraintBottom_toTopOf="@+id/prev"
       app:layout_constraintEnd_toEndOf="parent"
       app:layout_constraintStart_toStartOf="parent"
       app:layout_constraintTop_toTopOf="parent" />

   <Button
       android:id="@+id/prev"
       android:layout_width="wrap_content"
       android:layout_height="wrap_content"
       android:layout_marginStart="36dp"
       android:layout_marginTop="36dp"
       android:text="@string/prev"
       app:layout_constraintStart_toStartOf="parent"
       app:layout_constraintTop_toBottomOf="@+id/imgSw" />

   <Button
       android:id="@+id/next"
       android:layout_width="wrap_content"
       android:layout_height="wrap_content"
       android:layout_marginTop="36dp"
       android:layout_marginEnd="36dp"
       android:text="@string/next"
       app:layout_constraintEnd_toEndOf="parent"
       app:layout_constraintHorizontal_bias="1.0"
       app:layout_constraintStart_toEndOf="@+id/prev"
       app:layout_constraintTop_toBottomOf="@+id/imgSw" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

## 更新 strings.xml 文件

这里，我们使用字符串标签更新应用程序的名称。

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
<resources>
   <string name="app_name">ImageSwitcherInKotlin</string>
   <string name="next">Next</string>
   <string name="prev">Prev</string>
</resources>
```

## ImageSwitcher 小部件的不同方法

<figure class="table">

| 方法 | 描述 |
| --- | --- |
| setimagedrawinable | 它用于在切换器中的下一个图像视图上设置新的可绘制对象。 |
| setImageResource | 它用于在 ImageSwitcher 上设置具有给定资源 id 的新图像。 |
| setImageURI | 它用于在带有给定 URI 的图像切换器上设置新图像。 |

</figure>

## 访问 MainActivity.kt 文件中的 ImageSwitcher

首先，我们声明一个数组**花**，它包含用于 ImageView 的图像资源。

```kt
private val flowers = intArrayOf(R.drawable.flower1,
       R.drawable.flower2, R.drawable.flower4)
```

然后，我们从 XML 布局中访问 **ImageSwitcher** ，设置 ImageView 显示图像。

```kt
val imgSwitcher = findViewById<ImageSwitcher>(R.id.imgSw)
imgSwitcher?.setFactory({
           val imgView = ImageView(applicationContext)
           imgView.scaleType = ImageView.ScaleType.FIT_CENTER
           imgView.setPadding(8, 8, 8, 8)
           imgView
           })
```

此外，我们将对 ImageSwitcher 使用上述方法之一。

```kt
imgSwitcher?.setImageResource(flowers[index])
```

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
package com.geeksforgeeks.myfirstkotlinapp

import androidx.appcompat.app.AppCompatActivity

import android.os.Bundle
import android.view.animation.AnimationUtils
import android.widget.Button
import android.widget.ImageSwitcher
import android.widget.ImageView

class MainActivity : AppCompatActivity() {

   private val flowers = intArrayOf(R.drawable.flower1,
       R.drawable.flower2, R.drawable.flower4)
   private var index = 0

   override fun onCreate(savedInstanceState: Bundle?) {
       super.onCreate(savedInstanceState)
       setContentView(R.layout.activity_main)

       // access the ImageSwitcher
       val imgSwitcher = findViewById<ImageSwitcher>(R.id.imgSw)

       imgSwitcher?.setFactory({
           val imgView = ImageView(applicationContext)
           imgView.scaleType = ImageView.ScaleType.FIT_CENTER
           imgView.setPadding(8, 8, 8, 8)
           imgView
           })

        // set the method and pass array as a parameter
        imgSwitcher?.setImageResource(flowers[index])

        val imgIn = AnimationUtils.loadAnimation(
           this, android.R.anim.slide_in_left)
        imgSwitcher?.inAnimation = imgIn

        val imgOut = AnimationUtils.loadAnimation(
           this, android.R.anim.slide_out_right)
        imgSwitcher?.outAnimation = imgOut

        // previous button functionality
        val prev = findViewById<Button>(R.id.prev)
        prev.setOnClickListener {
           index = if (index - 1 >= 0) index - 1 else 2
           imgSwitcher?.setImageResource(flowers[index])
         }
        // next button functionality
        val next = findViewById<Button>(R.id.next)
        next.setOnClickListener {
           index = if (index + 1 < flowers.size) index +1 else 0
           imgSwitcher?.setImageResource(flowers[index])
       }
   }
}
```

## AndroidManifest.xml 文件

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
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

点击**下一步**按钮，然后我们得到视图中的另一个动画图像。