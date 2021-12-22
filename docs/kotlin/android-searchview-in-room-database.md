# 房间数据库中的安卓搜索视图

> 原文:[https://www . geesforgeks . org/Android-search view-in-room-database/](https://www.geeksforgeeks.org/android-searchview-in-room-database/)

数据库中的 SearchView 是一个非常基本的功能，你可以在日常生活中的大多数应用程序中看到，那么为什么不呢，你应该学习并实现它。在应用程序中实现并不太复杂。有很多更简单的方法可以实现它。您应该用来实现[搜索视图](https://www.geeksforgeeks.org/android-searchview-with-example/)的应用内任务是:-

1.  You need to create a menu item, set the action view class as a search view, and set other action view properties.
2.  , and then expand the menu in the onCreateOptionsMenu () method of the action for which you want to search.
3.  Then get the SearchView object from the menu and add SearchView. OnQueryTextListener calls it by calling the setOnQueryTextListener method.
4.  搜索视图。OnQueryTextListener 有两个回调方法 onQueryTextSubmit 和 onQueryTextChange
5.  Method onQueryTextSubmit will be called when the user submits the search by clicking the input button or clicking the submit button on the search widget.

在这种方法中，可以使用输入到搜索视图小部件中的文本来执行数据库搜索。您可以通过调用 setSubmitButtonEnabled 方法并传递布尔值 true 来启用搜索视图小部件中的搜索按钮。它是如何工作的一个基本概念。但是我们将讨论从房间数据库中搜索数据的最有效方法，为此，您应该了解一些概念，例如:

**先决条件:**

*   [How to use RoomDB](https://www.geeksforgeeks.org/how-to-perform-crud-operations-in-room-database-in-android/) (What is an adapter)
*   [What is room database](https://www.geeksforgeeks.org/overview-of-room-in-android-architecture-components/) (library)?
*   熟悉[模型–视图–视图模型架构(MVVM)](https://www.geeksforgeeks.org/mvvm-model-view-viewmodel-architecture-pattern-in-android/)
*   The most important one is [Dependent injection (dagger handle)](https://www.geeksforgeeks.org/dependency-injection-with-dagger-2-in-android/)

除此之外，我们不会从头开始创建一个应用程序，我们会提供初始内容的源代码，比如

*   按数据库更新回收视图中的数据
*   使用依赖注入
*   还创建了一些额外的课程

我们给你一个项目的快速概述，然后你会很容易理解它。通过[下载项目点击此处](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20211013235540/searchViewInRoom-master.zip)。

### 逐步实施

**第一步:从 GitHub 下载项目，添加到你的安卓工作室**

我们希望你们都知道如何将现有的项目导入到 android studio 中，如果没有，请转到文件>打开>选择下载的项目>然后等待…完成项目构建

**第二步:搭建。渐变文件**

导航到应用程序>渐变脚本>构建。在依赖项部分添加下面的依赖项。

*   We added some dependencies and plugins.
*   And enable view binding.

```kt
plugins {
   id 'com.android.application'
   id 'kotlin-android'
   id 'kotlin-kapt'     // dagger hilt plugin 
   id 'dagger.hilt.android.plugin'
}

android {

   compileSdkVersion 30
   buildToolsVersion "30.0.2"
   defaultConfig {
       applicationId "com.example.searchViewInRoom"
       minSdkVersion 21
       targetSdkVersion 30
       versionCode 1
       versionName "1.0"
       testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"
   }

   // here we have enabled viewBinding
   buildFeatures {
       viewBinding true
   }

   buildTypes {
       release {
           minifyEnabled false
           proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
       }
   }

   compileOptions {
       sourceCompatibility JavaVersion.VERSION_1_8
       targetCompatibility JavaVersion.VERSION_1_8
   }

   kotlinOptions {
       jvmTarget = '1.8'
   }

}

dependencies {
   implementation "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
   implementation 'androidx.core:core-ktx:1.3.2'
   implementation 'androidx.appcompat:appcompat:1.2.0'
   implementation 'com.google.android.material:material:1.2.1'
   implementation 'androidx.constraintlayout:constraintlayout:2.0.4'
   testImplementation 'junit:junit:4.13.1'
   androidTestImplementation 'androidx.test.ext:junit:1.1.2'
   androidTestImplementation 'androidx.test.espresso:espresso-core:3.3.0'

   // Navigation Component
   implementation 'androidx.navigation:navigation-fragment-ktx:2.3.2'

   // Room components
   implementation "androidx.room:room-runtime:2.2.6"

   kapt "androidx.room:room-compiler:2.2.6"
   implementation "androidx.room:room-ktx:2.2.6"

   androidTestImplementation "androidx.room:room-testing:2.2.6"

   // Dagger - Hilt
   implementation "com.google.dagger:hilt-android:2.28.3-alpha"

   kapt "com.google.dagger:hilt-android-compiler:2.28.3-alpha"
   implementation "androidx.hilt:hilt-lifecycle-viewmodel:1.0.0-alpha02"
   kapt "androidx.hilt:hilt-compiler:1.0.0-alpha02"

   // Lifecycle
   implementation "androidx.lifecycle:lifecycle-extensions:2.2.0"
   implementation "androidx.lifecycle:lifecycle-viewmodel-ktx:2.2.0"
   implementation "androidx.lifecycle:lifecycle-livedata-ktx:2.2.0"
}
```

**第三步:创建实体/表格**

转到 app > main > searcheviewinroom > data > person . kt .这是我们如何使用房间

## 科特林

在 SQLite 数据库中创建实体/表

```kt
package com.example.searchViewInRoom.data

import androidx.room.Entity
import androidx.room.PrimaryKey

// it's our data class that we have
// annotate @Entity to create it as table
@Entity(tableName = "person_table")
data class Person(
    // table is basically 
      // having 3 fields as follow....
    var firstName: String,
    var lastName: String,
    var age: Int
){
    @PrimaryKey(autoGenerate = true)
    // we make id as primary 
      // key and it will autogenerate
    var id: Int = 0
}
```