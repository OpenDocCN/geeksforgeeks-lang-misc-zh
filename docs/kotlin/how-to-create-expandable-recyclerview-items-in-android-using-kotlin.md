# 如何使用 Kotlin 在安卓中创建可扩展的 RecyclerView 项目？

> 原文:[https://www . geeksforgeeks . org/how-create-expandable-recycle view-items-in-Android-use-kot Lin/](https://www.geeksforgeeks.org/how-to-create-expandable-recyclerview-items-in-android-using-kotlin/)

[【recycle view】](https://www.geeksforgeeks.org/android-recyclerview/)是作为 GridView 和 ListView 的继承者加入安卓工作室的一个视图组。这是对两者的改进，可以在最新的 v-7 支持包中找到。它的创建是为了能够将任何带有 **XML** 布局的列表构建为一个项目，这样就可以进行大量定制，而 *则提高了列表视图和网格视图* 的效率。这种改进是通过回收用户不可见的视图来实现的。例如，如果用户向下滚动到项目 4 和 5 可见的位置；项目 1、2 和 3 将从内存中清除，以减少内存消耗。在本文中，我们将解释如何在 android 中创建可扩展的 Recycler View 项目。下面是展示我们将要构建的内容的示例视频。注意，我们将使用 **Kotlin** 语言来实现这个项目。

<video class="wp-video-shortcode" id="video-578854-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210323135218/expandable_rv_android_gfg.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210323135218/expandable_rv_android_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210323135218/expandable_rv_android_gfg.mp4)</video>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:添加视图绑定依赖关系**

转到 **build.gradle(app)** 和安卓标签内的以下依赖项，点击**立即同步。**

> 构建功能{
> 
> 视图绑定为真
> 
> }

**步骤 3:使用 activity_main.xml**

转到 **activity_main.xml** 文件，参考以下代码。下面是 **activity_main.xml** 文件的代码。它只有一个回收视图，我们将使用它来显示我们的数据。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:background="#F5F8FD"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!--Add recycler view to main activity-->
    <androidx.recyclerview.widget.RecyclerView
        android:id="@+id/rv_list"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:listitem="@layout/single_item"
        app:layoutManager="androidx.recyclerview.widget.LinearLayoutManager" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**第四步:新建布局文件，命名为 single_item.xml 文件**

转到 **single_item.xml** 文件，参考以下代码。下面是 **single_item.xml** 文件的代码。这是我们将在回收视图中使用的单一项目布局。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<com.google.android.material.card.MaterialCardView 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/card_layout"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_marginStart="5dp"
    android:layout_marginEnd="5dp"
    android:layout_marginBottom="10dp">

    <androidx.constraintlayout.widget.ConstraintLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <!--Text view for showing the language name-->
        <TextView
            android:id="@+id/tv_lang_name"
            android:layout_width="wrap_content"
            android:layout_height="40dp"
            android:layout_marginStart="20dp"
            android:layout_marginTop="10dp"
            android:text="Language"
            android:textColor="@color/black"
            android:textSize="20sp"
            android:textStyle="bold"
            app:layout_constraintLeft_toLeftOf="parent"
            app:layout_constraintTop_toTopOf="parent" />

        <!--This is the layout "expanded_view" we will 
            hide initially and show as expanded
            layout when user clicks on any of the item-->
        <RelativeLayout
            android:id="@+id/expanded_view"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            app:layout_constraintLeft_toLeftOf="parent"
            app:layout_constraintRight_toRightOf="parent"
            app:layout_constraintTop_toBottomOf="@id/tv_lang_name">

            <!--It has a text view which we will use in our case as
                a description text for the languages-->
            <TextView
                android:id="@+id/tv_description"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_margin="10dp"
                android:text="Description Text"
                android:textSize="18sp" />
        </RelativeLayout>

    </androidx.constraintlayout.widget.ConstraintLayout>

</com.google.android.material.card.MaterialCardView>
```

**第五步:新建模型类**

创建一个新的类 **Language.kt** 我们将使用自定义通用“**语言**的数据来传入将在 RecyclerView 中显示的列表。

## 我的锅

```kt
// this is the Language model class
class Language(
    val name : String ="",
    val description : String= "",
    var expand : Boolean = false
)
```

**步骤 6:使用适配器类**

创建一个新类 **RvAdapter.kt** 这将作为回收视图的适配器类。可扩展回收器视图背后的逻辑是，最初，我们将使 id 为“**的布局的可见性从“ **single_item.xm** l”扩展到 **GONE** ，一旦用户点击回收器视图的任何项目，我们将使其可见性**可见。**为了更好的理解，代码前增加了注释。**

## 我的锅

```kt
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import androidx.recyclerview.widget.RecyclerView
import com.geeksforgeeks.rvadapterviewbinding.databinding.SingleItemBinding

class RvAdapter(
    private var languageList: List<Language>
) : RecyclerView.Adapter<RvAdapter.ViewHolder>() {

    // create an inner class with name ViewHolder
    // It takes a view argument, in which pass the generated class of single_item.xml
    // ie SingleItemBinding and in the RecyclerView.ViewHolder(binding.root) pass it like this
    inner class ViewHolder(val binding: SingleItemBinding) : RecyclerView.ViewHolder(binding.root)

    // inside the onCreateViewHolder inflate the view of SingleItemBinding
    // and return new ViewHolder object containing this layout
    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val binding = SingleItemBinding.inflate(LayoutInflater.from(parent.context), parent, false)
        return ViewHolder(binding)
    }

    // bind the items with each item of the list languageList which than will be
    // shown in recycler view
    // to keep it simple we are not setting any image data to view
    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        with(holder){
            with(languageList[position]){
                // set name of the language from the list
                binding.tvLangName.text = this.name
                // set description to the text
                // since this is inside "expandedView" its visibility will be gone initially
                // after click on the item we will make the visibility of the "expandedView" visible
                // which will also make the visibility of desc also visible
                binding.tvDescription.text = this.description
                // check if boolean property "extend" is true or false
                // if it is true make the "extendedView" Visible
                binding.expandedView.visibility = if (this.expand) View.VISIBLE else View.GONE
                // on Click of the item take parent card view in our case
                // revert the boolean "expand"
                binding.cardLayout.setOnClickListener {
                    this.expand = !this.expand
                    notifyDataSetChanged()
                }
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
import com.geeksforgeeks.rvadapterviewbinding.databinding.ActivityMainBinding

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
        binding.rvList.layoutManager = LinearLayoutManager(this)

        // attach adapter to the recycler view
        rvAdapter = RvAdapter(languageList)
        binding.rvList.adapter = rvAdapter

        // create new objects
        // add some row data
        val language1 = Language(
            "Java",
            "Java is an Object Oriented Programming language." +
                    " Java is used in all kind of applications like Mobile Applications (Android is Java based), " +
                    "desktop applications, web applications, client server applications, enterprise applications and many more. ",
            false
        )
        val language2 = Language(
            "Kotlin",
            "Kotlin is a statically typed, general-purpose programming language" +
                    " developed by JetBrains, that has built world-class IDEs like IntelliJ IDEA, PhpStorm, Appcode, etc.",
            false
        )
        val language3 = Language(
            "Python",
            "Python is a high-level, general-purpose and a very popular programming language." +
                    " Python programming language (latest Python 3) is being used in web development, Machine Learning applications, " +
                    "along with all cutting edge technology in Software Industry.",
            false
        )
        val language4 = Language(
            "CPP",
            "C++ is a general purpose programming language and widely used now a days for " +
                    "competitive programming. It has imperative, object-oriented and generic programming features. ",
            false
        )

        // add items to list
        languageList.add(language1)
        languageList.add(language2)
        languageList.add(language3)
        languageList.add(language4)

        rvAdapter.notifyDataSetChanged()

    }

    // on destroy of view make the binding reference to null
    override fun onDestroy() {
        super.onDestroy()
        _binding = null
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-578854-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210323135218/expandable_rv_android_gfg.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210323135218/expandable_rv_android_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210323135218/expandable_rv_android_gfg.mp4)</video>

**Github Repo** [**此处**](https://github.com/introidx/RvGFG/tree/expandable_rv) **。**