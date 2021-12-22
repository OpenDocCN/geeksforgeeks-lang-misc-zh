# 带 Kotlin 的安卓 Chrome 自定义标签

> 原文:[https://www . geesforgeks . org/chrome-custom-tab-in-Android-with-kot Lin/](https://www.geeksforgeeks.org/chrome-custom-tabs-in-android-with-kotlin/)

作为开发人员，我们可以选择在用户的浏览器中或通过[webview](https://www.geeksforgeeks.org/android-webview-in-kotlin/)向用户显示 web 内容，但两者都有自己的局限性:启动浏览器对用户来说是一个大的、不可定制的上下文转换，而 webview 并不支持 web 平台的所有方面。为了解决这个问题，谷歌推出了 chrome 定制标签。这是一项浏览器功能，它为应用程序提供了对其网络体验的更多控制，并支持在不使用网络视图的情况下在本地和网络内容之间进行更无缝的转换。它们允许开发人员改变浏览器的外观和感觉。它提供了许多优势和定制:

*   能够更改工具栏颜色
*   添加进入和退出动画
*   启用内容共享
*   向浏览器工具栏和溢出菜单添加自定义操作
*   优化性能

### **本文我们要构建什么？**

在本文中，我们将使用 Chrome 自定义标签向用户显示网页内容。为了让您了解我们将在本文中做什么，这里有一个示例视频。

<video class="wp-video-shortcode" id="video-670108-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210815144335/chrometabs.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210815144335/chrometabs.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210815144335/chrometabs.mp4)</video>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:添加库依赖**

导航到**Gradle Scripts>build . Gradle(模块:** **app)** ，在依赖项部分添加库，并同步项目。

```kt
dependencies {
      implementation 'androidx.browser:browser:1.3.0'
}
```

**步骤 3:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

      <!--Adding a button-->
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/button"
        android:layout_centerInParent="true"
        android:padding="15dp"
        android:text="Open Custom Chrome Tabs"
        android:textColor="#0F9D58"/>

</RelativeLayout>
```

**第 4 步:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。添加注释是为了更详细地理解代码。

## 我的锅

```kt
import android.content.Context
import android.content.pm.PackageManager
import android.net.Uri
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import androidx.browser.customtabs.*
import androidx.core.content.ContextCompat
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {

    private var GFG_URI = "https://www.geeksforgeeks.org"
    private var package_name = "com.android.chrome";

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        button.setOnClickListener {

            val builder = CustomTabsIntent.Builder()

            // to set the toolbar color use CustomTabColorSchemeParams
            // since CustomTabsIntent.Builder().setToolBarColor() is deprecated

            val params = CustomTabColorSchemeParams.Builder()
            params.setToolbarColor(ContextCompat.getColor(this@MainActivity, R.color.colorPrimary))
            builder.setDefaultColorSchemeParams(params.build())

            // shows the title of web-page in toolbar
            builder.setShowTitle(true)

            // setShareState(CustomTabsIntent.SHARE_STATE_ON) will add a menu to share the web-page
            builder.setShareState(CustomTabsIntent.SHARE_STATE_ON)

            // To modify the close button, use
            // builder.setCloseButtonIcon(bitmap)

            // to set weather instant apps is enabled for the custom tab or not, use
            builder.setInstantAppsEnabled(true)

            //  To use animations use -
            //  builder.setStartAnimations(this, android.R.anim.start_in_anim, android.R.anim.start_out_anim)
            //  builder.setExitAnimations(this, android.R.anim.exit_in_anim, android.R.anim.exit_out_anim)
            val customBuilder = builder.build()

            if (this.isPackageInstalled(package_name)) {
                // if chrome is available use chrome custom tabs
                customBuilder.intent.setPackage(package_name)
                customBuilder.launchUrl(this, Uri.parse(GFG_URI))
            } else {
                // if not available use WebView to launch the url
            }
        }
    }
}

fun Context.isPackageInstalled(packageName: String): Boolean {
    // check if chrome is installed or not
    return try {
        packageManager.getPackageInfo(packageName, 0)
        true
    } catch (e: PackageManager.NameNotFoundException) {
        false
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-670108-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210815144335/chrometabs.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210815144335/chrometabs.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210815144335/chrometabs.mp4)</video>

**项目链接:** [点击此处](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20210829235251/GFGChromeCustomTabs-master.zip)