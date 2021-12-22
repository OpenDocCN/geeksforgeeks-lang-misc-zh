# 如何使用 Kotlin 在安卓系统中创建选项菜单？

> 原文:[https://www . geesforgeks . org/how-create-option-in-Android-use-kot Lin/](https://www.geeksforgeeks.org/how-to-create-option-menu-in-android-using-kotlin/)

在本文中，我们将学习如何使用 Kotlin 在安卓应用程序中创建选项菜单。为了在活动中有一个选项菜单，我们需要创建一个新的菜单 XML 文件，并使用*菜单编辑器*对其进行膨胀。充气( )方法。在 menu.xml 中，我们将根据应用程序的要求设计选项菜单。

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:执行选项菜单**

我们需要创建一个新的菜单 XML 文件，使用<item>标签，我们可以在菜单内创建项目。</item>

**第三步:为菜单选项**中的项目图标创建矢量资产

[矢量资产](https://www.geeksforgeeks.org/how-to-add-vector-assets-in-android-studio/)参考本链接。

**第四步:菜单. xml 文件参考该代码**

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <item
        android:id="@+id/overflowMenu"
        android:icon="@drawable/ic_3_dots"
        android:title=""
        app:showAsAction="always">
        <menu>
            <item
                android:id="@+id/settings"
                android:icon="@drawable/ic_settings"
                android:title="SETTINGS"
                app:showAsAction="never" />
            <item
                android:id="@+id/about"
                android:icon="@drawable/ic_about"
                android:title="ABOUT"
                app:showAsAction="never" />
            <item
                android:id="@+id/exit"
                android:icon="@drawable/ic_exit"
                android:title="EXIT"
                app:showAsAction="never" />
        </menu>
    </item>
</menu>
```

**步骤 5:使用**T2【主活动. kt】文件

我们不需要更改 **activity_main.xml** 文件中的任何内容。转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。

## 我的锅

```kt
package com.ayush.optionmenu

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.Menu
import android.view.MenuItem
import android.widget.Toast

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }

    override fun onCreateOptionsMenu(menu: Menu?): Boolean {
        menuInflater.inflate(R.menu.menu,menu)
        return super.onCreateOptionsMenu(menu)
    }

    override fun onOptionsItemSelected(item: MenuItem): Boolean {
        when (item.itemId){
            R.id.about -> Toast.makeText(this,"About Selected",Toast.LENGTH_SHORT).show()
            R.id.settings -> Toast.makeText(this,"Settings Selected",Toast.LENGTH_SHORT).show()
            R.id.exit -> Toast.makeText(this,"Exit Selected",Toast.LENGTH_SHORT).show()
        }
        return super.onOptionsItemSelected(item)
    }
}
```

所以我们的应用已经准备好了。

**输出:**

我们可以看到，当我们点击任何菜单选项时，都会显示一个吐司。

<video class="wp-video-shortcode" id="video-690055-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210930141514/video_2021-09-30_14-12-51.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210930141514/video_2021-09-30_14-12-51.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210930141514/video_2021-09-30_14-12-51.mp4)</video>