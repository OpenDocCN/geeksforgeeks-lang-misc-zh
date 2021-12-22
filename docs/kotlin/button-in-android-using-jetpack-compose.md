# 安卓系统中使用喷气背包合成的按钮

> 原文:[https://www . geesforgeks . org/button-in-Android-use-jet pack-compose/](https://www.geeksforgeeks.org/button-in-android-using-jetpack-compose/)

[**【喷气背包作曲】**](https://www.geeksforgeeks.org/basics-of-jetpack-compose-in-android/) 是谷歌提供的全新工具包。这对于设计漂亮的用户界面设计非常有用。一个[按钮](https://www.geeksforgeeks.org/button-in-kotlin/)是 Android 中的一个 UI 组件，用来在不同的屏幕之间导航。在按钮的帮助下，用户可以与您的应用程序交互，并在您的应用程序中执行多个操作。在本文中，我们将看一下使用 Jetpack compose 在 Android 中实现按钮。

### **按钮部件**的属性

<figure class="table">

| 

属性

 | 

描述

 |
| --- | --- |
| 点击 | 当用户单击按钮时执行操作。 |
| 修饰语 | 这个参数用来给我们的按钮添加填充。 |
| 使能够 | 启用或禁用按钮。 |
| 边界 | 这个参数用来给我们的按钮添加边框。 |
| 形状 | 该参数用于为我们的按钮添加形状。 |
| 文本() | 此参数将用于添加显示在按钮上的文本。 |

</figure>

### **分步实施**

**步骤 1:创建新项目。**

要在安卓工作室加那利版本中创建新项目，请参考[如何使用 Jetpack Compose](https://www.geeksforgeeks.org/how-to-create-a-new-project-in-android-studio-canary-version-with-jetpack-compose/) 在安卓工作室加那利版本中创建新项目。

**步骤 2:使用 MainActivity.kt 文件**

导航到**应用程序> java >你的应用程序的包名，打开 MainActivity.kt 文件**。在该文件中添加下面的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
import android.graphics.drawable.shapes.Shape
import android.media.Image
import android.os.Bundle
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.compose.foundation.BorderStroke
import androidx.compose.foundation.Image
import androidx.compose.foundation.Text
import androidx.compose.foundation.layout.*
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.foundation.text.KeyboardOptions
import androidx.compose.material.*
import androidx.compose.material.icons.Icons
import androidx.compose.material.icons.filled.AccountCircle
import androidx.compose.material.icons.filled.Info
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
import androidx.compose.ui.res.colorResource
import androidx.compose.ui.text.TextStyle
import androidx.compose.ui.text.font.FontFamily
import androidx.compose.ui.text.input.*
import androidx.compose.ui.unit.Dp
import androidx.compose.ui.unit.TextUnit

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            GFGAppTheme {
                // A surface container using the 'background'
                  // color from the theme
                Surface(color = MaterialTheme.colors.background) {
                    // at below line we are calling
                      // our function for button.
                    MyButton();
                }
            }
        }
    }
}

// @Preview function is use to see preview
// for our composable function in preview section.
@Preview(showBackground = true)
@Composable
fun DefaultPreview() {
    GFGAppTheme {
          // we are passing our composable
        // function to display its preview.
        MyButton();
    }
}

@Composable
fun MyButton() {

    Column(
            // we are using column to align our
            // imageview to center of the screen.
            modifier = Modifier.fillMaxWidth().fillMaxHeight(),

            // below line is used for specifying
            // vertical arrangement.
            verticalArrangement = Arrangement.Center,

            // below line is used for specifying
            // horizontal arrangement.
            horizontalAlignment = Alignment.CenterHorizontally,
            ) {
        // below line is use to get
        // the context for our app.
        val context = ContextAmbient.current

        // below line is use to create a button.
        Button(
                // below line is use to add onclick
                // parameter for our button onclick
                onClick = {
                    // when user is clicking the button
                    // we are displaying a toast message.
                    Toast.makeText(context, "Welcome to Geeks for Geeks", Toast.LENGTH_LONG).show()
                },
                // in below line we are using modifier
                // which is use to add padding to our button
                modifier = Modifier.padding(all = Dp(10F)),

                // below line is use to set or
                // button as enable or disable.
                enabled = true,

                // below line is use to
                // add border to our button.
                border = BorderStroke(width = 1.dp, brush = SolidColor(Color.Blue)),

                // below line is use to add shape for our button.
                shape = MaterialTheme.shapes.medium,
        )
        // below line is use to
        // add text on our button
        {
            Text(text = "Geeks for Geeks", color = Color.White)
        }
    }
}
```

### **输出:**

<video class="wp-video-shortcode" id="video-539287-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210102222930/Screenrecorder-2021-01-02-22-26-59-652.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210102222930/Screenrecorder-2021-01-02-22-26-59-652.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210102222930/Screenrecorder-2021-01-02-22-26-59-652.mp4)</video>