# 安卓系统中的首选数据存储

> 原文:[https://www . geesforgeks . org/preferences-datastore-in-Android/](https://www.geeksforgeeks.org/preferences-datastore-in-android/)

**偏好数据存储**用于在安卓中永久存储数据。早先我们不得不[共享首选项](https://www.geeksforgeeks.org/shared-preferences-in-android-with-examples/)**T5】来获得相同的，但是因为它被否决了，我们现在使用数据存储。下面给出了一个示例视频，以了解我们将在本文中做什么。请注意，我们将使用 **Kotlin** 语言来实现这个项目。**

<video class="wp-video-shortcode" id="video-547017-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210122121933/prefs_data_store_gfg2.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210122121933/prefs_data_store_gfg2.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210122121933/prefs_data_store_gfg2.mp4)</video>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。请注意，选择**科特林**作为编程语言

**第二步:在 build.gradle(app)中添加依赖关系**

在 **build.gradle(app)** 中添加[数据存储](https://developer.android.com/jetpack/androidx/releases/datastore)、[生命周期](https://developer.android.com/jetpack/androidx/releases/lifecycle)和 [Coroutines](https://github.com/Kotlin/kotlinx.coroutines) 依赖项，点击**立即同步**按钮。

> //首选项数据存储
> 
> 实现“androidx . datastore:datastore-preferences:1 . 0 . 0-alpha 01”
> 
> //生命周期组件
> 
> 实现“androidx . life cycle:life cycle-live data-ktx:2 . 2 . 0”
> 
> 实现“androidx . life cycle:life cycle-extensions:2 . 2 . 0”
> 
> 实现“androidx . life cycle:life cycle-common-java8:2 . 2 . 0”
> 
> 实现“androidx . life cycle:life cycle-view model-ktx:2 . 2 . 0”
> 
> // Kotlin coroutines 组件
> 
> 实现" org . jet brains . kot Lin:kot Lin-stdlib-JDK 7:1 . 4 . 10 "
> 
> api“组织 jetbrains . kot linx:kot linx-corroutines 核心:1.4.1”
> 
> “组织 jetbrains . kot linx:kot linx-corroutines-Android:1 . 4 . 1”API

**步骤 3:使用 activity_main.xml 文件**

转到 **activity_main.xml** 文件，参考以下代码。下面是 **activity_main.xml** 文件的代码。这是应用程序中使用的基本布局。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center_horizontal"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/et_name"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:layout_marginTop="20dp"
        android:ems="10"
        android:hint="Name" />

    <EditText
        android:id="@+id/et_age"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:ems="10"
        android:hint="Age"
        android:inputType="number" />

    <Button
        android:id="@+id/btn_save"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:background="#FF7043"
        android:padding="10dp"
        android:text="Save user"
        android:textColor="@android:color/white" />

    <TextView
        android:id="@+id/tv_name"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:text="Name"
        android:textColor="@android:color/black"
        android:textSize="20sp" />

    <TextView
        android:id="@+id/tv_age"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:text="Age"
        android:textColor="@android:color/black"
        android:textSize="20sp" />

</LinearLayout>
```

**第 4 步:使用 UserManager.kt 类**

创建一个新的 [kotlin 类](https://www.geeksforgeeks.org/how-to-create-classes-in-android-studio/)并将其命名为**用户管理器**，该类保存从首选项数据存储中保存和检索数据的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.content.Context
import androidx.datastore.preferences.createDataStore
import androidx.datastore.preferences.edit
import androidx.datastore.preferences.preferencesKey
import kotlinx.coroutines.flow.Flow
import kotlinx.coroutines.flow.map

class UserManager(context: Context) {

    // Create the dataStore and give it a name same as shared preferences
    private val dataStore = context.createDataStore(name = "user_prefs")

    // Create some keys we will use them to store and retrieve the data
    companion object {
        val USER_AGE_KEY = preferencesKey<Int>("USER_AGE")
        val USER_NAME_KEY = preferencesKey<String>("USER_NAME")
    }

    // Store user data
    // refer to the data store and using edit 
    // we can store values using the keys
    suspend fun storeUser(age: Int, name: String) {
        dataStore.edit {
            it[USER_AGE_KEY] = age
            it[USER_NAME_KEY] = name

            // here it refers to the preferences we are editing

        }
    }

    // Create an age flow to retrieve age from the preferences
    // flow comes from the kotlin coroutine
    val userAgeFlow: Flow<Int> = dataStore.data.map {
        it[USER_AGE_KEY] ?: 0
    }

    // Create a name flow to retrieve name from the preferences
    val userNameFlow: Flow<String> = dataStore.data.map {
        it[USER_NAME_KEY] ?: ""
    }
}
```

**步骤 5:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity
import androidx.lifecycle.asLiveData
import androidx.lifecycle.observe
import kotlinx.coroutines.GlobalScope
import kotlinx.coroutines.launch

class MainActivity : AppCompatActivity() {

    lateinit var etName: EditText
    lateinit var etAge: EditText
    lateinit var tvName: TextView
    lateinit var tvAge: TextView
    lateinit var saveButton: Button

    lateinit var userManager: UserManager
    var age = 0
    var name = ""

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        etName = findViewById(R.id.et_name)
        etAge = findViewById(R.id.et_age)
        tvName = findViewById(R.id.tv_name)
        tvAge = findViewById(R.id.tv_age)
        saveButton = findViewById(R.id.btn_save)

        // Get reference to our userManager class
        userManager = UserManager(this)

        // this function saves the data to
        // preference data store on click of
        // save Button
        buttonSave()

        // this function retrieves the saved data
        // as soon as they are stored and even
        // after app is closed and started again
        observeData()
    }

    private fun buttonSave() {
        // Gets the user input and saves it
        saveButton.setOnClickListener {
            name = etName.text.toString()
            age = etAge.text.toString().toInt()

            // Stores the values
            // Since the storeUser function of UserManager
            // class is a suspend function
            // So this has to be done in a coroutine scope
            GlobalScope.launch {
                userManager.storeUser(age, name)
            }
        }
    }

    private fun observeData() {
        // Updates age
        // every time user age changes it will be observed by userAgeFlow
        // here it refers to the value returned from the userAgeFlow function 
        // of UserManager class
        this.userManager.userAgeFlow.asLiveData().observe(this) {
            age = it
            tvAge.text = it.toString()
        }

        // Updates name
        // every time user name changes it will be observed by userNameFlow
        // here it refers to the value returned from the usernameFlow function 
        // of UserManager class
        userManager.userNameFlow.asLiveData().observe(this) {
            name = it
            tvName.text = it.toString()
        }
    }
}
```

### 输出:

<video class="wp-video-shortcode" id="video-547017-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210122121933/prefs_data_store_gfg2.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210122121933/prefs_data_store_gfg2.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210122121933/prefs_data_store_gfg2.mp4)</video>

github rest 在这里。