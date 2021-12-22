# 如何在安卓中创建没有额外活动的闪屏？

> 原文:[https://www . geesforgeks . org/如何在安卓中创建不带额外活动的闪屏/](https://www.geeksforgeeks.org/how-to-create-splash-screen-without-an-extra-activity-in-android/)

初始屏幕是应用程序打开时的第一个屏幕。它用于在应用程序完全加载之前显示一些基本的介绍性信息，如公司徽标、内容等。在本文中，我们将遵循最佳实践来创建一个闪屏，该闪屏不需要为其创建额外的活动，一旦活动加载，它就会消失。下面是一个示例视频，展示了我们将要构建的内容。这个项目可以使用 **Java/Kotlin** 。

<video class="wp-video-shortcode" id="video-644139-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210713002246/splash_screen_without_an_extra_activity_gfg.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210713002246/splash_screen_without_an_extra_activity_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210713002246/splash_screen_without_an_extra_activity_gfg.mp4)</video>

> **注:**
> 
> *   用 Java 创建闪屏:[创建闪屏](https://www.geeksforgeeks.org/android-creating-a-splash-screen/)
> *   要在 Kotlin 中创建闪屏:[如何使用 Kotlin 在安卓中创建闪屏？](https://www.geeksforgeeks.org/how-to-create-a-splash-screen-in-android-using-kotlin/)
> *   创建动画闪屏:[如何在安卓中创建动画闪屏？](https://www.geeksforgeeks.org/how-to-create-an-animated-splash-screen-in-android/)

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。可以选择 **Kotlin/Java** 作为编程语言。

**步骤 2:创建一个新的可绘制文件，并将其命名为“splash _ image . XML”**

转到**RES->drawing->splash _ image . XML**和以下代码。添加注释。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <!--Add the following code
        add the drawable color to white-->
    <item android:drawable="@color/white"/>
    <!--Add the logo that you want to display and its gravity to centre-->
    <item android:drawable="@drawable/gfg_logo" android:gravity="center"/>
</layer-list>
```

**第三步:在 themes.xml 文件**中添加新样式

转到**RES->values->themes . XML**添加一个新样式，并将其命名为“**splasshscreen theme**”。这将保存我们想要在闪屏上显示的信息，如**窗口背景**和**状态栏颜色**。

## 可扩展标记语言

```kt
<resources xmlns:tools="http://schemas.android.com/tools">

    <!--Create a new style and name it splashScreenTheme and add the following code-->
    <style name="splashScreenTheme" parent="Theme.MaterialComponents.Light.NoActionBar">
        <item name="android:windowBackground">@drawable/splash_image</item>
        <item name="android:statusBarColor">@color/black</item>
    </style>

    <!-- Default Code do not change it. 
         we will use it as our theme after
          the aplash screen is shown-->
    <!-- Base application theme -->
    <style name="Theme.SplashAPIGFG" parent="Theme.MaterialComponents.DayNight.NoActionBar">
        <!-- Primary brand color-->
        <item name="colorPrimary">#2F8D46</item>
        <item name="colorPrimaryVariant">#2F8D46</item>
        <item name="colorOnPrimary">@color/white</item>
        <!-- Secondary brand color. -->
        <item name="colorSecondary">#2F8D46</item>
        <item name="colorSecondaryVariant">@color/teal_700</item>
        <item name="colorOnSecondary">@color/black</item>
        <!-- Status bar color. -->
        <item name="android:statusBarColor" tools:targetApi="l">?attr/colorPrimaryVariant</item>
        <!-- Customize your theme here. -->
    </style>

</resources>
```

**第四步:将样式添加到清单文件**

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.introidx.splashapigfg">

    <!--In the theme add the style that we just created-->
    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/splashScreenTheme"> 
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

**步骤 5:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 MainActivity.kt 文件的代码。这里设置我们希望在闪屏显示后显示的主题。

## 我的锅

```kt
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

          // add the default theme here which we want 
          // to display after the splash screen is shown
        setTheme(R.style.Theme_SplashAPIGFG)
        setContentView(R.layout.activity_main)
    }
}
```

**注意:activity_main.xml** 文件只是有一个显示消息的 Text View。

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

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="This is test app for Splash Screen"
        app:layout_constraintBottom_toBottomOf="parent"
        android:textStyle="bold"
        android:textSize="22sp"
        android:textColor="@color/black"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**输出:**

<video class="wp-video-shortcode" id="video-644139-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210713002246/splash_screen_without_an_extra_activity_gfg.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210713002246/splash_screen_without_an_extra_activity_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210713002246/splash_screen_without_an_extra_activity_gfg.mp4)</video>