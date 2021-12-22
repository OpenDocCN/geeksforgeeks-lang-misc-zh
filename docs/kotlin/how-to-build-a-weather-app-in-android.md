# 如何在安卓系统中搭建天气应用？

> 原文:[https://www . geeksforgeeks . org/如何构建安卓天气应用/](https://www.geeksforgeeks.org/how-to-build-a-weather-app-in-android/)

在这个项目中，我们将构建一个天气应用程序。该应用程序将显示某个位置的温度。为了获取天气信息，我们需要一个**应用编程接口。**一个 [API(应用程序编程接口)](https://www.geeksforgeeks.org/introduction-to-apis/)是一个允许应用程序使用各种组件和微服务进行交互和共享数据的功能。对于本项目，我们将使用**天气位应用编程接口**获取天气数据。天气位应用编程接口提供了一种快速而优雅的获取天气数据的方法。注意，我们将使用 **Kotlin** 语言来实现这个项目。

### **项目概述**

在这个项目中，我们将构建一个应用程序，它将找到设备的位置坐标(经度和纬度)。然后我们将通过 **API 键**将这些数据发送给 API(我们稍后会看到)。API 会给我们发送一个 [**JSON**](https://www.geeksforgeeks.org/javascript-json/) ，我们会从中提取出需要的数据，那就是位置的温度和城市。

### 逐步实施

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:** **先去编码区之前你要做一些前置任务**

转到 **app > res >** **可绘制** **文件**并将 [此图像](https://raw.githubusercontent.com/njdunk07/NJ-Weather-GFG/master/app/src/main/res/drawable/weather_background.jpg) 粘贴到此文件。现在**右键点击** **可绘制** **文件夹>新建>可绘制资源文件**并将文件命名为 s **btn_bg6** 。下面是 **btn_bg6.xml** 文件的代码。

> **参考文章:** [如何在 Android Studio 中给可绘制文件夹添加图片？](https://www.geeksforgeeks.org/how-to-add-image-to-drawable-folder-in-android-studio/)

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item>
        <shape>
            <gradient
                android:angle="0"
                android:startColor="#BBE1FD"
                android:endColor="#6CC7E3"
                android:type="linear"/>
        </shape>
    </item>
</selector>
```

**第三步:获取 API 密钥**

要获取 API 密钥，只需登录[**【天气位】**](https://www.weatherbit.io/) 并订阅当前天气数据 API 的免费 API。这样做之后，你会收到一个应用编程接口密钥，你可以走了。

**第四步:权限检查**

为了让这个应用程序工作，我们需要向系统申请三个权限–

> *   **粗定位**–<使用-权限安卓:name = " Android。允许。access _ rough _ Location "/ >
> *   **精定位**–<使用-权限安卓:name = " Android。允许。access _ Fine _ Location "/ >
> *   **–<使用-权限安卓:name = " Android。允许。互联网"/ >**

**我们将在 **AndroidManifest.xml** 文件中添加使用权限代码。请参见下面的代码**

## **可扩展标记语言**

```kt
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"

    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
    <uses-permission android:name="android.permission.INTERNET"/>
    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

****第五步:构建布局****

**我们将在应用程序的唯一屏幕中添加一个 [**按钮**](https://www.geeksforgeeks.org/button-in-kotlin/) 和 [**文本视图**](https://www.geeksforgeeks.org/textview-in-kotlin/) 。当用户点击按钮时，该位置的温度和城市将显示在文本视图中。请参见下面的代码:**

## **可扩展标记语言**

```kt
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/weather_background"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/btVar1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:background="@drawable/btn_bg6"
        android:padding="10dp"
        android:text="Get Weather"
        android:textSize="20dp" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_margin="40dp"
        android:layout_marginBottom="100dp"
        android:fontFamily="sans-serif-black"
        android:text="Get temperature here"
        android:textColor="#F6F8F5"
        android:textSize="25dp"
        android:textStyle="bold" />

</RelativeLayout>
```

****第六步:获取设备坐标****

**在这一步中，我们将使用谷歌播放服务获得设备的最后位置–**

*   **通过在 SDK 管理器中下载组件来设置 google play 服务。**
*   **在 build.gradle 中为位置添加依赖项–“**实现****com . Google . Android . GMS:play-services-location:17 . 1 . 0”**，版本可能会在以后更改。**
*   **在 **onCreate()** 方法中，创建一个**融合位置提供者客户端**的实例。**
*   **之后使用 **lastlocation()** 方法调用最后一个位置。请参见第 5 步后的科特林代码。**

****第七步:获取 JSON 后解析****

**要获取 **JSON** 我们需要使用 [**凌空**](https://www.geeksforgeeks.org/volley-library-in-android/) 库进行 HTTP 客户端请求**

*   **在 gradle app 文件中添加 **'implementation com.android .凌空:凌空:1.1.1'** 。**
*   **为 JSON 创建 http。例如–**“https://API . weather bit . io/v 2.0/current？”+" lat =+位置？。纬度+”&lon =“+位置？。经度+ " &键=+API _ id1。**这里我们已经生成了 API 键以及位置坐标。**
*   **从这个网址发出请求并获取数据。**

****步骤 8:使用 MainActivity.kt 文件****

**转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。**

## **我的锅**

```kt
import android.annotation.SuppressLint
import android.location.Location
import android.os.Bundle
import android.util.Log
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity
import com.android.volley.Request
import com.android.volley.Response
import com.android.volley.toolbox.StringRequest
import com.android.volley.toolbox.Volley
import com.google.android.gms.location.FusedLocationProviderClient
import com.google.android.gms.location.LocationServices
import kotlinx.android.synthetic.main.activity_main.*
import org.json.JSONObject

class MainActivity : AppCompatActivity() {

    // weather url to get JSON
    var weather_url1 = ""

    // api id for url
    var api_id1 = "030314b750cc43e7b39e503dfe37150c"

    private lateinit var textView: TextView
    private lateinit var fusedLocationClient: FusedLocationProviderClient
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // link the textView in which the 
        // temperature will be displayed
        textView = findViewById(R.id.textView)

        // create an instance of the Fused
        // Location Provider Client
        fusedLocationClient = LocationServices.getFusedLocationProviderClient(this)
        Log.e("lat", weather_url1)

        // on clicking this button function to
        // get the coordinates will be called
        btVar1.setOnClickListener {
            Log.e("lat", "onClick")
            // function to find the coordinates
            // of the last location
            obtainLocation()
        }
    }

    @SuppressLint("MissingPermission")
    private fun obtainLocation() {
        Log.e("lat", "function")
        // get the last location
        fusedLocationClient.lastLocation
            .addOnSuccessListener { location: Location? ->
                // get the latitude and longitude
                // and create the http URL
                weather_url1 = "https://api.weatherbit.io/v2.0/current?" + "lat=" + location?.latitude + "&lon=" + location?.longitude + "&key=" + api_id1
                Log.e("lat", weather_url1.toString())
                // this function will
                // fetch data from URL
                getTemp()
            }
    }

    fun getTemp() {
        // Instantiate the RequestQueue.
        val queue = Volley.newRequestQueue(this)
        val url: String = weather_url1
        Log.e("lat", url)

        // Request a string response 
        // from the provided URL.
        val stringReq = StringRequest(Request.Method.GET, url,
            Response.Listener<String> { response ->
                Log.e("lat", response.toString())

                // get the JSON object
                val obj = JSONObject(response)

                // get the Array from obj of name - "data"
                val arr = obj.getJSONArray("data")
                Log.e("lat obj1", arr.toString())

                // get the JSON object from the 
                // array at index position 0
                val obj2 = arr.getJSONObject(0)
                Log.e("lat obj2", obj2.toString())

                // set the temperature and the city
                // name using getString() function
                textView.text = obj2.getString("temp") + " deg Celcius in " + obj2.getString("city_name")
            },
            // In case of any error
            Response.ErrorListener { textView!!.text = "That didn't work!" })
        queue.add(stringReq)
    }
}
```

### ****输出:****

> ****注意:**在运行应用程序之前，请确保设备中的位置已打开，并且应用程序可以访问该位置。**

**![](img/44ad085de58bf0f400cf01582dcfb523.png)**

****github link:**[https://github . com/njdunk 07/NJ-weather-gfg](https://github.com/njdunk07/NJ-Weather-GFG)**