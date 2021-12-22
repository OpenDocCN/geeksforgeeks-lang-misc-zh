# 在安卓系统中用示例

进行 PulseCountDown

> 原文:[https://www . geeksforgeeks . org/pulseecountdown-in-Android-with-example/](https://www.geeksforgeeks.org/pulsecountdown-in-android-with-example/)

**安卓系统中的 pulse untdown**是 CountDownTimer 的替代品。CountDownTimer 是一种精确的计时器，可用于网站或博客，以显示任何特殊事件的倒计时，如生日或周年纪念日。实现 pulse ountdown 而不是 CountDownTimer 是非常容易的，因为 pulse ountdown 提供了一个带有一些漂亮动画的默认布局。默认情况下，**脉冲卸载**的**开始值**为 10，**结束值**为 0。假设需要一个**问答软件**，在里面加上回答问题的时间限制，就可以使用**pulse uncdown**。

![pulse countdown](img/debe0e504443a2513a564e2e2d59c824.png)

### 属性表

<figure class="table">

| **XML 属性** | **方法**

 | **功能** |
| pc_startValue | startValue（int value） | 脉冲卸载的起始值(默认为 10) |
| pc_endValue | 结束值(整数值) | 倒计时停止前的值(默认为 0) |
| – | 开始(回调:()->单位= {}) | 开始倒计时 |

</figure>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。

> **注意:**最低 SDK 版本必须大于 **API 22:安卓 5.1(棒棒糖)**才能实现这个依赖。因此，在创建新项目时，请选择合适的软件开发工具包。

**第二步:添加依赖关系**

导航到**渐变脚本>构建.渐变(模块:应用)**，并在依赖项部分添加以下依赖项。

> 实现' com . gus akov:pulse-倒计时:1.1.0-rc1 '

**步骤 3:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。在这个文件中添加 **脉冲卸载** 视图和一个开始按钮到布局。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```kt
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <com.gusakov.library.PulseCountDown
        android:id="@+id/pulseCountDown"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="5"
        android:textSize="100sp"
        app:pc_startValue="5"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="188dp"
        android:text="Start Countdown"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**步骤 4:使用** **主活动文件**

转到**主活动**文件，参考以下代码。在此文件中，将 **onClickListner()** 方法添加到按钮以启动 PulseCountDownView。以下是**主活动**文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.view.View
import android.widget.Toast
import com.gusakov.library.start
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // when the user tap on the button this
        // function get invoked automatically.
        button.setOnClickListener(View.OnClickListener {
            pulseCountDown.start {
                // when countdown ends a toast
                // will be shown to user
                Toast.makeText(this,
                "Course Alert!", Toast.LENGTH_LONG).show()
            }
        })
    }
}
```

## Java 语言(一种计算机语言，尤用于创建网站)

```kt
import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

import com.gusakov.library.PulseCountDown;
import com.gusakov.library.java.interfaces.OnCountdownCompleted;

public class MainActivity extends AppCompatActivity {

    // creating object of Button and PulseCountDown
    private Button buttonStart;
    private PulseCountDown pulseCountDown;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // initialising objects
        buttonStart=(Button)findViewById(R.id.buttonStart);
        pulseCountDown=(PulseCountDown)findViewById(R.id.pulseCountDown);

        // button OnClickListener
        buttonStart.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                // start countdown and add OnCountdownCompleted
                pulseCountDown.start(new OnCountdownCompleted() {
                    @Override
                    public void completed() {
                        // show simple toast when countdown completed
                        Toast.makeText(MainActivity.this, "Pulse Count Completed :)", Toast.LENGTH_SHORT).show();
                    }
                });
            }
        });
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-459519-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20200717103908/Record_2020-07-17-10-37-56_f07c2d9688030c881824144c337bea4e1.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20200717103908/Record_2020-07-17-10-37-56_f07c2d9688030c881824144c337bea4e1.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20200717103908/Record_2020-07-17-10-37-56_f07c2d9688030c881824144c337bea4e1.mp4)</video>