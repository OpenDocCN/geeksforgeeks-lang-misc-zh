# 如何在安卓中用 RecyclerView 创建折叠工具栏和卷轴上的 FAB？

> 原文:[https://www . geeksforgeeks . org/如何使用 android 中的 recyclerview 创建一个折叠工具栏和滚动 fab/](https://www.geeksforgeeks.org/how-to-create-a-collapsing-toolbar-and-fab-on-scroll-with-recyclerview-in-android/)

在本文中，我们将使用[循环查看](https://www.geeksforgeeks.org/android-recyclerview/)在滚动中创建一个折叠工具栏和浮动操作按钮。许多流行的应用程序都有这种效果，例如 LinkedIn。下面是展示我们将要构建的内容的示例视频。请注意，我们将使用**柯特林**语言来实现这个项目。

<video class="wp-video-shortcode" id="video-643350-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210710002532/collapsing_toolbar_and_fab_gfg.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210710002532/collapsing_toolbar_and_fab_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210710002532/collapsing_toolbar_and_fab_gfg.mp4)</video>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:添加视图绑定依赖关系**

转到 android 标签内的 build.gradle(app)和以下依赖项，点击**立即同步。**

> 构建功能{
> 
> 视图绑定为真
> 
> }

**步骤 3:使用 activity_main.xml 文件**

转到 **activity_main.xml** 文件，参考以下代码。下面是 **activity_main.xml** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<!--first of all you have to change
    the layout as CoordinatorLayout.-->
<androidx.coordinatorlayout.widget.CoordinatorLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--First child of CoordinatorLayout layout
         should be App Bar Layout-->
    <com.google.android.material.appbar.AppBarLayout
        android:id="@+id/appBarLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar">

        <!-- Add Material toolbar make the layout_scrollFlags
              to scroll|enterAlways (Important)-->
        <com.google.android.material.appbar.MaterialToolbar
            android:id="@+id/toolbar"
            android:layout_width="match_parent"
            android:layout_height="?attr/actionBarSize"
            app:layout_scrollFlags="scroll|enterAlways"
            app:title="@string/app_name" />

    </com.google.android.material.appbar.AppBarLayout>

    <!--Add a recycler view
        inside layout behaviour add "@string/appbar_scrolling_view_behavior" (Important)
        by default it comes from the @string-->
    <androidx.recyclerview.widget.RecyclerView
        android:id="@+id/recyclerView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="#F5F8FD"
        android:orientation="vertical"
        android:padding="5dp"
        app:layoutManager="androidx.recyclerview.widget.LinearLayoutManager"
        app:layout_behavior="@string/appbar_scrolling_view_behavior" />

    <!--Add a floating action button
        "com.google.android.material.behavior.HideBottomViewOnScrollBehavior" (Important)-->
    <com.google.android.material.floatingactionbutton.FloatingActionButton
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="bottom|right"
        android:layout_margin="16dp"
        android:src="@drawable/ic_baseline_add_24"
        app:fabSize="normal"
        app:layout_behavior="com.google.android.material.behavior.HideBottomViewOnScrollBehavior"
        app:tint="@android:color/white" />

</androidx.coordinatorlayout.widget.CoordinatorLayout>
```

**第四步:新建一个布局文件，命名为 single_item.xml 文件**

转到 **single_item.xml** 文件，参考以下代码。下面是 **single_item.xml** 文件的代码。这是我们将在回收视图中使用的单一项目布局。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<com.google.android.material.card.MaterialCardView
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_marginBottom="10dp"
    android:layout_marginStart="5dp"
    android:layout_marginEnd="5dp"
    android:layout_height="110dp">

    <androidx.constraintlayout.widget.ConstraintLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <!--Add image view, We will not set any data here.-->
        <ImageView
            android:id="@+id/iv_language"
            android:layout_width="80dp"
            android:layout_height="90dp"
            android:layout_marginStart="20dp"
            android:layout_marginTop="10dp"
            android:scaleType="fitCenter"
            android:src="@mipmap/ic_launcher"
            app:layout_constraintLeft_toLeftOf="parent"
            app:layout_constraintTop_toTopOf="parent" />

        <!--Text view for showing the language name-->
        <TextView
            android:id="@+id/tv_lang_name"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginStart="30dp"
            android:layout_marginTop="30dp"
            android:text="Language"
            android:textSize="16sp"
            android:textStyle="bold"
            app:layout_constraintLeft_toRightOf="@id/iv_language"
            app:layout_constraintTop_toTopOf="parent" />

        <!--Text View for showing the exp-->
        <TextView
            android:id="@+id/tv_exp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="Exp : 3 years"
            app:layout_constraintLeft_toLeftOf="@id/tv_lang_name"
            app:layout_constraintTop_toBottomOf="@id/tv_lang_name" />

    </androidx.constraintlayout.widget.ConstraintLayout>

</com.google.android.material.card.MaterialCardView>
```

**第五步:新建模型类**

创建一个新的类 **Language.kt** 我们将使用自定义通用“Language”的数据来传入将在回收器视图中显示的列表。

## 我的锅

```kt
// this is the Language model class
class Language(
    val name : String ="",
    val exp : String = ""
)
```

**步骤 6:使用适配器类**

创建一个新类 **RvAdapter.kt** 这将作为回收视图的适配器类。为了更好地理解，在代码前添加了注释。

## 我的锅

```kt
import android.view.LayoutInflater
import android.view.ViewGroup
import androidx.recyclerview.widget.RecyclerView
import com.introidx.collapsingtoolbargfg.databinding.SingleItemBinding

class RvAdapter(
    private var languageList: List<Language>) : RecyclerView.Adapter<RvAdapter.ViewHolder>() {

    // create an inner class with name ViewHolder
    // It takes a view argument, in which pass the 
    // generated class of single_item.xml
    // ie SingleItemBinding and in the 
    // RecyclerView.ViewHolder(binding.root) pass it like this
    inner class ViewHolder(val binding: SingleItemBinding) : RecyclerView.ViewHolder(binding.root)

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val binding = SingleItemBinding.inflate(LayoutInflater.from(parent.context), parent, false)
        return ViewHolder(binding)
    }

    // bind the items with each item of 
    // the list languageList which than will be
    // shown in recycler view
    // to keep it simple we are not 
    // setting any image data to view
    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        with(holder) {
            with(languageList[position]) {
                // set text to language name
                binding.tvLangName.text = this.name
                // set exp
                binding.tvExp.text = this.exp
            }
        }
    }

    // return the size of languageList
    override fun getItemCount(): Int {
        return languageList.size
    }
}
```

**第 7 步:使用 MainActivity.kt**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import androidx.recyclerview.widget.LinearLayoutManager
import com.introidx.collapsingtoolbargfg.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {

    // view binding for the activity
    private var _binding: ActivityMainBinding? = null
    private val binding get() = _binding!!

    // get reference to the adapter class
    private var languageList = ArrayList<Language>()
    private lateinit var rvAdapter: RvAdapter

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        _binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)

        // define layout manager for the Recycler view
        binding.recyclerView.layoutManager = LinearLayoutManager(this)

        // attach adapter to the recycler view and also handle item click

        // attach adapter to the recycler view
        rvAdapter = RvAdapter(languageList)

        // add adapter to the recycler view
        binding.recyclerView.adapter = rvAdapter

        // create objects of Language
        // create some row data
        val language1 = Language("Java", "3 Year exp")
        val language2 = Language("Kotlin", "2 Year exp")
        val language3 = Language("Python", "1 Year exp")
        val language4 = Language("CPP", "5 Year exp")
        val language5 = Language("PHP", "No exp")

        // pass raw data t rhe list
        languageList.add(language1)
        languageList.add(language2)
        languageList.add(language3)
        languageList.add(language4)
        languageList.add(language5)
        languageList.add(language3)
        languageList.add(language4)
        languageList.add(language5)
        languageList.add(language3)
        languageList.add(language4)
        languageList.add(language5)

        rvAdapter.notifyDataSetChanged()

    }

    // on destroy of view make the 
      // binding reference to null
    override fun onDestroy() {
        super.onDestroy()
        _binding = null
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-643350-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210710002532/collapsing_toolbar_and_fab_gfg.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210710002532/collapsing_toolbar_and_fab_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210710002532/collapsing_toolbar_and_fab_gfg.mp4)</video>