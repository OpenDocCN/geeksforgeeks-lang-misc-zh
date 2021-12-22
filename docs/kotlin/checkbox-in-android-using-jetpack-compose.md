# 安卓系统中使用喷气背包合成的复选框

> 原文:[https://www . geesforgeks . org/checkbox-in-Android-use-jet pack-compose/](https://www.geeksforgeeks.org/checkbox-in-android-using-jetpack-compose/)

[复选框](https://www.geeksforgeeks.org/how-to-use-checkbox-in-android/)是一个可组合的函数，用于表示安卓系统中任何项目的两种状态。它用于区分项目和项目列表。在这篇文章中，我们将看看简单复选框在安卓系统中使用[喷气背包合成的实现。](https://www.geeksforgeeks.org/basics-of-jetpack-compose-in-android/)

### **复选框**的属性

<figure class="table">

| 

属性

 | 

使用

 |
| --- | --- |
| 检查 | 这用于在应用程序启动时设置我们的复选框已选中或未选中。 |
| oncheckedchanged | 这是一个回调，当事件发生变化时，无论复选框是选中还是未选中，它都会收到。 |
| 修饰语 | 这用于在填充、边距和其他属性的意义上美化我们的复选框。 |
| 颜色 | 此参数用于在默认情况下为我们的复选框添加颜色，前提是复选框颜色是应用程序主题中的辅助颜色。 |

</figure>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室金丝雀版本中创建新项目，请参考[如何使用 Jetpack Compose 在安卓工作室金丝雀版本中创建新项目。](https://www.geeksforgeeks.org/how-to-create-a-new-project-in-android-studio-canary-version-with-jetpack-compose/)

**步骤 2:使用 MainActivity.kt 文件**

导航到**应用程序> java >你的应用程序的包名，打开 MainActivity.kt** 文件。在该文件中添加下面的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```
import android.graphics.drawable.shapes.Shape
import android.media.Image
import android.os.Bundle
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.compose.foundation.*
import androidx.compose.foundation.Text
import androidx.compose.foundation.layout.*
import androidx.compose.foundation.shape.CircleShape
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.foundation.text.KeyboardOptions
import androidx.compose.material.*
import androidx.compose.material.Icon
import androidx.compose.material.icons.Icons
import androidx.compose.material.icons.filled.AccountCircle
import androidx.compose.material.icons.filled.Info
import androidx.compose.material.icons.filled.Menu
import androidx.compose.material.icons.filled.Phone
import androidx.compose.runtime.*
import androidx.compose.runtime.savedinstancestate.savedInstanceState
import androidx.compose.ui.Alignment
import androidx.compose.ui.layout.ContentScale
import androidx.compose.ui.platform.setContent
import androidx.compose.ui.res.imageResource
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import com.example.gfgapp.ui.GFGAppTheme
import androidx.compose.ui.Modifier
import androidx.compose.ui.draw.clip
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.graphics.SolidColor
import androidx.compose.ui.platform.ContextAmbient
import androidx.compose.ui.platform.testTag
import androidx.compose.ui.res.colorResource
import androidx.compose.ui.semantics.SemanticsProperties.ToggleableState
import androidx.compose.ui.text.TextStyle
import androidx.compose.ui.text.font.FontFamily
import androidx.compose.ui.text.input.*
import androidx.compose.ui.unit.Dp
import androidx.compose.ui.unit.TextUnit

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            Column {
                // in below line we are 
                  // calling a checkbox method. 
                SimpleCheckboxComponent()
            }
        }
    }
}

@Preview(showBackground = true)
@Composable
fun DefaultPreview() {
    GFGAppTheme {
        SimpleCheckboxComponent();
    }
}

@Composable
fun SimpleCheckboxComponent() {
    // in below line we are setting
     // the state of our checkbox.
    val checkedState = remember { mutableStateOf(true) }
    // in below line we are displaying a row
      // and we are creating a checkbox in a row. 
    Row {
        Checkbox(
            // below line we are setting 
              // the state of checkbox.
            checked = checkedState.value,
            // below line is use to add padding
              // to our checkbox. 
            modifier = Modifier.padding(16.dp),
            // below line is use to add on check 
              // change to our checkbox. 
            onCheckedChange = { checkedState.value = it },
        )
        // below line is use to add text to our check box and we are 
         // adding padding to our text of checkbox
        Text(text = "Checkbox Example", modifier = Modifier.padding(16.dp))
    }
}
```

现在运行您的应用程序，并查看应用程序的输出。

### **输出:**

<video class="wp-video-shortcode" id="video-546999-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210123195048/Checkbox-in-Android-using-Jetpack-Compose.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210123195048/Checkbox-in-Android-using-Jetpack-Compose.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210123195048/Checkbox-in-Android-using-Jetpack-Compose.mp4)</video>