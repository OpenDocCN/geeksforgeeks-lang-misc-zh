# 在安卓中用可视寻呼机缩放动画中的立方体

> 原文:[https://www . geesforgeks . org/cube-in-scaling-animation-with-view-pager-in-Android/](https://www.geeksforgeeks.org/cube-in-scaling-animation-with-viewpager-in-android/)

安卓可视寻呼机已经成为安卓应用中一个非常有趣的概念。它使用户能够在具有公共用户界面的片段之间平滑切换，这是让您的应用程序与众不同的最佳方式。可视寻呼机提供视觉连续性。他们基本上跟踪哪个页面是可见的，然后要求页面适配器显示层次结构中的下一个页面。不仅如此，它甚至允许你创建各种令人敬畏的幻灯片效果和动画！

### **本文我们要构建什么？**

在本文中，我们将使用 ViewPager 实现缩放立方体动画。下面给出了一个示例 GIF，以了解我们将在本文中做什么。注意，我们将使用 **Kotlin** 语言来实现这个项目。

![](img/ef5c225e2301987aaa9597598be0f622.png)

完整实现可视寻呼机有 3 个基本组件:

*   一个包含可视寻呼机和主要用户界面的[活动](https://www.geeksforgeeks.org/introduction-to-activities-in-android/)。
*   一组[片段](https://www.geeksforgeeks.org/introduction-fragments-android/)，在可视寻呼机中作为单独的页面查看。
*   [片段页面适配器](https://developer.android.com/reference/androidx/fragment/app/FragmentPagerAdapter)或[片段状态页面适配器](https://developer.android.com/reference/androidx/fragment/app/FragmentStatePagerAdapter)返回下一个需要显示的正确片段。

例如，参考文章–[用示例](https://www.geeksforgeeks.org/viewpager-using-fragments-in-android-with-example/)在安卓中使用片段查看寻呼机。

### **分步实施**

这里，我们将使用 ViewPager 制作一个图像滑块，然后应用缩放立方体动画。

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:设计 UI**

下面是 **activity_main.xml** 文件的代码。我们只添加了一个可视寻呼机来显示图像。下面是 **activity_main.xml 文件**的完整代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!-- viewpager to show images -->
    <androidx.viewpager.widget.ViewPager
        android:id="@+id/viewPagerMain"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

现在，在**应用程序> res >布局**文件夹内创建一个新的布局资源文件 **item.xml** 。下面是 **item.xml** 文件的代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- image viewer to view the images -->
    <ImageView
        android:id="@+id/imageViewMain"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_margin="10dp"
        android:contentDescription="image" />

</LinearLayout>
```

**第三步:使用 ViewPagerAdapter.kt 和 MainActivity.kt 文件**

首先，创建一个**视图页面适配器**类，一个视图页面适配器。下面是**viewpageadapter . kt**类的完整代码。注释被添加到代码中，以理解代码的每一行。

## 我的锅

```
import android.content.Context
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.ImageView
import android.widget.LinearLayout
import androidx.viewpager.widget.PagerAdapter
import java.util.*

internal class ViewPagerAdapter(private val context: Context, private val images: IntArray) : PagerAdapter() {

    // Layout Inflater
    var mLayoutInflater: LayoutInflater
    override fun getCount(): Int {
        // return the number of images
        return images.size
    }

    init {
        mLayoutInflater = context.getSystemService(Context.LAYOUT_INFLATER_SERVICE) as LayoutInflater
    }

    override fun isViewFromObject(view: View, `object`: Any): Boolean {
        return view === `object` as LinearLayout
    }

    override fun instantiateItem(container: ViewGroup, position: Int): Any {

        // inflating the item.xml
        val itemView: View = mLayoutInflater.inflate(R.layout.item, container, false)

        // referencing the image view from the item.xml file
        val imageView: ImageView = itemView.findViewById(R.id.imageViewMain)

        // setting the image in the imageView
        imageView.setImageResource(images[position])

        // Adding the View
        Objects.requireNonNull(container).addView(itemView)
        return itemView
    }

    override fun destroyItem(container: ViewGroup, position: Int, `object`: Any) {
        container.removeView(`object` as LinearLayout)
    }
}
```

下面是 **MainActivity.kt** 文件的完整代码。注释被添加到代码中，以理解代码的每一行。

## 我的锅

```
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import androidx.viewpager.widget.ViewPager

class MainActivity : AppCompatActivity() {

    // creating object of ViewPager
    lateinit var mViewPager: ViewPager

    // images array
    private var images = intArrayOf(R.drawable.a1, R.drawable.a2, R.drawable.a3, R.drawable.a4)

    // Creating Object of ViewPagerAdapter
    private lateinit var mViewPagerAdapter: ViewPagerAdapter

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Initializing the ViewPager Object
        mViewPager = findViewById(R.id.viewPagerMain)

        mViewPager.setPageTransformer(true, CubeInScalingAnimation())

        // Initializing the ViewPagerAdapter
        mViewPagerAdapter = ViewPagerAdapter(this@MainActivity, images)

        // Adding the Adapter to the ViewPager
        mViewPager.adapter = mViewPagerAdapter
    }
}
```

**第四步:**新建一个类**立方体缩放动画。以下是**cubeinscalanimation . kt**文件的完整代码。注释被添加到代码中，以理解代码的每一行。**

## 我的锅

```
import android.view.View
import androidx.viewpager.widget.ViewPager
import kotlin.math.abs

class CubeInScalingAnimation : ViewPager.PageTransformer {

    override fun transformPage(page: View, position: Float) {
        page.cameraDistance = 20000F
        when {
            position < -1 -> {   //{-infinity,-1}
                // page offset to left side
                page.alpha = 0F
            }
            position <= 0 -> {
                // transition from left 
                // side of page to current page
                page.alpha = 1F
                page.pivotX = page.width.toFloat()
                page.rotationY = 90F * abs(position)
            }
            position <= 1 -> {
                // transition form current 
                // page to right side
                page.alpha = 1F
                page.pivotX = 0F
                page.rotationY = -90F * abs(position)
            }
            //{1,+infinity}
            else -> { //Page offset to right side
                page.alpha = 0F
            }
        }

        when {
            // transition between page1 and page2
            abs(position) <= 0.5 -> {
                page.scaleY = Math.max(0.4f, 1 - abs(position))
            }
            abs(position) <= 1 -> {
                page.scaleY = Math.max(0.4f, abs(position))
            }
        }
    }
}
```

现在，运行应用程序

**输出:**

<video class="wp-video-shortcode" id="video-670112-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210820132940/CubeInAnimationViewPager.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210820132940/CubeInAnimationViewPager.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210820132940/CubeInAnimationViewPager.mp4)</video>

**源代码:** [点击此处](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20210830131659/Cube-In-Scaling-Animmation-GFG-article-main.zip)