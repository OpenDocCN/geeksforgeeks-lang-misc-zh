# 如何使用 Kotlin 在安卓中创建 RecyclerView 的选项菜单？

> 原文:[https://www . geeksforgeeks . org/如何创建-选项-菜单-for-recycle view-in-Android-use-kot Lin/](https://www.geeksforgeeks.org/how-to-create-options-menu-for-recyclerview-in-android-using-kotlin/)

[【recycle view】](https://www.geeksforgeeks.org/android-recyclerview/)是作为 GridView 和 ListView 的继承者加入安卓工作室的一个视图组。这是对两者的改进，可以在最新的 v-7 支持包中找到。它的创建是为了能够将任何带有 **XML** 布局的列表构建为一个项目，这样就可以进行大量定制，而 *则提高了列表视图和网格视图* 的效率。这种改进是通过回收用户不可见的视图来实现的。例如，如果用户向下滚动到项目 4 和 5 可见的位置；项目 1、2 和 3 将从内存中清除，以减少内存消耗。在本文中，我们将解释如何在回收视图的每个项目中使用[选项菜单](https://www.geeksforgeeks.org/how-to-implement-options-menu-in-android/)。下面是展示我们将要构建的内容的示例视频。注意，我们将使用 **Kotlin** 语言来实现这个项目。

<video class="wp-video-shortcode" id="video-578866-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210323133613/options_menu_in_rv_android_gfg.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210323133613/options_menu_in_rv_android_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210323133613/options_menu_in_rv_android_gfg.mp4)</video>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:添加视图绑定依赖关系**

转到 **build.gradle(app)** 和安卓标签内的以下依赖项，点击**立即同步**。

> 构建功能{
> 
> 视图绑定为真
> 
> }

**步骤 3:使用 activity_main.xml 文件**

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
            android:layout_width="90dp"
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
            android:layout_marginTop="20dp"
            android:text="Language"
            android:textSize="20sp"
            android:textColor="@color/black"
            android:textStyle="bold"
            app:layout_constraintLeft_toRightOf="@id/iv_language"
            app:layout_constraintTop_toTopOf="parent" />

        <!--Text view fr showing exp-->
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            app:layout_constraintTop_toBottomOf="@id/tv_lang_name"
            app:layout_constraintLeft_toLeftOf="@id/tv_lang_name"
            android:text="1 Year exp"
            android:id="@+id/tv_exp"
            android:textSize="16sp"
            android:layout_marginTop="15dp"/>

        <!--Text view for showing the options menu-->
        <TextView
            android:id="@+id/textViewOptions"
            android:layout_width="20dp"
            android:gravity="center"
            android:layout_height="30dp"
            android:layout_alignParentTop="true"
            android:textStyle="bold"
            app:layout_constraintRight_toRightOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            android:layout_margin="20dp"
            android:text="⋮"
            android:textAppearance="?android:textAppearanceLarge" />

    </androidx.constraintlayout.widget.ConstraintLayout>

</com.google.android.material.card.MaterialCardView>
```

**第五步:新建模型类**

创建一个新的类 **Language.kt** 我们将使用自定义通用“ **Language** ”的数据来传入将在回收器视图中显示的列表。

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
import com.geeksforgeeks.rvadapterviewbinding.databinding.SingleItemBinding

class RvAdapter(
    private var languageList: List<Language>,
    private var optionsMenuClickListener: OptionsMenuClickListener
) : RecyclerView.Adapter<RvAdapter.ViewHolder>() {

    // create an interface for onClickListener
    // so that we can handle data most effectively in MainActivity.kt
    interface OptionsMenuClickListener {
        fun onOptionsMenuClicked(position: Int)
    }

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
                // set text to language name
                binding.tvLangName.text = this.name
                // set exp
                binding.tvExp.text = this.exp
                // implement on clickListener and pass position of the item
                // rest we will handle in MainActivity.kt
                binding.textViewOptions.setOnClickListener {
                    optionsMenuClickListener.onOptionsMenuClicked(position)
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
import android.view.MenuItem
import android.widget.PopupMenu
import android.widget.Toast
import androidx.core.view.get
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
        // attach adapter to the recycler view and also handle item click
        rvAdapter = RvAdapter(languageList , object : RvAdapter.OptionsMenuClickListener{
            // implement the required method
            override fun onOptionsMenuClicked(position: Int) {
                // this method will handle the onclick options click
                // it is defined below
                performOptionsMenuClick(position)
            }
        })
        // add adapter to the recycler view
        binding.rvList.adapter = rvAdapter

        // create objects of Language
        // create some row data
        val language1 = Language("Java" , "3 Year exp" )
        val language2 = Language("Kotlin" , "2 Year exp" )
        val language3 = Language("Python" , "1 Year exp" )
        val language4 = Language("CPP" , "5 Year exp" )
        val language5 = Language("PHP" , "No exp" )

        // pass raw data t rhe list
        languageList.add(language1)
        languageList.add(language2)
        languageList.add(language3)
        languageList.add(language4)
        languageList.add(language5)

        rvAdapter.notifyDataSetChanged()
    }

    // this method will handle the onclick options click
    private fun performOptionsMenuClick(position: Int) {
        // create object of PopupMenu and pass context and view where we want
        // to show the popup menu
        val popupMenu = PopupMenu(this , binding.rvList[position].findViewById(R.id.textViewOptions))
        // add the menu
        popupMenu.inflate(R.menu.options_menu)
        // implement on menu item click Listener
        popupMenu.setOnMenuItemClickListener(object : PopupMenu.OnMenuItemClickListener{
            override fun onMenuItemClick(item: MenuItem?): Boolean {
                when(item?.itemId){
                    R.id.delete -> {
                        // here are the logic to delete an item from the list
                        val tempLang = languageList[position]
                        languageList.remove(tempLang)
                        rvAdapter.notifyDataSetChanged()
                        return true
                    }
                    // in the same way you can implement others
                    R.id.item2 -> {
                        // define
                        Toast.makeText(this@MainActivity , "Item 2 clicked" , Toast.LENGTH_SHORT).show()
                        return true
                    }
                    R.id.item3 -> {
                        // define
                        Toast.makeText(this@MainActivity , "Item 3 clicked" , Toast.LENGTH_SHORT).show()
                        return true
                    }
                }
                return false
            }
        })
        popupMenu.show()
    }

    // on destroy of view make the binding reference to null
    override fun onDestroy() {
        super.onDestroy()
        _binding = null
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-578866-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210323133613/options_menu_in_rv_android_gfg.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210323133613/options_menu_in_rv_android_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210323133613/options_menu_in_rv_android_gfg.mp4)</video>

**Github 回购** [这里**。**](https://github.com/introidx/RvGFG/tree/options_menu_for_rv)