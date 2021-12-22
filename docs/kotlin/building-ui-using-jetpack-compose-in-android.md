# 在安卓中使用 Jetpack Compose 构建用户界面

> 原文:[https://www . geesforgeks . org/building-ui-using-jet pack-compose-in-Android/](https://www.geeksforgeeks.org/building-ui-using-jetpack-compose-in-android/)

Jetpack Compose 是一个现代用户界面工具包，旨在简化安卓用户界面的开发。它由一个反应式编程模型组成，具有柯特林编程语言的简洁性和易用性。它是完全声明性的，因此您可以通过调用一些将数据转换为用户界面层次结构的系列函数来描述您的用户界面。当数据改变或更新时，框架会自动调用这些函数，并为您更新视图。

**先决条件:**

1.  熟悉[柯特林](https://www.geeksforgeeks.org/kotlin-programming-language/)和 [OOP](https://www.geeksforgeeks.org/introduction-of-object-oriented-programming/) 概念
2.  对[喷气背包合成](https://www.geeksforgeeks.org/basics-of-jetpack-compose-in-android/)的基本了解
3.  [Android Studio](https://www.geeksforgeeks.org/android-studio-main-window/)

因此，我们将使用 jetpack compose (Kotlin)创建一个应用程序用户界面。我们最终的 UI 将看起来像它。

<video class="wp-video-shortcode" id="video-706432-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20211026125808/Screen-20211026-093622.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20211026125808/Screen-20211026-093622.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20211026125808/Screen-20211026-093622.mp4)</video>

使用 jetpack compose 构建用户界面很容易，但是使用 XML 就有点难了。所以，让我们一步一步来。

### **分步实施**

**第一步:新建安卓工作室项目**

要使用 Jetpack Compose 在 Android Studio 中创建新项目，请参考:- [如何使用 Jetpack Compose 在 Android Studio Canary 版本中创建新项目。](https://www.geeksforgeeks.org/how-to-create-a-new-project-in-android-studio-canary-version-with-jetpack-compose/)

**第二步:我们给项目增加资源**

有一些资源，如颜色、图像资源、字体和一些小东西。你可以很容易地找到它们，否则只需从 [GitHub repo](https://github.com/alokyd/geekscourse/tree/master/app/src/main/res/drawable) 获取它们。

**第三步:创建一个 Kotlin 类主屏幕**

我们也可以在 MainActivity.kt 中完成同样的任务，但是最好创建另一个文件。最初，我们从顶部开始，所以创建用户界面的第一个标题。有两个带有搜索图标图像的文本。事情很简单，在这种情况下，我们只需创建函数并调用它们，这就是我们如何非常容易地重用代码。

## 我的锅

```
package com.cuid.geekscourse.ui.theme

import androidx.compose.foundation.background
import androidx.compose.foundation.layout.*
import androidx.compose.material.Icon
import androidx.compose.material.MaterialTheme
import androidx.compose.material.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import com.cuid.composeui.R

// here we have created HomeScreen function
// and we will call all functions inside it.
// and finally just call this function from mainActivity
@Composable
fun HomeScreen() {
      // this is the most outer box that will
      // contain all the views,buttons,chips,etc.
    Box(
        modifier = Modifier
            .background(DeepBlue)
            .fillMaxSize()
    ) {
        Column {
              // this is how we call
              // function adding whole UI
            GreetingSection()
        }
 }

@Composable

// and this is the function
// just for creating header at top
fun GreetingSection(
    name: String = "Geeks"
) {
      // here we just arrange the views
    Row(
        horizontalArrangement = Arrangement.SpaceBetween,
        verticalAlignment = Alignment.CenterVertically,
        modifier = Modifier
            .fillMaxWidth()
            .padding(15.dp)
    ) {
        Column(
            verticalArrangement = Arrangement.Center
        ) {
              // heading text view
            Text(
                text = "Good morning, $name",
                style = MaterialTheme.typography.h1
            )
            Text(
                text = "We wish you have a good day!",
                style = MaterialTheme.typography.body1
            )
        }
        // search icon
        Icon(
            painter = painterResource(id = R.drawable.ic_search),
            contentDescription = "Search",
            tint = Color.White,
            modifier = Modifier.size(24.dp)
        )
    }
}
```

**第四步:为芯片创建另一个功能**

正如我们在上面的应用内预览中显示的，我们可以更换芯片。让我们建造它。

## 我的锅

```
// This is how we can create chip seaction at the top of app

@Composable
fun ChipSection(
     // function with single argument
    chips: List<String>
) {
    var selectedChipIndex by remember {
        // it will not update the string
        // but save and it will helpful for us
        mutableStateOf(0)
    }
    LazyRow {
        items(chips.size) {
            Box(
                contentAlignment = Alignment.Center,
                modifier = Modifier
                    .padding(start = 15.dp, top = 15.dp, bottom = 15.dp)
                    .clickable {
                        selectedChipIndex = it
                    }
                    .clip(RoundedCornerShape(10.dp))
                    .background(
                        // this is basic condition for selected chip index
                        if (selectedChipIndex == it) ButtonGreen
                        else DarkerButtonGreen
                    )
                    .padding(15.dp)
            ) {
                Text(text = chips[it], color = TextWhite)
            }
        }
    }
}
```

**第 5 步:创建一个建议提醒功能**

这真的是这个应用非常基本的一部分。

## 我的锅

```
// This function is for suggestion secation

@Composable
fun SuggestionSection(
    color: Color = LightBlue
) {
    Row(   
        verticalAlignment = Alignment.CenterVertically,
        horizontalArrangement = Arrangement.SpaceBetween,
        modifier = Modifier
            .padding(15.dp)
            .clip(RoundedCornerShape(10.dp))
            .background(color)
            .padding(horizontal = 15.dp, vertical = 20.dp)
            .fillMaxWidth()
    ) {
        Column {
            // here are two text views or we can say only text
            Text(
                text = "Daily Coding",
                  // it can be litile bit confusing but
                  // it is just text style alternate
                  // of fontfamily in XML
                style = MaterialTheme.typography.h2

            )
            Text(
                // same as above
                text = "do at least • 3-10 problems / day",
                style = MaterialTheme.typography.body1,
                color = TextWhite
            )
        }
        Box(
            // box containing icon
            contentAlignment = Alignment.Center,
            modifier = Modifier
                .size(40.dp)
                .clip(CircleShape)
                .background(ButtonGreen)
                .padding(10.dp)
        ) {
            Icon(
                painter = painterResource(id = R.drawable.ic_play),
                contentDescription = "Play",
                tint = Color.White,
                modifier = Modifier.size(16.dp)
            )
        }
    }
}
```

下一步应该是课程的卡牌，但这并不容易，或者我们可以说整个 UI 最难的部分**，所以我们会在最后一个之后做。**

*   **让我们创建一个 BottomSection，但是在此之前，为了简单起见，我们应该创建这个类**
*   **因为我们的 BottomSection 元素有两个字段或视图，所以让我们这样做**

****第 6 步:为 ButtomSection(bottomnucontent . kt)创建类****

## **我的锅**

```
package com.cuid.geekscourses

import androidx.annotation.DrawableRes
// having two parameters title and iconid
data class BottomMenuContent(
    val title: String,
    @DrawableRes val iconId: Int
)
```

****第 7 步:为按钮部分**创建功能**

## **我的锅**

```
@Composable
// this function tells us that
// how menu item should look like
fun BottomMenu(
    items: List<BottomMenuContent>,
    modifier: Modifier = Modifier,
    activeHighlightColor: Color = ButtonGreen,
    activeTextColor: Color = Color.White,
    inactiveTextColor: Color = AquaBlue,
    initialSelectedItemIndex: Int = 0
) {
    var selectedItemIndex by remember {       
        mutableStateOf(initialSelectedItemIndex)
    }
    Row(
        horizontalArrangement = Arrangement.SpaceAround,
        verticalAlignment = Alignment.CenterVertically,
        modifier = modifier   
            .fillMaxWidth()
            .background(DeepBlue)
            .padding(15.dp)
    ) {
          // it is basically what we should have
          // for creating an element of BottomMenuItem
        items.forEachIndexed { index, item ->
            BottomMenuItem(
                item = item,
                isSelected = index == selectedItemIndex,
                activeHighlightColor = activeHighlightColor,
                activeTextColor = activeTextColor,
                inactiveTextColor = inactiveTextColor
            ) {
                selectedItemIndex = index
            }
        }
    }
}
// it's basically how menu item should look like
@Composable
fun BottomMenuItem(
    item: BottomMenuContent,
    isSelected: Boolean = false,
    activeHighlightColor: Color = ButtonGreen,
    activeTextColor: Color = Color.White,
    inactiveTextColor: Color = AquaBlue,
    onItemClick: () -> Unit
) {
    Column(
        horizontalAlignment = Alignment.CenterHorizontally,
        verticalArrangement = Arrangement.Center,
        modifier = Modifier.clickable {
            onItemClick()
        }
    ) {
          // here are some peremetens
          // for how elements will align
        Box(
            contentAlignment = Alignment.Center,
            modifier = Modifier
                .clip(RoundedCornerShape(10.dp))
                .background(if (isSelected) activeHighlightColor else Color.Transparent)
                .padding(10.dp)
        ) {
            Icon(
                painter = painterResource(id = item.iconId),
                contentDescription = item.title,
                tint = if (isSelected) activeTextColor else inactiveTextColor,
                modifier = Modifier.size(20.dp)
            )
        }
        Text(
            text = item.title,
              // it's basic condition
            color = if(isSelected) activeTextColor else inactiveTextColor
        )
    }
}
```