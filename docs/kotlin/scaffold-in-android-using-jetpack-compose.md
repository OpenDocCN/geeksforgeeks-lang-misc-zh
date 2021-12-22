# 安卓系统中使用 Jetpack Compose 的支架

> 原文:[https://www . geesforgeks . org/scaffold-in-Android-using-jet pack-compose/](https://www.geeksforgeeks.org/scaffold-in-android-using-jetpack-compose/)

有很多应用包含 [TopAppBar](https://www.geeksforgeeks.org/topappbar-in-android-using-jetpack-compose/) 、[抽屉](https://www.geeksforgeeks.org/navigation-drawer-in-android/)、[浮动动作按钮](https://www.geeksforgeeks.org/floating-action-button-fab-in-android-with-example/)、 [BottomAppBar](https://www.geeksforgeeks.org/how-to-add-a-floating-action-button-to-bottom-navigation-bar-in-android/) (底部导航形式)、Snackbar。虽然您可以在一个应用程序中单独设置所有这些，但需要很多设置。喷气背包组合提供**支架组合**，可以节省大量时间。它就像一个预建的模板。在本文中，我们将看到如何在 android 中使用 Jetpack Compose 设置 Scaffold。我们将构建一个演示脚手架可组装性的基本应用程序，下面是展示该应用程序的视频。

<video class="wp-video-shortcode" id="video-648014-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210714223839/screen-20210714-211820.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210714223839/screen-20210714-211820.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210714223839/screen-20210714-211820.mp4)</video>

**先决条件:**

*   [科特林](https://www.geeksforgeeks.org/kotlin-programming-language/)知识。
*   知识[喷气背包合成](https://www.geeksforgeeks.org/basics-of-jetpack-compose-in-android/)。

### **分步实施**

**步骤 1:创建 TopAppBar**

打开 **MainActivity.kt** 并创建一个 TopBar 可组合函数，它将是我们在脚手架中 TopAppBar 的包装器。

## 我的锅

```
// A function which will receive a 
// callback to trigger to opening the drawer
@Composable
fun TopBar(onMenuClicked: () -> Unit) {

    // TopAppBar Composable
    TopAppBar(
        // Provide Title
        title = {
            Text(text = "Scaffold||GFG", color = Color.White)
        },
        // Provide the navigation Icon (Icon on the left to toggle drawer)
        navigationIcon = {
            Icon(
                imageVector = Icons.Default.Menu,
                contentDescription = "Menu",

                // When clicked trigger onClick 
                // Callback to trigger drawer open
                modifier = Modifier.clickable(onClick = onMenuClicked), 
                tint = Color.White
            )
        },
        // background color of topAppBar
        backgroundColor = Color(0xFF0F9D58)
    )
}
```

**第二步:创建底部应用栏**

打开 **MainActivity.kt** 并创建一个可组合的底部条。这将是一个简单的直接在我们的应用程序。

## 我的锅

```
@Composable
fun BottomBar() {
    // BottomAppBar Composable
    BottomAppBar(
        backgroundColor = Color(0xFF0F9D58)
    ) {
        Text(text = "Bottom App Bar", color = Color.White)
    }
}
```

**第三步:创建抽屉内容**

打开 **MainActivity.kt** 并创建一个可组合的抽屉，它将是我们脚手架中的抽屉。

## 我的锅

```
@Composable
fun Drawer() {
    // Column Composable
    Column(
        Modifier
            .background(Color.White)
            .fillMaxSize()
    ) {
        // Repeat is a loop which
        // takes count as argument 
        repeat(5) { item ->
            Text(text = "Item number $item", modifier = Modifier.padding(8.dp), color = Color.Black)
        }
    }
}
```

**步骤 4:** **创建支架的身体部分**

创建另一个可组合函数 **Body。**这将是一个简单的文本组合在我们的应用程序中。在其他应用程序中实现时，一定要定制它。

## 我的锅

```
@Composable
fun Body() {
    Column(
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally,
        modifier = Modifier
            .fillMaxSize()
            .background(Color.White)
    ) {
        Text(text = "Body Content", color = Color(0xFF0F9D58))
    }
}
```

既然我们需要的所有组件都完成了，让我们来看看脚手架部分。

**第五步:使用脚手架**

因为我们已经创建了所有的组件，所以 Scaffold 代码将非常简单，并且不言自明。

## 我的锅

```
@Composable
fun ScaffoldExample() {

    // create a scaffold state, set it to close by default
    val scaffoldState = rememberScaffoldState(rememberDrawerState(DrawerValue.Closed))

    // Create a coroutine scope. Opening of 
    // Drawer and snackbar should happen in
    // background thread without blocking main thread
    val coroutineScope = rememberCoroutineScope()

    // Scaffold Composable
    Scaffold(

        // pass the scaffold state
        scaffoldState = scaffoldState,

        // pass the topbar we created
        topBar = {
            TopBar(
                // When menu is clicked open the
                // drawer in coroutine scope
                onMenuClicked = {
                    coroutineScope.launch {
                        // to close use -> scaffoldState.drawerState.close()
                        scaffoldState.drawerState.open()
                    }
                })
        },

        // pass the bottomBar
        // we created
        bottomBar = { BottomBar() },

        // Pass the body in
        // content parameter
        content = {
            Body()
        },

        // pass the drawer
        drawerContent = {
            Drawer()
        },

        floatingActionButton = {
            // Create a floating action button in 
            // floatingActionButton parameter of scaffold
            FloatingActionButton(

                onClick = {
                    // When clicked open Snackbar
                    coroutineScope.launch {
                        when (scaffoldState.snackbarHostState.showSnackbar(
                            // Message In the snackbar
                            message = "Snack Bar", 
                            actionLabel = "Dismiss"
                        )) {
                            SnackbarResult.Dismissed -> {
                                // do something when 
                               // snack bar is dismissed
                            }

                            SnackbarResult.ActionPerformed -> {
                            // when it appears
                            }
                        }
                    }
                }) {
                // Simple Text inside FAB
                Text(text = "X")
            }
        }
    )
}
```

现在从**主活动**类中的 setContent 调用这个可组合的

## 我的锅

```
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent { 
            Surface(color = Color.White) {
                // Scaffold we created
                ScaffoldExample()
            }         
        }
    }
}
```

现在运行该应用程序，并看到它的工作。

**完整代码:**

## 我的锅

```
package com.gfg.scaffoldjetpackcompose

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.background
import androidx.compose.foundation.clickable
import androidx.compose.foundation.layout.Arrangement
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.padding
import androidx.compose.material.*
import androidx.compose.material.icons.Icons
import androidx.compose.material.icons.filled.Menu
import androidx.compose.runtime.Composable
import androidx.compose.runtime.rememberCoroutineScope
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.unit.dp
import kotlinx.coroutines.launch

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            Surface(color = Color.White) {
                // Scaffold we created
                ScaffoldExample()
            }
        }
    }
}

@Composable
fun ScaffoldExample() {

    // create a scaffold state, set it to close by default
    val scaffoldState = rememberScaffoldState(rememberDrawerState(DrawerValue.Closed))

    // Create a coroutine scope. Opening of Drawer
    // and snackbar should happen in background 
    // thread without blocking main thread
    val coroutineScope = rememberCoroutineScope()

    // Scaffold Composable
    Scaffold(

        // pass the scaffold state
        scaffoldState = scaffoldState,

        // pass the topbar we created
        topBar = {
            TopBar(
                // When menu is clicked open the
                // drawer in coroutine scope
                onMenuClicked = {
                    coroutineScope.launch {
                        // to close use -> scaffoldState.drawerState.close()
                        scaffoldState.drawerState.open()
                    }
                })
        },

        // pass the bottomBar we created
        bottomBar = { BottomBar() },

        // Pass the body in
        // content parameter
        content = {
            Body()
        },

        // pass the drawer
        drawerContent = {
            Drawer()
        },

        floatingActionButton = {
            // Create a floating action button in
            // floatingActionButton parameter of scaffold
            FloatingActionButton(
                onClick = {
                    // When clicked open Snackbar
                    coroutineScope.launch {
                        when (scaffoldState.snackbarHostState.showSnackbar(
                            // Message In the snackbar
                            message = "Snack Bar", 
                            actionLabel = "Dismiss"
                        )) {
                            SnackbarResult.Dismissed -> {
                                // do something when 
                                // snack bar is dismissed
                            }

                            SnackbarResult.ActionPerformed -> {
                            // when it appears
                            }

                        }
                    }
                }) {
                // Simple Text inside FAB
                Text(text = "X")
            }
        }
    )
}

// A function which will receive a 
// callback to trigger to opening the drawer
@Composable
fun TopBar(onMenuClicked: () -> Unit) {
    // TopAppBar Composable
    TopAppBar(
        // Provide Title
        title = {
            Text(text = "Scaffold||GFG", color = Color.White)
        },
        // Provide the navigation Icon ( Icon on the left to toggle drawer)
        navigationIcon = {
            Icon(
                imageVector = Icons.Default.Menu,
                contentDescription = "Menu",

                   // When clicked trigger onClick 
                  // Callback to trigger drawer open
                modifier = Modifier.clickable(onClick = onMenuClicked),
                tint = Color.White
            )
        },
        // background color of topAppBar
        backgroundColor = Color(0xFF0F9D58)
    )
}

@Composable
fun BottomBar() {
    // BottomAppBar Composable
    BottomAppBar(
        backgroundColor = Color(0xFF0F9D58)
    ) {
        Text(text = "Bottom App Bar", color = Color.White)
    }
}

@Composable
fun Body() {
    Column(
        verticalArrangement = Arrangement.Center,
        horizontalAlignment = Alignment.CenterHorizontally,
        modifier = Modifier
            .fillMaxSize()
            .background(Color.White)
    ) {
        Text(text = "Body Content", color = Color(0xFF0F9D58))
    }
}

@Composable
fun Drawer() {
    // Column Composable
    Column(
        Modifier
            .background(Color.White)
            .fillMaxSize()
    ) {
        // Repeat is a loop which
        // takes count as argument
        repeat(5) { item ->
            Text(text = "Item number $item", modifier = Modifier.padding(8.dp), color = Color.Black)
        }
    }
}
```

**输出:**

<video class="wp-video-shortcode" id="video-648014-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210714223839/screen-20210714-211820.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210714223839/screen-20210714-211820.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210714223839/screen-20210714-211820.mp4)</video>

从 G [到 itHub](https://github.com/sunny52525/GFG-articles/tree/master/ScaffoldJetpackCompose) 获取完整的项目。