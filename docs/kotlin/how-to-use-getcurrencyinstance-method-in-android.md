# 如何在安卓系统中使用 getCurrencyInstance 方法？

> 原文:[https://www . geeksforgeeks . org/使用方法-getcurrency instance-in-method-in-Android/](https://www.geeksforgeeks.org/how-to-use-getcurrencyinstance-method-in-android/)

在安卓系统中，当我们必须格式化任何文本视图的数字时，我们使用“数字格式”类，这是所有格式化方法的基类。因此，不同类型的格式化使用不同的格式化方法。这样，当我们必须为特定的区域设置指定数字时，就会使用 getInstance 方法。例如:getNumberInstance()用于查找整数格式，而 **getPercentInstance()** 用于显示数字是百分比，比如 0.53 到 53%，getCurrencyInstance 用于获取货币格式。我们将在这里讨论。

### **本文我们要构建什么？**

我们将构建一个应用程序，其中我们获得一些数字作为输入，并使用 getcurrencyInstance 方法用货币符号显示它。应用程序的组件。

1.  [编辑文本](https://www.geeksforgeeks.org/android-edittext-in-kotlin/)进行输入
2.  [文本视图](https://www.geeksforgeeks.org/textview-in-kotlin/)进行建议
3.  [按钮](https://www.geeksforgeeks.org/button-in-kotlin/)，点击时显示结果
4.  另一个显示结果的文本视图

让我们看看下面的编码实现。

### **分步实施**

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**步骤 2:使用 activity_main.xml 文件**

导航到**应用程序> res >布局> activity_main.xml** 并将下面的代码添加到该文件中。下面是 **activity_main.xml** 文件的代码。

## 可扩展标记语言

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.appcompat.widget.LinearLayoutCompat
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/teal_200"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/editText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="20dp"
        android:autofillHints="@string/enter_an_amount"
        android:hint="@string/enter_an_amount"
        android:textColor="@color/black"
        android:textSize="30sp"
        android:textStyle="bold" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="20dp"
        android:text="@string/amount"
        android:textColor="@color/black"
        android:textSize="30sp"
        android:textStyle="bold" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="20dp"
        android:onClick="showValue"
        android:text="@string/show_value" />

    <TextView
        android:id="@+id/output"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="20dp"
        android:textColor="@color/black"
        android:textSize="30sp"
        android:textStyle="bold" />

</androidx.appcompat.widget.LinearLayoutCompat>
```

**第 3 步:处理字符串. xml 文件**

导航到 **应用程序> res >值> strings.xml** 并将下面的代码添加到该文件中。下面是 **strings.xml** 文件的代码。

## 可扩展标记语言

```
<resources>
    <string name="app_name">Geeksforgeeks Currency adder</string>
    <string name="amount">Amount you entered with currency sign is</string>
    <string name="show_value">Show Value</string>
    <string name="enter_an_amount">Enter an amount</string>
</resources>
```

**第四步:使用****MainActivity.java 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.os.Bundle
import android.view.View
import android.widget.EditText
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity
import java.util.*

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }

    fun showValue(view: View) {
        // variable editText to get the id of editText
        val editText: EditText = findViewById(R.id.editText)
        // we've id in editText variable, convert it into Int
        val value: String = editText.text.toString()
        // get the currency of local system
        val currency: Currency = Currency.getInstance(Locale.getDefault())
        // store the currency sign in symbol variable
        val symbol: String = currency.symbol
        val message = "$symbol$value"
        // now again find the id of output textView
        val textView: TextView = findViewById(R.id.output)
        // set the message value in it with sign
        // first way
        textView.text = message
        // second way
        // message.also { textView.text = it }
        // following line tells us how we can add any specific currency
        // val newCurrency: Currency = Currency.getInstance("EUR")
        // and everything will be same
    }

}
```

这是我们得到的。

**输出:**

![Output](img/a04d9855de6afdfdcc105afb2f1e35f1.png)

应用程序输出窗口