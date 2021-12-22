# 如何利用 DiffUtil 提高安卓中的 RecyclerView 性能？

> 原文:[https://www . geeksforgeeks . org/how-to-improved-recycle view-in-Android-use-diffutil/](https://www.geeksforgeeks.org/how-to-improve-recyclerview-performance-in-android-using-diffutil/)

[DiffUtil](https://developer.android.com/reference/androidx/recyclerview/widget/DiffUtil) 类用于提高[recycle view](https://www.geeksforgeeks.org/android-recyclerview/)的性能。DiffUtil 背后的算法是，它获取两个列表并找出两者之间的差异，然后将更新后的列表作为输出提供。它使用尤金·迈尔斯的差分算法来计算最小更新次数。在本文中，我们将看到它的实现。注意，我们将使用**柯特林**语言来实现这个项目。

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

**第三步:新建模型类**

创建一个新的类 **Language.kt** 我们将使用自定义通用“**语言**的数据来传入将在 RecyclerView 中显示的列表。

## 我的锅

```kt
// this is the Language model class
class Language(
    val id : Int =0,
    val name : String ="",
    val exp : String =""
)
```

**第四步:创建一个新的布局文件，并将其命名为 single_item.xml 文件**

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

**第 5 步:使用 activity_main.xml**

转到 **activity_main.xml** 文件，参考以下代码。下面是 activity_main.xml 文件的代码。它只有一个回收视图，我们将使用它来显示我们的数据。

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

    <com.google.android.material.floatingactionbutton.ExtendedFloatingActionButton
        android:id="@+id/btn_new_language"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Add New Language"
        android:padding="10dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        android:layout_marginBottom="20dp"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```

**第六步:新建一个类，并命名为 MyDiffUtil.kt**

转到 **MyDiffUtil.kt** 文件，编写以下代码。添加注释是为了更好地理解代码。

## 我的锅

```kt
import androidx.recyclerview.widget.DiffUtil

// pass two list one oldList and second newList
class MyDiffUtil(
    private val oldList : List<Language>,
    private val newList : List<Language>
) :DiffUtil.Callback() {
    // implement methods
    override fun getOldListSize(): Int {
        // return oldList size
        return oldList.size
    }

    override fun getNewListSize(): Int {
        // return newList size
        return newList.size
    }

    override fun areItemsTheSame(oldItemPosition: Int, newItemPosition: Int): Boolean {
        // compare items based on their unique id
        return oldList[oldItemPosition].id == newList[newItemPosition].id
    }

    override fun areContentsTheSame(oldItemPosition: Int, newItemPosition: Int): Boolean {
        // in here compare each item if they are same or different
        // return false if any data is same else return true
        return when{
            oldList[oldItemPosition].id != newList[newItemPosition].id -> false
            oldList[oldItemPosition].name != newList[newItemPosition].name -> false
            oldList[oldItemPosition].exp != newList[newItemPosition].exp -> false
            else -> true
        }
    }
}
```

**步骤 7:使用适配器类**

创建一个新类 **RvAdapter.kt** 这将作为回收视图的适配器类。使用视图绑定，我们使用布局 single_item.xml 即 SingleItemBinding 的生成类，在我们的例子中，在 MainActivity.kt 的回收器视图中添加数据和视图。为了更好地理解，在代码前添加了注释。

## 我的锅

```kt
import android.view.LayoutInflater
import android.view.ViewGroup
import androidx.recyclerview.widget.DiffUtil
import androidx.recyclerview.widget.RecyclerView
import com.geeksforgeeks.rvadapterviewbinding.databinding.SingleItemBinding

class RvAdapter() : RecyclerView.Adapter<RvAdapter.ViewHolder>() {

    private var oldLanguageList= emptyList<Language>()
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
            with(oldLanguageList[position]){
                binding.tvLangName.text = this.name
                binding.tvExp.text = this.exp
            }
        }
    }

    // return the size of languageList
    override fun getItemCount(): Int {
        return oldLanguageList.size
    }

    fun setData(newLanguageList : List<Language>){
        val diffUtil = MyDiffUtil(oldLanguageList , newLanguageList)
        // it calculates the different items of the oldLanguageList and newLanguageList
        val diffResult = DiffUtil.calculateDiff(diffUtil)
        // assign oldLanguageList to newLanguageList
        oldLanguageList = newLanguageList
        diffResult.dispatchUpdatesTo(this)
    }
}
```

**步骤 8:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import androidx.recyclerview.widget.LinearLayoutManager
import com.geeksforgeeks.rvadapterviewbinding.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {

    // view binding for the activity
    private var _binding : ActivityMainBinding? = null
    private val binding get() = _binding!!

    // get reference to the adapter class
    private val rvAdapter by lazy { RvAdapter() }

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        _binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)

        // define layout manager for the Recycler view
        binding.rvList.layoutManager = LinearLayoutManager(this)

        // attach adapter to the recycler view
        binding.rvList.adapter = rvAdapter

        // create new objects
        val language1= Language(1,"Java" , "Exp : 3 years")
        val language2=Language(2,"Kotlin" , "Exp : 2 years")
        val language3=Language(3,"Python" , "Exp : 4 years")

        // call set data method of adapter class and the list data
        rvAdapter.setData(listOf(language1, language2, language3))
        binding.btnNewLanguage.setOnClickListener {
            // on click of button add one more item to the list
            val language4= Language(4,"CPP" , "Exp : 5 years")
            rvAdapter.setData(listOf(language1,language2,language3,language4))
        }
    }

    // on destroy of view make the binding reference to null
    override fun onDestroy() {
        super.onDestroy()
        _binding = null
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-577346-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210320222246/rv_using_diffutil_gfg.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210320222246/rv_using_diffutil_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210320222246/rv_using_diffutil_gfg.mp4)</video>