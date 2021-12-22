# 安卓系统中使用喷气背包合成

的单选按钮

> 原文:[https://www . geesforgeks . org/radio button-in-Android-using-jet pack-compose/](https://www.geeksforgeeks.org/radiobuttons-in-android-using-jetpack-compose/)

[单选按钮](https://www.geeksforgeeks.org/android-how-to-add-radio-buttons-in-an-android-application/)用于从列表中的几个选项列表中仅选择一个特定选项，或者选择其中一个。单选按钮在许多地方用于从两个或多个选项列表中仅选择一个选项。在本文中，我们将看看这个单选按钮在安卓系统中使用[喷气背包合成](https://www.geeksforgeeks.org/basics-of-jetpack-compose-in-android/)的实现。

### **单选按钮的属性**

<figure class="table">

| 属性 | 描述 |
| --- | --- |
| 挑选 | 该属性用于选择单选按钮。 |
| 点击 | 当我们的单选按钮被点击时使用。 |
| 修饰语 | 给我们的单选按钮添加填充。 |

</figure>

### **分步实施**

**第一步:创建新项目**

要在安卓工作室金丝雀版本中创建新项目，请参考[如何使用 Jetpack Compose 在安卓工作室金丝雀版本中创建新项目。](https://www.geeksforgeeks.org/how-to-create-a-new-project-in-android-studio-canary-version-with-jetpack-compose/)

**步骤 2:使用 MainActivity.kt 文件**

导航到**应用程序> java >你的应用程序的包名，打开 MainActivity.kt** 文件。在该文件中添加下面的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.graphics.drawable.shapes.Shape
import android.media.Image
import android.os.Bundle
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.compose.foundation.*
import androidx.compose.foundation.Text
import androidx.compose.foundation.layout.*
import androidx.compose.foundation.selection.selectable
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
                // in below line we are calling
                  // a radio button  method.
                SimpleRadioButtonComponent()
            }
        }
    }
}

@Preview(showBackground = true)
@Composable
fun DefaultPreview() {
    GFGAppTheme {
        SimpleRadioButtonComponent();
    }
}

@Composable
fun SimpleRadioButtonComponent() {
    val radioOptions = listOf("DSA", "Java", "C++")
    val (selectedOption, onOptionSelected) = remember { mutableStateOf(radioOptions[2]) }
    Column(
        // we are using column to align our 
          // imageview to center of the screen.
        modifier = Modifier.fillMaxWidth().fillMaxHeight(),

          // below line is used for
          // specifying vertical arrangement.
        verticalArrangement = Arrangement.Center,

          // below line is used for
          // specifying horizontal arrangement.
        horizontalAlignment = Alignment.CenterHorizontally,
        ) {
        // we are displaying all our
          // radio buttons in column.
        Column {
            // below line is use to set data to
            // each radio button in colums.
            radioOptions.forEach { text ->
                Row(
                    Modifier
                        // using modifier to add max 
                      // width to our radio button.
                        .fillMaxWidth()
                        // below method is use to add
                      // selectable to our radio button.
                        .selectable(
                            // this method is called when
                            // radio button is selected.
                            selected = (text == selectedOption),
                            // below method is called on
                            // clicking of radio button.
                            onClick = { onOptionSelected(text) }
                        )
                         // below line is use to add
                       // padding to radio button.
                        .padding(horizontal = 16.dp)
                ) {
                    // below line is use to get context.
                    val context = ContextAmbient.current

                    // below line is use to
                    // generate radio button
                    RadioButton(
                        // inside this method we are
                          // adding selected with a option.
                        selected = (text == selectedOption),modifier = Modifier.padding(all = Dp(value = 8F)),
                        onClick = {
                            // inide on click method we are setting a
                            // selected option of our radio buttons.
                            onOptionSelected(text)

                            // after clicking a radio button 
                            // we are displaying a toast message.
                            Toast.makeText(context, text, Toast.LENGTH_LONG).show()
                        }
                    )
                    // below line is use to add
                    // text to our radio buttons.
                    Text(
                        text = text,
                        modifier = Modifier.padding(start = 16.dp)
                    )
                }
            }
        }
    }
}
```

现在运行您的应用程序，并查看应用程序的输出。

### **输出:**

<video class="wp-video-shortcode" id="video-547013-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210118232236/Screenrecorder-2021-01-18-23-19-42-380.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210118232236/Screenrecorder-2021-01-18-23-19-42-380.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210118232236/Screenrecorder-2021-01-18-23-19-42-380.mp4)</video>