# 安卓如何禁用 GridView 滚动？

> 原文:[https://www . geesforgeks . org/如何禁用-GridView-在安卓中滚动/](https://www.geeksforgeeks.org/how-to-disable-gridview-scrolling-in-android/)

一个[网格视图](https://www.geeksforgeeks.org/gridview-in-android-with-example/)是一个视图组，它可以以类似网格的结构显示来自对象或数据库列表的数据，该结构由行和列组成。网格视图需要一个适配器来从资源中获取数据。该视图可以水平和垂直滚动。默认情况下，GridView 的滚动功能设置为启用。

![](img/6ecfea9ad67f1dda2025baa43c41af9b.png)

然而，在本文中，我们将展示如何禁用 GridView 的滚动功能。

### 逐步实施

**第一步:在安卓工作室新建项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在**科特林**中演示了该应用程序，因此在创建新项目时，请确保选择科特林作为主要语言。

**步骤 2:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。在布局中创建这个简单的 GridView。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="8dp"
    tools:context=".MainActivity">

    <GridView
        android:id="@+id/gridLayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />

</RelativeLayout>
```

**步骤 3:为网格视图创建适配器(MyGridViewAdapter.kt)**

我们必须创建一个适配器来将数据(在我们的例子中是图像)发送到网格视图。所以，创建一个新的类并给它一个相关的名字。要查看我们是如何添加这些照片的，请参考**第 6 步**。

## 我的锅

```
import android.content.Context
import android.view.View
import android.view.ViewGroup
import android.widget.AbsListView
import android.widget.BaseAdapter
import android.widget.ImageView

// Array of Images, 
// we used GeeksforGeeks logo
private val myImages = arrayOf(
    R.drawable.logo,
    R.drawable.logo,
    R.drawable.logo,
    R.drawable.logo,
    R.drawable.logo,
    R.drawable.logo,
    R.drawable.logo,
)

class MyGridViewAdapter constructor(c:Context): BaseAdapter() {
    private val context: Context = c

    override fun getCount(): Int {
        return myImages.size
    }

    override fun getItem(position: Int): Any? {
        return null
    }

    override fun getItemId(position: Int): Long {
        return 0
    }

    override fun getView(position: Int, convertView: View?, parent: ViewGroup?): View {
        val imageView: ImageView

        if (convertView == null) {
            imageView = ImageView(context)
            imageView.layoutParams = AbsListView.LayoutParams(
                ViewGroup.LayoutParams.WRAP_CONTENT,
                ViewGroup.LayoutParams.WRAP_CONTENT
            )
            imageView.scaleType = ImageView.ScaleType.CENTER_CROP
            imageView.setPadding(30, 30, 30, 30)
        }
        else {
            imageView = convertView as ImageView
        }

        imageView.setImageResource(myImages[position])

        return imageView
    }
}
```

**第 4 步:使用**T2【主活动. kt】文件

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。在主代码中将适配器链接到网格视图。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.annotation.SuppressLint
import android.content.Context
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.MotionEvent
import android.view.View
import android.view.ViewGroup
import android.widget.*

class MainActivity : AppCompatActivity() {

    @SuppressLint("ClickableViewAccessibility")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declare the GridView from the layout
        val gridView = findViewById<GridView>(R.id.gridLayout)

        // Specify number of columns
        gridView.numColumns = 1

        // Setting the grid view 
        // adapter as MyGridViewAdapter
        gridView.adapter = MyGridViewAdapter(this)
    }
}
```

**输出:现在运行应用程序**

您可以看到我们能够垂直滚动 GridView。

<video class="wp-video-shortcode" id="video-651988-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210722201241/3231.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210722201241/3231.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210722201241/3231.mp4)</video>

**第五步:在主代码中添加该代码，禁用滚动(MainActivity.kt)**

## 我的锅

```
import android.annotation.SuppressLint
import android.content.Context
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.MotionEvent
import android.view.View
import android.view.ViewGroup
import android.widget.*

class MainActivity : AppCompatActivity() {

    @SuppressLint("ClickableViewAccessibility")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val gridView = findViewById<GridView>(R.id.gridLayout)
        gridView.numColumns = 1
        gridView.adapter = MyGridViewAdapter(this)

        // What should happen when 
        // the Grid View is touched
        gridView.setOnTouchListener { _, event ->

            // A Toast is generated for every touch and 
            // event action is set as ACTION_MOVE
            Toast.makeText(applicationContext, "Scrolling is Disabled", Toast.LENGTH_SHORT).show()
            event.action == MotionEvent.ACTION_MOVE
        }
    }
}
```

**输出:运行应用程序**

您可以看到我们无法垂直滚动网格视图。

<video class="wp-video-shortcode" id="video-651988-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210722201239/3241.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210722201239/3241.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210722201239/3241.mp4)</video>

**注意:**可以在资源中添加下图

![](img/b04ab927a5fd467424603e53ed44ee31.png)

从互联网下载的图像

现在只需将其复制粘贴到 **res** 文件夹中的 **Drawables** 文件夹中。命名它们并点击**确定**。