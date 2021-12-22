# 建立一个安卓应用来检查一个号码是不是阿姆斯特朗

> 原文:[https://www . geesforgeks . org/build-an-Android-app-to-check-a-number-is-Armstrong-or-not/](https://www.geeksforgeeks.org/build-an-android-app-to-check-a-number-is-armstrong-or-not/)

**阿姆斯特朗的号码是多少？**如果一个数的位数之和与该数的位数之和的幂相加，则称该数为阿姆斯特朗数。给定一个数 x，确定给定的数是否是阿姆斯特朗的数。 **n 位数**的正整数称为**阶 n** 的阿姆斯壮数(阶是位数)if。

```kt
abcd... = pow(a,n) + pow(b,n) + pow(c,n) + pow(d,n) + .... 
```

**示例:**

```kt
153 is an Armstrong number.
1*1*1 + 5*5*5 + 3*3*3 = 153

120 is not an Armstrong number.
1*1*1 + 2*2*2 + 0*0*0 = 9

1253 is not an Armstrong Number
1*1*1*1 + 2*2*2*2 + 5*5*5*5 + 3*3*3*3 = 723

1634 is an Armstrong Number
1*1*1*1 + 6*6*6*6 + 3*3*3*3 + 4*4*4*4 = 1634
```

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择 **Java** 作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:background="@color/teal_200">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Armstrong Number or Not"
        android:textColor="@color/black"
        android:textSize="26sp"
        app:layout_constraintBottom_toTopOf="@+id/textView"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.491" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Enter a number to check Armstrong Number"
        android:textColor="@color/black"
        android:textSize="18sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintHorizontal_bias="0.494"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.4" />

    <EditText
        android:id="@+id/etNum"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:hint="ENTER THE NUMBER"
        android:inputType="number"
        app:layout_constraintEnd_toEndOf="@+id/textView"
        app:layout_constraintStart_toStartOf="@+id/textView"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <Button
        android:id="@+id/btnCheck"
        android:layout_width="149dp"
        android:layout_height="50dp"
        android:layout_margin="10dp"
        android:layout_marginTop="16dp"
        android:backgroundTint="@color/black"
        android:text="Check"
        android:textColor="@color/teal_700"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="@+id/etNum"
        app:layout_constraintHorizontal_bias="0.496"
        app:layout_constraintStart_toStartOf="@+id/etNum"
        app:layout_constraintTop_toBottomOf="@+id/etNum"
        app:layout_constraintVertical_bias="0.113" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

**第三步:使用**T2【主活动. kt】文件

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。这里我们将绑定视图并编写应用程序的逻辑。

## 我的锅

```kt
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.Toast
import java.lang.Math.pow
import kotlin.math.pow

class MainActivity : AppCompatActivity() {
  lateinit var btnCheck : Button
  lateinit var etNum : EditText

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        supportActionBar?.hide()

        // Binding the views
        btnCheck = findViewById(R.id.btnCheck)
        etNum = findViewById(R.id.etNum)

        btnCheck.setOnClickListener {
            val n = etNum.text.toString().length
            val num = etNum.text.toString().toInt()
            var temp = num
            var result = 0

            while (temp != 0){
                val remainder = temp % 10

                result += (remainder.toDouble().pow(n.toDouble())).toInt()

                temp /= 10
            }
            if (result == num)
                Toast.makeText(this,"Armstrong Number",Toast.LENGTH_SHORT).show()
            else
                Toast.makeText(this,"Not an Armstrong Number",Toast.LENGTH_SHORT).show()
        }
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-692753-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20211001011948/video_2021-10-01_01-16-35.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20211001011948/video_2021-10-01_01-16-35.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20211001011948/video_2021-10-01_01-16-35.mp4)</video>