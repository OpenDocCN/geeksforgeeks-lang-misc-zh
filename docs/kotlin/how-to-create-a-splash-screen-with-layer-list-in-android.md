# 如何在安卓中创建带图层列表的闪屏？

> 原文:[https://www . geeksforgeeks . org/如何在安卓中创建带图层列表的闪屏/](https://www.geeksforgeeks.org/how-to-create-a-splash-screen-with-layer-list-in-android/)

[闪屏](https://www.geeksforgeeks.org/how-to-create-a-splash-screen-in-android-using-kotlin/)是应用程序启动时显示的初始屏幕。所以要么在屏幕启动时显示你的徽标，要么显示你的应用程序的名称。类似于 WhatsApp 或 Instagram 应用在发布时的做法。他们展示了一个简单的应用标志。现在，问题来了，要做到这一点，您需要创建一个启动器活动，在该活动中，为了显示您的内容，您将使用 XML。该 XML 代码被添加到 **onCreate()** 方法的 **setContentView()** 上的活动类中。所以在启动时，因为 **onCreate()** 方法被认为是一个繁重的过程。在应用程序中加载我们的 XML 代码的时间太长了，在此之前，启动时会出现一个空白屏幕，这就是所谓的冷启动。为了避免这个空白屏幕，您可以使用另一种方法，使用一个层列表，并在清单中使用它作为主题。

> **注意:**在开始之前，创建一个启动器活动并删除该活动的 XML 文件，因为我们不打算在类中使用 onCreate 方法。

让我们从实际部分开始。

**步骤 1:创建可绘制资源**

在要添加闪屏内容的位置添加新的可绘制资源。转到 res 目录->可绘制->您的 _ splashScreenDrawable.xml

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item>  <!-- Add Background color as per your necessity-->
        <color android:color="@color/your_favoriteBackgroundColor" />
    </item>
    <item>
       <!-- Add Bitmap with gravity as center to align the content in center -->
        <bitmap 
            android:gravity="center"
            android:src="@drawable/yourDrawableResourceFile" />
    </item>
</layer-list>
```

在这个代码片段中，您将使用**层列表**中的项目标签。这些物品标签有特定的属性来满足你的需求。所以这个片段将成为启动屏幕，它包含一个带有背景色的位图。

**第二步:将可绘制资源添加到 styles.xml 中**

## 可扩展标记语言

```kt
<style name="yourThemeName" parent="AppTheme">
  <item name="android:windowBackground">@drawable/yourDrawableFileName</item>
  <item name="android:windowFullscreen">true</item>
</style>
```

而**style . XML**中的这段代码将为闪屏增加额外的属性，比如全屏等等。在这个属性中，android:windowBackground 将添加可绘制的资源作为屏幕背景。

**第三步:在 MainActivity.kt 文件**中处理闪屏显示时间

## 我的锅

```kt
class MainActivity:AppCompatActivty(){  

private val mHandler = Handler(Looper.getMainLooper()) 
private val mLauncher: Launcher = Launcher()
    override fun onStart() {
        super.onStart()
        mHandler.postDelayed(mLauncher, SPLASH_DELAY.toLong())
    }

    override fun onStop() {
        mHandler.removeCallbacks(mLauncher)
        super.onStop()
    }

    private fun launch() {
        if (!isFinishing) {
               startActivity(Intent(this@MainActivity, AnotherActivity::class.java))
            finish()
        }
    }

    private inner class Launcher : Runnable {
        override fun run() {
            launch()
        }
    }

    companion object {
        private const val SPLASH_DELAY = 2000
        private const val TAG = "MainActivity"
    }
}
```

现在这个代码是主要部分，因为它处理屏幕显示时间。这里有一个扩展 Runnable 的启动器类，它被处理程序对象延迟，当延迟时间结束时，启动器进入另一个活动。现在，剩下的关键部分在应用程序的清单文件中。

**第四步:在清单文件**中使用样式作为主题

转到清单目录->打开 AndroidManifest.xml。在清单文件中，在您的活动标签中添加一个主题属性，您将在该属性中添加这个可绘制的作为应用程序中的主题。

## 可扩展标记语言

```kt
<activity
  android:name=".MainActivity"
  android:theme="@style/yourDrawableTheme">
    <intent-filter>
      <category android:name="android.intent.category.DEFAULT" />
      <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```