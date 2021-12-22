# 使用 Jetpack Compose 的安卓动画闪屏

> 原文:[https://www . geesforgeks . org/animated-闪屏-in-Android-use-jet pack-compose/](https://www.geeksforgeeks.org/animated-splash-screen-in-android-using-jetpack-compose/)

[Jetpack Compose](https://www.geeksforgeeks.org/basics-of-jetpack-compose-in-android/) 是安卓的高级工具包，用于以非常简单的形式创建唯物主义 UI。在安卓工作室中，它不需要任何类型的 XML 文件，也有助于创建本地应用程序。它最近在安卓工作室北极狐版本中推出。喷气背包合成函数声明为:

```kt
@Composable
fun MessageCard(name: String) {
    Text(text = "Hello $name!")
}
```

预览合成功能:

```kt
@Preview
@Composable
fun PreviewMessageCard() {
    MessageCard("Android")
}
```

### **闪屏**

[闪屏](https://www.geeksforgeeks.org/how-to-create-a-splash-screen-in-android-using-kotlin/)通常是通过应用程序的徽标或名称来表示您的应用程序的第一个屏幕。它会停留几秒钟，然后自动引导您进入主屏幕。您可以使用您的徽标或任何种类的信息文本来表示您的应用程序。

### **动画闪屏**

动画闪屏对用户来说看起来很有吸引力，因为徽标或任何类型的文本都可以被动画化以使其更有趣。Jetpack Compose 提供了多种 API 来决定要执行哪些动画。在这个项目中，我们将使用 Animatable API 来实现我们的闪屏。您可以根据自己的喜好自定义动画效果和延迟时间。

### **使用喷气背包合成的动画闪屏**

下面给出了一个示例视频，以了解我们将在本文中做什么。注意，我们将使用**喷气背包合成**来实现这个项目。

<video class="wp-video-shortcode" id="video-675527-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210903195433/SplashScreenJC.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210903195433/SplashScreenJC.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210903195433/SplashScreenJC.mp4)</video>

**要求:**

*   安卓工作室北极狐版
*   我的锅
*   图像(.png)

### **分步实施**

**第一步:创建新项目**

使用空撰写活动在安卓工作室创建一个新项目，选择语言为 **Kotlin** 。点击**完成**。

**第二步:添加依赖关系**

将导航依赖项添加到位于渐变脚本文件夹中的 [build.gradle(:app](https://www.geeksforgeeks.org/android-build-gradle/) )文件中。

> 实现“androidx . navigation:navigation-compose:2 . 4 . 0-alpha 06”

**第三步:将图像添加到可绘制文件夹**

添加图像/徽标(。png)到可绘制文件夹中。图像的命名约定应该是小写的，没有任何符号、数字或空格。

**第 4 步:使用 MainActivity.kt 文件**

创建用于导航的可组合函数

## 我的锅

```kt
@Composable
fun Navigation() {
    val navController = rememberNavController()
    NavHost(navController = navController,
        startDestination = "splash_screen") {
        composable("splash_screen") {
            SplashScreen(navController = navController)
        }
        // Main Screen
        composable("main_screen") {
            Box(modifier = Modifier.fillMaxSize(), contentAlignment = Alignment.Center) {
                Text(text = "Main Screen", color = Color.Black, fontSize = 24.sp)
            }
        }
    }
}
```

为闪屏创建可组合的函数

## 我的锅

```kt
@Composable
fun SplashScreen(navController: NavController) {
    val scale = remember {
        androidx.compose.animation.core.Animatable(0f)
    } 

    // AnimationEffect
    LaunchedEffect(key1 = true) {
        scale.animateTo(
            targetValue = 0.7f,
            animationSpec = tween(
                durationMillis = 800,
                easing = {
                    OvershootInterpolator(4f).getInterpolation(it)
                })
        )
        delay(3000L)
        navController.navigate("main_screen")
    } 

    // Image
    Box(contentAlignment = Alignment.Center,
        modifier = Modifier.fillMaxSize()) {
            Image(painter = painterResource(id = R.drawable.gfglogo),
                contentDescription = "Logo",
                modifier = Modifier.scale(scale.value))
    }
}
```

转到 **MainActivity.kt** 文件，参考以下代码。以下是 **MainActivity.kt** 文件的完整代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
package com.example.splashscreenjc

import android.os.Bundle
import android.view.animation.OvershootInterpolator
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.animation.core.tween
import androidx.compose.foundation.Image
import androidx.compose.foundation.layout.Box
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.material.Surface
import androidx.compose.material.Text
import androidx.compose.runtime.Composable
import androidx.compose.runtime.LaunchedEffect
import androidx.compose.runtime.remember
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.draw.scale
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.unit.sp
import androidx.navigation.NavController
import androidx.navigation.compose.NavHost
import androidx.navigation.compose.composable
import androidx.navigation.compose.rememberNavController
import kotlinx.coroutines.delay

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
                Surface(color = Color.White, modifier = Modifier.fillMaxSize()) {
                    com.example.splashscreenjc.Navigation()
            }
        }
    }
}
@Composable
fun Navigation() {
    val navController = rememberNavController()
    NavHost(navController = navController,
        startDestination = "splash_screen") {
        composable("splash_screen") {
            SplashScreen(navController = navController)
        }

        // Main Screen
        composable("main_screen") {
            Box(modifier = Modifier.fillMaxSize(), contentAlignment = Alignment.Center) {
                Text(text = "Main Screen", color = Color.Black, fontSize = 24.sp)
            }
        }
    }
}
@Composable
fun SplashScreen(navController: NavController) {
    val scale = remember {
        androidx.compose.animation.core.Animatable(0f)
    }

    // Animation
    LaunchedEffect(key1 = true) {
        scale.animateTo(
            targetValue = 0.7f,
              // tween Animation
            animationSpec = tween(    
                durationMillis = 800,
                easing = {
                    OvershootInterpolator(4f).getInterpolation(it)
                }))
        // Customize the delay time
        delay(3000L) 
        navController.navigate("main_screen")
    }

    // Image
    Box(contentAlignment = Alignment.Center,
        modifier = Modifier.fillMaxSize()) {
            // Change the logo
            Image(painter = painterResource(id = R.drawable.gfglogo), 
                contentDescription = "Logo",
                modifier = Modifier.scale(scale.value))
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-675527-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210903195433/SplashScreenJC.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210903195433/SplashScreenJC.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210903195433/SplashScreenJC.mp4)</video>