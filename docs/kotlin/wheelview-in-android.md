# 安卓中的 wheel view

> 原文:[https://www.geeksforgeeks.org/wheelview-in-android/](https://www.geeksforgeeks.org/wheelview-in-android/)

本文在安卓中增加了 **WheelView** 。 **WheelView** 提供了一个非常令人印象深刻的用户界面，允许开发人员创建一个 Wheel 并根据他的需要添加项目。由 WheelView 提供的一些重要标签有 **wheelArcBackgroundColor、wheelAnchorAngle、wheelStartAngle、wheelMode、wheelCenterIcon、**等等。它可以用于用户想要从项目列表中选择项目的地方。假设在银行应用程序中，用户可以选择其银行账户来检查余额、支付历史等，在这种情况下，这可以使用。

**优势:**

*   可以根据要求定制。
*   它为动画提供了改进用户界面的视图。
*   它提供了一个内置的布局，像 [**【自定义对话框】**](https://www.geeksforgeeks.org/how-to-create-a-custom-alertdialog-in-android/) 这样可以用来代替车轮视图的选项没有提供。

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。

**第二步:添加依赖和 JitPack 存储库**

导航到**渐变脚本>构建.渐变(模块:应用)**，并在依赖项部分添加以下依赖项。

> 实现' com . github . PSU Zn:WheelView:1 . 0 . 1 '

将 JitPack 存储库添加到构建文件中。将其添加到 allprojects{ }部分内存储库末尾的 root build.gradle 中。

> *所有项目{*
> 
> *存储库{*
> 
> *……*
> 
> *maven { URL " https://jitpack . io " }*
> 
> *}*
> 
> *}*

添加这个依赖项后，同步您的项目，现在我们将开始实现它。

**步骤 3:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <me.sujanpoudel.wheelview.WheelView
        android:id="@+id/wheel_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_margin="16dp"
        app:wheelDividerStrokeWidth="16dp"
        app:wheelArcBackgroundColor="#F7F8FB"
        app:wheelSelectedArcBackgroundColor="@color/colorPrimary"
        app:wheelCenterIcon="@drawable/ic_baseline_add_24"
        app:wheelCenterIconPadding="16dp"
        app:wheelCenterIconTint="@android:color/white"
        app:wheelAnchorAngle="270"
        app:wheelStartAngle="315"
        app:wheelTextSize="16sp"
        app:wheelSelectedTextColor="#FFF"
        app:wheelTextColor="#000000"
        app:wheelAnimationDuration="800"
        app:wheelMode="ANIMATE_TO_ANCHOR"
        />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**第 4 步:使用** **主活动文件**

转到**主活动**文件，参考以下代码。以下是**主活动**文件的代码。代码中添加了注释，以更详细地理解代码。

## Java 语言(一种计算机语言，尤用于创建网站)

```
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import java.util.Arrays;
import me.sujanpoudel.wheelview.WheelView;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // create a string array  of tiles
        String[] titles={"Bubble Sort", "Quick Sort", "Merge Sort", "Radix Sort"};

        // get the reference of the wheelView
        WheelView wheelView =(WheelView)findViewById(R.id.wheel_view);

        // convert tiles array to list and pass it to setTitles
        wheelView.setTitles(Arrays.asList(titles));
    }
}
```

## 我的锅

```
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import me.sujanpoudel.wheelview.WheelView

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val wheelView = findViewById<WheelView>(R.id.wheel_view)
        wheelView.titles = listOf("Bubble Sort", "Quick Sort", "Merge Sort", "Radix Sort")
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-458491-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20200718132250/Record_2020-07-18-13-21-50_69fa71ed7e998de6cab47c8740bea3c11.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20200718132250/Record_2020-07-18-13-21-50_69fa71ed7e998de6cab47c8740bea3c11.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20200718132250/Record_2020-07-18-13-21-50_69fa71ed7e998de6cab47c8740bea3c11.mp4)</video>