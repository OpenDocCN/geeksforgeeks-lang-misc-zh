# 如何在安卓系统中使用编辑文本和文本观察器在列表视图中搜索一个项目？

> 原文:[https://www . geesforgeks . org/如何在列表视图中搜索项目-使用-edittext-and-text watcher-in-Android/](https://www.geeksforgeeks.org/how-to-search-an-item-in-listview-using-edittext-and-textwatcher-in-android/)

一些应用程序提供了一个搜索栏，用于从项目列表中查找任何特定的项目。从技术上讲，搜索栏是编辑文本，项目列表可以是列表视图、回收视图或包含某些项目的网格视图。现在，当用户在编辑文本中键入内容时，列表必须根据用户键入的文本进行更新。字符串匹配算法用于检查键入的文本是否是任何列表项的子字符串，如果是，则这些项显示在更新列表视图中。但是，创建单独的函数或算法来执行此搜索操作会消耗编辑器上更多的行。为此，可以使用一个 TextWatcher 对象，一个公共接口，它在 EditText 上实现并检查文本是否改变。因此，在本文中，我们将向您展示如何在编辑文本上实现文本观察器，以便在用户输入时更新结果列表视图。一旦集成开发环境准备就绪，请遵循以下步骤。

### 逐步实施

**第一步:在安卓工作室新建项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在 **Kotlin** 中演示了该应用程序，因此在创建新项目时，请确保选择 Kotlin 作为主要语言。

**步骤 2:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** ，并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。在活动的顶部创建一个[编辑文本](https://www.geeksforgeeks.org/android-edittext-in-kotlin/)，它应该是一个假定的搜索栏，并在其下方创建一个[列表视图](https://www.geeksforgeeks.org/android-listview-in-kotlin/)来显示项目。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/edit_text"
        android:layout_width="match_parent"
        android:layout_height="50sp"
        android:inputType="text"/>

    <ListView
        android:id="@+id/list_view"
        android:layout_below="@id/edit_text"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>

</RelativeLayout>
```

**第三步:使用**T2【主活动. kt】文件

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。我们声明了一个项目数组，如代码所示。这些项目最初使用适配器显示在列表视图中。接下来，在编辑文本上实现[文本观察器](https://www.geeksforgeeks.org/how-to-implement-textwatcher-in-android/)。TextWatcher 实现了三个成员函数，即 beforeTextChanger()、onTextChanged()和 afterTextChanged()。我们关心的是 ***onTextChanged()*** ，因为我们希望在文本实时变化时更新列表视图。该函数从编辑文本中获取整个字符串，根据输入过滤适配器中的数组元素，并显示更新后的列表视图。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.text.Editable
import android.text.TextWatcher
import android.widget.ArrayAdapter
import android.widget.EditText
import android.widget.ListView

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Declare and Initialize the EditText
          // and ListView from the layout file.
        val mSearch = findViewById<EditText>(R.id.edit_text)
        val mListView = findViewById<ListView>(R.id.list_view)

        // Declare array of elements, create an adapter
          // and display the array in the ListView
        val mCities = arrayOf("Mumbai", "Mohali", "Delhi", "Dehradun", "Darjeeling", "Bengaluru")
        val mArrayAdapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, android.R.id.text1, mCities)
        mListView.adapter = mArrayAdapter

          // TextWatcher to check if the EditText text changes
        mSearch.addTextChangedListener(object: TextWatcher{
            override fun beforeTextChanged(s: CharSequence?, start: Int, count: Int, after: Int) {
                // Do Nothing
            }

            override fun onTextChanged(s: CharSequence?, start: Int, before: Int, count: Int) {
                mArrayAdapter.filter.filter(s)
            }

            override fun afterTextChanged(s: Editable?) {
                // Do Nothing
            }

        })
    }
}
```

**输出:**

我们可以看到列表视图是根据给定的输入进行更新的。

<video class="wp-video-shortcode" id="video-728388-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210816211533/o104.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210816211533/o104.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210816211533/o104.mp4)</video>