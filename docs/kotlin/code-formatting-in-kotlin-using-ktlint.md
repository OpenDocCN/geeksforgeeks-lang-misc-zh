# 使用 ktlint 在 Kotlin 中格式化代码

> 原文:[https://www . geesforgeks . org/code-formatting-in-kot Lin-using-ktlint/](https://www.geeksforgeeks.org/code-formatting-in-kotlin-using-ktlint/)

众所周知，谷歌推荐的 kotlin 语言特别适合安卓应用程序开发，当然，它让安卓应用程序开发人员的生活变得更加轻松。但是，如果你是这个领域的初学者，那么你可能不知道你需要以期望的格式编写代码。而且这对开发人员肯定是有帮助的，但是如果你不熟悉如何使用 Kotlin 编写干净的代码，那么不要担心你不需要学习一些东西来实现这一点，相反，你只需要使用用于相同目的的 **ktlint** 。

> ***ktlint***:ktlint 是一款内置格式的防飞车党 Kotlin 短绒。简而言之，它检查我们的代码样式，还帮助我们形成代码，并使其更好地理解。

### 使用它的好处

*   Ktlitn 可以节省你的时间
*   它可以节省您的精力(因为您不必手动检查代码样式)
*   它可以简化您的流程

### 我们可以用 ktlint 做什么？

在此之前，让我们谈谈一些重要的事情，比如 ktlint 分解成两件事。

1.  **Lin Ting tool:** Lining tool is based on kotlin standard style guide, which will verify and ensure that your code conforms to the style guide.
2.  **Formatter:** If ktlint detects problems in your code, you can run the formatter and have ktlint try to fix these problems for you automatically.

### 我们如何实施？

*   将 ktlint 添加到您的项目中，更具体地说，我们将把 ktlint 与 ktlint Gradle 插件集成在一起，这是一个独立的第三方插件，位于基本的 ktlint 工具之上，它通过提供现成的 Gradle 任务来运行 ktlint 命令，从而使使用 ktlint 变得非常容易。
*   有几个选项，但最简单的方法是使用 ktlint-Gradle 插件，该插件为 ktlint 的工具提供现成的 Gradle 任务

### 将 ktlint 添加到您的安卓项目中

*   要添加 ktlint-gradle 插件，只需将 ktlint-gradle 插件添加到您的根级构建. gradle 文件中
*   对于将插件应用于子项目，只需将 ktlint-gradle 插件应用于您想要检查的任何 gradle 模块
*   将添加的梯度任务验证为检查是否已为您的各种构建目标添加了 ktlintCheck 和 ktlintFormat 任务

### **添加 ktlint-gradle 插件**

如果使用支持插件 DSL 的 Gradle 版本，可以使用以下代码将 ktlint-gradle 添加到项目中:

## 我的锅

```
// root-level build.gradle
plugins {
    id "org.jlleitschuh.gradle.ktlint" version "7.1.0"
}

// root-level build.gradle
buildscript {
  repositories {
    maven {
      url "https://plugins.gradle.org/m2/"
    }
  }
  dependencies {
    classpath "org.jlleitschuh.gradle:ktlint-gradle:7.1.0"
  }
}
```

### 将 ktlint-Gradle 插件应用于所有子项目

您将希望将 ktlint-gradle 插件应用到项目中的各个模块。您可以使用根级 build.gradle 文件中的 allProjects{}块来实现这一点。

## 科特林

```
// root-level build.gradle
allprojects {
    ...
    apply plugin: "org.jlleitschuh.gradle.ktlint"
}
```

### 测试添加的梯度任务

最后，您将希望测试 ktlint Gradle 任务现在是否可用。你可以通过这些方式

*   Run. /gradlew tasks from the command line and look for any ktlint tasks.
*   Try to run. /gradlewktlintfrom the command line
*   Use IntelliJ or Gradle tool window in Android Studio to see if tasks are listed.

要实际检查代码的格式，请从命令行运行以下命令:

> **。/gradlew ktlintCheck**
> 
> 这将运行您的项目，并报告使用默认 ktlint-gradle 插件配置发现的任何错误。

要自动修复 ktlintCheck 报告的任何错误，您可以从命令行运行以下命令:

> **。/grad Lew ktlintform**
> 
> 这将尝试自动修复任何错误，并将报告任何无法自动修复的问题。

当所有内容都正确格式化后，当您运行 ktlintCheck 时，应该会看到类似于下图的内容。ktlint 是一个开源项目，由 Pinterest 维护，你可以找到更多信息。 [***点击此处。***](https://ktlint.github.io/)