# 如何在安卓系统中实现谷歌的地点自动完成栏？

> 原文:[https://www . geeksforgeeks . org/how-implement-Googles-places-autocomplete bar-in-Android/](https://www.geeksforgeeks.org/how-to-implement-googles-places-autocompletebar-in-android/)

如果你曾经在手机上使用过谷歌地图，或者从桌面上访问过，你肯定在搜索栏的某个位置输入了内容，并选择了其中的一个结果。结果可能有地址、电话号码、收视率、计时等字段。此外，如果你曾经在桌面上搜索过 google.com 的一个地方，你一定会得到许多搜索结果，还有一张带有上述参数的右边对齐的位置卡。下面给出了一个 GIF 示例，来了解一下我们将在本文中做什么。注意，我们将使用 **Kotlin** 语言来实现这个项目。

<video class="wp-video-shortcode" id="video-608976-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210519095714/ABImplement.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210519095714/ABImplement.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210519095714/ABImplement.mp4)</video>

这两个应用程序都实现了一个单一的应用编程接口，这就是众所周知的位置应用编程接口。自动完成栏是地点应用编程接口的一项功能，它根据用户在搜索栏中键入的单词推荐位置列表。借助 Places API，我们将实现自动完成栏并获取位置信息。

### **分步实施**

**第一步:在安卓工作室新建项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。我们在 Kotlin 中演示了该应用程序，因此在创建新项目时，请确保选择 **Kotlin** 作为主要语言。

**第二步:获取并隐藏 API 密钥**

我们的应用程序利用谷歌的地点应用编程接口来实现自动完成栏，所以我们需要从谷歌获得地点应用编程接口密钥。要获取应用编程接口密钥，请参考[为使用任何谷歌应用编程接口生成应用编程接口密钥](https://www.geeksforgeeks.org/generating-api-keys-for-using-any-google-apis/)。隐藏应用编程接口密钥是必不可少的，要做到这一点，请参考[如何在安卓工作室隐藏应用编程接口和密钥？](https://www.geeksforgeeks.org/how-to-hide-api-and-secret-keys-in-android-studio/)。

**第三步:在 build.gradle 文件**中添加依赖项

我们需要导入支持自动完成栏实现的库。由于自动完成栏是 Places API 的一个特性，我们需要在 [build.gradle](https://www.geeksforgeeks.org/android-build-gradle/) 文件中追加它的最新依赖项。下面是必须添加的依赖项。

> 实现' com . Google . Android . libraries . places:places:2 . 4 . 0 '

**第四步:在你的清单文件**中添加互联网权限

导航到**应用程序>清单文件夹**，并为其写下以下权限。

**第五步:在 activity_main.xml 文件(前端)中实现自动完成栏片段**

导航到 **app > res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是**activity _ main . XML**文件的代码。

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

    <LinearLayout
        android:id="@+id/ll1"
        android:layout_width="match_parent"
        android:layout_height="40sp"
        android:layout_marginLeft="10sp"
        android:layout_marginRight="10sp"
        android:background="@android:color/white">
        <fragment
            android:id="@+id/autocomplete_fragment1"
            android:name="com.google.android.libraries.places.widget.AutocompleteSupportFragment"
            android:layout_width="match_parent"
            android:layout_height="match_parent"/>
    </LinearLayout>

    <TextView
        android:id="@+id/tv1"
        android:layout_below="@id/ll1"
        android:layout_marginTop="20sp"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        />

</RelativeLayout>
```

**第 6 步:使用 MainActivity.kt(后端)**

简而言之，我们做的是:

1.  获取我们在**步骤 2** 中存储的 API 密钥。
2.  使用应用编程接口键初始化位置应用编程接口。
3.  初始化布局(activity_main.xml)中的自动完成片段。
4.  声明了我们希望从 API 获取的位置参数。
5.  在 select listener 事件上声明，当从自动完成栏结果中单击位置时，该事件会在布局的文本视图中发布参数。

***onError*** 函数是 select listener 的成员函数，在失败的情况下会抛出祝酒信息“出现了一些错误”。一个普遍的原因可能是互联网不可用。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
package org.geeksforgeeks.myapplication

import android.content.pm.ApplicationInfo
import android.content.pm.PackageManager
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.TextView
import android.widget.Toast
import com.google.android.gms.common.api.Status
import com.google.android.libraries.places.api.Places
import com.google.android.libraries.places.api.model.Place
import com.google.android.libraries.places.widget.AutocompleteSupportFragment
import com.google.android.libraries.places.widget.listener.PlaceSelectionListener

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Fetching API_KEY which we wrapped
        val ai: ApplicationInfo = applicationContext.packageManager
            .getApplicationInfo(applicationContext.packageName, PackageManager.GET_META_DATA)
        val value = ai.metaData["api_key"]
        val apiKey = value.toString()

        // Initializing the Places API 
          // with the help of our API_KEY
        if (!Places.isInitialized()) {
            Places.initialize(applicationContext, apiKey)
        }

        // Initialize Autocomplete Fragments 
          // from the main activity layout file
        val autocompleteSupportFragment1 = supportFragmentManager.findFragmentById(R.id.autocomplete_fragment1) as AutocompleteSupportFragment?

        // Information that we wish to fetch after typing 
          // the location and clicking on one of the options
        autocompleteSupportFragment1!!.setPlaceFields(
            listOf(

                Place.Field.NAME,
                Place.Field.ADDRESS,
                Place.Field.PHONE_NUMBER,
                Place.Field.LAT_LNG,
                Place.Field.OPENING_HOURS,
                Place.Field.RATING,
                Place.Field.USER_RATINGS_TOTAL

            )
        )

        // Display the fetched information after clicking on one of the options
        autocompleteSupportFragment1.setOnPlaceSelectedListener(object : PlaceSelectionListener {
            override fun onPlaceSelected(place: Place) {

                // Text view where we will
                  // append the information that we fetch
                val textView = findViewById<TextView>(R.id.tv1)

                // Information about the place
                val name = place.name
                val address = place.address
                val phone = place.phoneNumber.toString()
                val latlng = place.latLng
                val latitude = latlng?.latitude
                val longitude = latlng?.longitude

                val isOpenStatus : String = if(place.isOpen == true){
                    "Open"
                } else {
                    "Closed"
                }

                val rating = place.rating
                val userRatings = place.userRatingsTotal

                textView.text = "Name: $name \nAddress: $address \nPhone Number: $phone \n" +
                        "Latitude, Longitude: $latitude , $longitude \nIs open: $isOpenStatus \n" +
                        "Rating: $rating \nUser ratings: $userRatings"
            }

            override fun onError(status: Status) {
                Toast.makeText(applicationContext,"Some error occurred", Toast.LENGTH_SHORT).show()
            }
        })

    }
}
```

**输出:**

> **注意:**启动应用前打开互联网(Wifi/移动数据)。

<video class="wp-video-shortcode" id="video-608976-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210519095714/ABImplement.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210519095714/ABImplement.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210519095714/ABImplement.mp4)</video>