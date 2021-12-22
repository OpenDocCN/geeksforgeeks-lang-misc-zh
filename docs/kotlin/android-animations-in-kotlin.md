# Kotlin 中的安卓动画

> 原文:[https://www.geeksforgeeks.org/android-animations-in-kotlin/](https://www.geeksforgeeks.org/android-animations-in-kotlin/)

动画是一种方法，其中一组图像以特定的方式组合并处理，然后它们作为运动图像出现。构建动画使屏幕上的对象看起来像是活的。安卓有相当多的工具可以帮助你相对轻松地创建动画。因此在本文中，我们将学习使用 Kotlin 创建动画。下面是我们在用 xml 编写代码时使用的一些属性。

**属性表:**

<figure class="table">

| XML ATTRIBUTES | 描述 |
| --- | --- |
| 安卓:持续时间 | 它用于指定动画运行的持续时间 |
| 安卓:fromAlpha | 这是动画的起始 alpha 值，
其中 1.0 表示完全不透明，0.0 表示完全透明 |
| 安卓:toAlpha | 这是结束 alpha 值 |
| android:id | 设置视图的唯一 id |
| 安卓:fromYDelta | 这是要在动画开始时应用的 Y 坐标变化 |
| 安卓:玩具反斗城 | 这是要在动画结束时应用的 Y 坐标变化 |
| android:启动偏移 | 到达开始时间后，动画运行时会出现延迟(以毫秒为单位)。 |
| android:pivotX | 它表示从起点开始缩放的 X 轴坐标。 |
| Android:pivot(旋转) | 它表示从起点开始缩放的 Y 轴坐标。 |
| android:fromXScale | 起始 X 尺寸偏移， |
| android:fromYScale | 起始 Y 尺寸偏移， |
| android:toXScale | X 尺寸偏移的结束 |
| 安卓:toYScale | Y 尺寸偏移的结束 |
| 安卓:从度 | 起始角度位置，单位为度。 |
| 安卓:toDegrees | 结束角度位置，单位为度。 |
| 安卓:插值器 | 插值器定义动画的变化率 |

</figure>

首先，我们将创建一个新的安卓应用程序。然后，我们将创建一些动画。
如果已经创建了项目，则忽略步骤 1。

### 创建新项目

1.  打开安卓工作室
2.  转到文件= >新建= >新项目。
3.  然后，选择空活动并单击下一步
    *   将应用程序名称写成 DynamicEditTextKotlin
    *   根据需要选择最小 SDK，这里我们选择了 21 作为最小 SDK
    *   选择语言为 Kotlin，然后点击完成按钮。

如果您正确地遵循了上述过程，您将成功地获得一个新创建的项目。
创建项目后，我们将修改 xml 文件。在 xml 文件中，我们将创建一个执行所有动画的*文本视图*，以及八个不同动画的*八个按钮*。

### 修改 activity_main.xml 文件

打开 res/layout/activity_main.xml 文件并向其中添加代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <TextView
        android:id="@+id/textView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_above="@+id/linearLayout"
        android:gravity="center"
        android:text="Geeks for Geeks"
        android:textSize="32sp"
        android:textColor="@color/colorPrimaryDark"
        android:textStyle="bold" />
    <LinearLayout
        android:id="@+id/linearLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:orientation="vertical">
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:weightSum="2">
            <Button
                android:id="@+id/fade_in"
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:text="Fade In"
                android:textAllCaps="false" />
            <Button
                android:id="@+id/fade_out"
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:text="Fade Out"
                android:textAllCaps="false" />
        </LinearLayout>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:weightSum="2">
            <Button
                android:id="@+id/zoom_in"
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:text="Zoom In"
                android:textAllCaps="false" />
            <Button
                android:id="@+id/zoom_out"
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:text="Zoom Out"
                android:textAllCaps="false" />
        </LinearLayout>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:weightSum="2">
            <Button
                android:id="@+id/slide_down"
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:text="Slide Down"
                android:textAllCaps="false" />
            <Button
                android:id="@+id/slide_up"
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:text="Slide Up"
                android:textAllCaps="false" />
        </LinearLayout>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:weightSum="2">
            <Button
                android:id="@+id/bounce"
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:text="Bounce"
                android:textAllCaps="false" />
            <Button
                android:id="@+id/rotate"
                android:layout_width="0dp"
                android:layout_height="match_parent"
                android:layout_weight="1"
                android:text="Rotate"
                android:textAllCaps="false" />
        </LinearLayout>
    </LinearLayout>
</RelativeLayout>
```

修改布局后，我们将为*动画*创建 xml 文件。所以我们将首先创建一个名为*动漫*的文件夹。
在这个文件夹中，我们将添加用于制作动画的 XML 文件。为此，请转到 app/res 右键单击，然后选择*安卓资源目录*并将其命名为动漫。

### bounce.xml

在这个动画中，文本像球一样弹跳。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/linear_interpolator"
    android:fillAfter="true">
    <translate
        android:fromYDelta="100%"
        android:toYDelta="-20%"
        android:duration="300" />
    <translate
        android:startOffset="500"
        android:fromYDelta="-20%"
        android:toYDelta="10%"
        android:duration="150" />
    <translate
        android:startOffset="1000"
        android:fromYDelta="10%"
        android:toYDelta="0"
        android:duration="100" />
</set>
```

### 淡入. xml

在淡入动画中，文本将从背景中出现。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/linear_interpolator">
    <alpha
        android:duration="1000"
        android:fromAlpha="0.1"
        android:toAlpha="1.0" />
</set>
```

### 淡出. xml

在淡出动画中，文本的颜色会在特定的时间内淡化。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/linear_interpolator">
    <alpha
        android:duration="1000"
        android:fromAlpha="1.0"
        android:toAlpha="0.1" />
</set>
```

### rotate.xml

在旋转动画中，文本旋转一段特定的时间。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<rotate xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="1000"
    android:fromDegrees="0"
    android:interpolator="@android:anim/linear_interpolator"
    android:pivotX="50%"
    android:pivotY="50%"
    android:startOffset="0"
    android:toDegrees="360" />
```

### slide_down.xml

在这个动画中，文本将从上到下。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <translate
        android:duration="1000"
        android:fromYDelta="-100%"
        android:toYDelta="0" />
</set>
```

### slide_up.xml

在这个动画中，文本将从底部到顶部。

## 可扩展标记语言

```
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <translate
        android:duration="1000"
        android:fromYDelta="0"
        android:toYDelta="-100%" />
</set>
```

### 放大. xml

在此动画中，文本在特定时间内会变大。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true">
    <scale xmlns:android="http://schemas.android.com/apk/res/android"
        android:duration="1000"
        android:fromXScale="1"
        android:fromYScale="1"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toXScale="1.5"
        android:toYScale="1.5">
    </scale>
</set>
```

### zoom_out.xml

在此动画中，文本在特定时间内会变小。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >
    <scale
        xmlns:android="http://schemas.android.com/apk/res/android"
        android:duration="1000"
        android:fromXScale="1.0"
        android:fromYScale="1.0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toXScale="0.5"
        android:toYScale="0.5" >
    </scale>
</set>
```

在用 xml 创建所有动画之后。我们将创建主活动。

### 创建 MainActivity.kt 文件

打开 app/src/main/Java/net . geeks forgeeks . animationsinkotlin/mainactivity . kt 文件，并在其中添加以下代码。

## Java 语言(一种计算机语言，尤用于创建网站)

```
package net.geeksforgeeks.animationsinkotlin

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
        fade_in.setOnClickListener {
            textView.visibility = View.VISIBLE
            val animationFadeIn = AnimationUtils.loadAnimation(this, R.anim.fade_in)
            textView.startAnimation(animationFadeIn)
        }
        fade_out.setOnClickListener {
            val animationFadeOut = AnimationUtils.loadAnimation(this, R.anim.fade_out)
            textView.startAnimation(animationFadeOut)
            Handler().postDelayed({
                textView.visibility = View.GONE
            }, 1000)
        }
        zoom_in.setOnClickListener {
            val animationZoomIn = AnimationUtils.loadAnimation(this, R.anim.zoom_in)
            textView.startAnimation(animationZoomIn)
        }
        zoom_out.setOnClickListener {
            val animationZoomOut = AnimationUtils.loadAnimation(this, R.anim.zoom_out)
            textView.startAnimation(animationZoomOut)
        }
        slide_down.setOnClickListener {
            val animationSlideDown = AnimationUtils.loadAnimation(this, R.anim.slide_in)
            textView.startAnimation(animationSlideDown)
        }
        slide_up.setOnClickListener {
            val animationSlideUp = AnimationUtils.loadAnimation(this, R.anim.slide_out)
            textView.startAnimation(animationSlideUp)
        }
        bounce.setOnClickListener {
            val animationBounce = AnimationUtils.loadAnimation(this, R.anim.bounce)
            textView.startAnimation(animationBounce)
        }
        rotate.setOnClickListener {
            val animationRotate = AnimationUtils.loadAnimation(this, R.anim.rotate)
            textView.startAnimation(animationRotate)
        }
    }
}
```

As， **AndroidManifest.xml** 文件是安卓应用中非常重要的文件，所以下面是 Manifest 文件的代码。

### AndroidManifest.xml 文件

```
Code inside src/main/AndroidManifest.xml file would look like below
```

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="net.geeksforgeeks.animationsinkotlin">

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

### 作为模拟器运行:

<video class="wp-video-shortcode" id="video-365107-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20191203180727/WhatsApp-Video-2019-12-03-at-6.04.23-PM.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20191203180727/WhatsApp-Video-2019-12-03-at-6.04.23-PM.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20191203180727/WhatsApp-Video-2019-12-03-at-6.04.23-PM.mp4)</video>

你可以在这里找到完整的代码:[https://github.com/missyadavmanisha/AnimationsInKotlin](https://github.com/missyadavmanisha/AnimationsInKotlin)T2】