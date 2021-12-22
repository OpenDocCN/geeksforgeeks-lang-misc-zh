# 如何在安卓中动态添加视图并在数组列表中存储数据？

> 原文:[https://www . geeksforgeeks . org/如何在 android 中动态添加视图和存储数组列表中的数据/](https://www.geeksforgeeks.org/how-to-add-views-dynamically-and-store-data-in-arraylist-in-android/)

**动态视图**是在我们不想有重复的 XML 代码时创建的。在本文中，我们将创建一个单独的布局，并在[线性布局](https://www.geeksforgeeks.org/android-linearlayout-in-kotlin/)中膨胀它们，然后我们将用户数据存储在**数组列表**中，并将其显示为[吐司](https://www.geeksforgeeks.org/android-what-is-toast-and-how-to-use-it-with-examples/)。下面给出一个视频示例，了解一下我们在本文中要做什么。注意，我们将使用 **Kotlin** 语言来实现这个项目。

<video class="wp-video-shortcode" id="video-545983-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210117172810/add_dynamic_views_android_prview_gfg.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210117172810/add_dynamic_views_android_prview_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210117172810/add_dynamic_views_android_prview_gfg.mp4)</video>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。请注意，选择**科特林**作为编程语言

**第二步:在 build.gradle(app)中添加依赖关系**

在 **build.gradle(app)** 中添加[视图绑定](https://developer.android.com/topic/libraries/view-binding)依赖项，点击立即同步按钮。

> 安卓{
> 
> ..
> 
> 构建功能{
> 
> 视图绑定为真
> 
> }
> 
> }

**步骤 3:使用 activity_main.xml 文件**

转到 **activity_main.xml** 文件，参考以下代码。下面是 **activity_main.xml** 文件的代码。注意它有一个 id 为 ***的 Linear Layout 父 _linear_layout*** ，我们将对其进行膨胀以添加我们的视图。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_margin="15dp"
        android:text="Programming Language List"
        android:textColor="@color/black"
        android:textSize="15sp" />

    <!--This is the parent linear layout
        which we will inflate soon-->
    <LinearLayout
        android:id="@+id/parent_linear_layout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical" />

    <com.google.android.material.button.MaterialButton
        android:id="@+id/button_add"
        android:layout_width="wrap_content"
        android:layout_height="50dp"
        android:layout_marginLeft="15dp"
        android:layout_marginTop="10dp"
        android:drawableRight="@drawable/ic_add"
        android:paddingLeft="10dp"
        android:paddingRight="10dp"
        android:text="Add"
        android:textAllCaps="false"
        android:textColor="@color/white" />

    <com.google.android.material.button.MaterialButton
        android:id="@+id/button_submit_list"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:layout_marginLeft="15dp"
        android:layout_marginTop="10dp"
        android:layout_marginRight="15dp"
        android:paddingLeft="10dp"
        android:paddingRight="10dp"
        android:text="Submit List"
        android:textAllCaps="false"
        android:textColor="@color/white" />

    <com.google.android.material.button.MaterialButton
        android:id="@+id/button_show_list"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:layout_marginLeft="15dp"
        android:layout_marginTop="10dp"
        android:layout_marginRight="15dp"
        android:paddingLeft="10dp"
        android:paddingRight="10dp"
        android:text="Show List Data"
        android:textAllCaps="false"
        android:textColor="@color/white" />

</LinearLayout>
```

**第 4 步:创建新布局**

创建名为 **row_add_language.xml** 的新布局。这是我们将用 id *parent_linear_layout* 在 Linear Layout 内部展开的单独布局。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_margin="10dp">

    <EditText
        android:id="@+id/et_name"
        android:layout_width="200dp"
        android:layout_height="50dp"
        android:hint="Enter language"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Spinner
        android:id="@+id/exp_spinner"
        android:layout_width="100dp"
        android:layout_height="50dp"
        android:layout_marginStart="20dp"
        android:entries="@array/experience"
        app:layout_constraintLeft_toRightOf="@id/et_name"
        app:layout_constraintTop_toTopOf="parent"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```

**第 5 步:在 string.xml 中添加我们在 Spinner** 中使用的条目

## 可扩展标记语言

```kt
<string-array name="experience">
     <item>Exp</item>
     <item>1 Year</item>
     <item>2 Year</item>
     <item>3 Year</item>
     <item>4 Year</item>
 </string-array>
```

**第六步:创建一个新的 Kotlin 类**

创建一个新的 Kotlin 类 **Language.kt** 。这是我们将用于数组列表来存储数据的通用类。

## 我的锅

```kt
class Language(
    var name: String = "",
    var exp: String = ""
) {
}
```

**第 7 步:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.os.Bundle
import android.view.LayoutInflater
import android.view.View
import android.widget.EditText
import android.widget.Spinner
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity

// Provide your package name here
import com.example.addviewsdynamically.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {

    // initiate viewBinding
    private var _binding: ActivityMainBinding? = null
    private val binding get() = _binding!!

    // create an arraylist in which
    // we will store user data
    private var languageList = ArrayList<Language>()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        _binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)

        // This addButton is used to add a new view
        // in the parent linear layout
        binding.buttonAdd.setOnClickListener {
            addNewView()
        }

        // This Submit Button is used to store all the
        // data entered by user in arraylist
        binding.buttonSubmitList.setOnClickListener {
            saveData()
        }

        // This Show button is used to show data
        // stored in the arraylist.
        binding.buttonShowList.setOnClickListener {
            showData()
        }
    }

    // This function is called after
    // user clicks on addButton
    private fun addNewView() {
        // this method inflates the single item layout
        // inside the parent linear layout
        val inflater = LayoutInflater.from(this).inflate(R.layout.row_add_language, null)
        binding.parentLinearLayout.addView(inflater, binding.parentLinearLayout.childCount)

    }

    // This function is called after user
    // clicks on Submit Button
    private fun saveData() {
        languageList.clear()
        // this counts the no of child layout
        // inside the parent Linear layout
        val count = binding.parentLinearLayout.childCount
        var v: View?

        for (i in 0 until count) {
            v = binding.parentLinearLayout.getChildAt(i)

            val languageName: EditText = v.findViewById(R.id.et_name)
            val experience: Spinner = v.findViewById(R.id.exp_spinner)

            // create an object of Language class
            val language = Language()
            language.name = languageName.text.toString()
            language.exp = experience.selectedItem as String

            // add the data to arraylist
            languageList.add(language)
        }
    }

    // This function is called after user
    // clicks on Show List data button
    private fun showData() {
        val count = binding.parentLinearLayout.childCount
        for (i in 0 until count) {
            Toast.makeText(this, "Language at $i is ${languageList[i].name} and experience is ${languageList[i].exp} ", Toast.LENGTH_SHORT).show()
        }
    }

    override fun onDestroy() {
        super.onDestroy()
        _binding = null
    }
}
```

### 输出:

<video class="wp-video-shortcode" id="video-545983-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210117172810/add_dynamic_views_android_prview_gfg.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210117172810/add_dynamic_views_android_prview_gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210117172810/add_dynamic_views_android_prview_gfg.mp4)</video>

github rest 在这里。