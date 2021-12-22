# 用 Kotlin 设计安卓模式

> 原文:[https://www . geesforgeks . org/design-patterns-in-Android-with-kot Lin/](https://www.geeksforgeeks.org/design-patterns-in-android-with-kotlin/)

设计模式基本上是我们在编程中反复遇到的一个问题的解决方案或蓝图，所以它们只是我们作为程序员可以遇到的典型问题类型，而这些设计模式只是解决那些问题的好方法，安卓中有很多设计模式。基本上，它们分为以下三类:

1.  **创造模式**:你如何创造物体。
2.  **结构模式**:你如何组成物体。
3.  **行为模式**:你如何协调对象交互。

现在我们将讨论您应该知道的最重要的设计模式。

### 1.创造模式

这些是处理对象创建机制的设计模式，试图以适合情况的方式创建对象。对象创建的基本形式可能会导致设计问题或增加设计的复杂性。创造性的设计模式通过某种方式控制对象的创建来解决这个问题。这些设计模式都属于这一类。

*   一个
*   建设者
*   依赖注入
*   工厂

让我们快速讨论一下它们:

[](https://www.geeksforgeeks.org/singleton-design-pattern/)****:****

*   **单例模式确保一个特定类中只有一个对象被创建。对 singleton 类对象的所有进一步引用都指向同一个底层实例。应用程序很少，不要过度使用这种模式。**
*   **在 Kotlin 中很容易完成，但在 java 中却不容易。因为在 java 中没有 singleton 的本机实现。**

## **我的锅**

```
object eSingleton {
  fun doing() {
    // ...
  }
}
```

> ****要访问单例对象的成员，可以这样调用:****
> 
> **eSingleton.doing()**

*   **通过使用 ***对象*** ，你会知道你在你的应用程序中使用的是同一个类的实例。**

**[**建造者**](https://www.geeksforgeeks.org/builder-design-pattern/) **:****

*   **构建器模式用于创建具有组成部分的复杂对象，这些组成部分必须以相同的顺序或使用特定的算法创建。外部类控制构造算法。[点击此处](https://www.geeksforgeeks.org/builder-design-pattern/)**

**[**工厂**](https://www.geeksforgeeks.org/abstract-factory-pattern/) **:****

*   **顾名思义，工厂负责所有的对象创造逻辑。在这种模式下，工厂类控制实例化哪个对象。工厂模式在处理许多常见对象时非常有用。您可以在不想指定具体类的地方使用它。[点击此处](https://www.geeksforgeeks.org/abstract-factory-pattern/)**

****依赖注入:****

*   **依赖注入就像搬进带家具的公寓。你需要的一切都已经在那里了。你不必等待家具交付或遵循宜家的指示页面来组装一个 Borgsjö书架。**
*   **用软件术语来说，依赖注入让你提供任何需要的对象来实例化一个新的对象。这个新对象不需要自己构造或定制对象。**
*   **在安卓系统中，您可能会发现需要从应用程序中的不同点访问相同的复杂对象，例如网络客户端、图像加载器或用于本地存储的共享引用。您可以将这些对象注入到您的活动和片段中，并立即访问它们。**
*   **目前，依赖注入有三个主要库:匕首' 2 '，匕首柄，和 Koin。**

### **2.结构模式**

**这些设计模式都是关于类和对象的组合。结构类创建模式使用继承来组成接口。结构对象模式定义了组合对象以获得新功能的方法。**

*   **外表**
*   **适配器**
*   **装饰者**
*   **复合材料**
*   **保护代理**

**[**门面**](https://www.geeksforgeeks.org/facade-design-pattern-introduction/) **:****

*   **门面模式用于定义一个更复杂子系统的简化接口。**

**[**适配器**](https://www.geeksforgeeks.org/adapter-pattern/) **:****

*   **适配器模式通过用支持客户端所需接口的类包装“adaptee”来提供两个不兼容类型之间的链接。**

**[](https://www.geeksforgeeks.org/decorator-pattern-set-3-coding-the-design/)****:******

*   ****装饰器模式用于在运行时通过将对象包装在装饰器类的对象中来扩展或改变对象的功能。这为使用继承来修改行为提供了一个灵活的替代方案。****

****[**复合**](https://www.geeksforgeeks.org/composite-design-pattern/)T4:****

*   ****复合模式用于组成零个或多个相似的对象，以便它们可以作为一个对象进行操作。****

****[**【保护代理】**](https://www.geeksforgeeks.org/proxy-design-pattern/) **:******

*   ****代理模式用于提供引用基础对象的代理或占位符对象。保护代理正在限制访问。****

### ****3.行为模式****

*   ****命令****
*   ****观察者****
*   ****战略****
*   ****状态****
*   ****访问者****
*   ****调解人****
*   ****纪念品****
*   ****责任链****

****[**命令**](https://www.geeksforgeeks.org/command-pattern/) **:******

*   ****命令模式用于在命令对象中表达请求，包括要进行的调用及其所有必需的参数。然后，该命令可以立即执行或保留以备后用。****

****[**观察者**](https://www.geeksforgeeks.org/observer-pattern-set-1-introduction/) **:******

*   ****观察者模式用于允许对象发布对其状态的更改。其他对象订阅以获得任何更改的即时通知。****

****[**战略**](https://www.geeksforgeeks.org/strategy-pattern-set-1/) **:******

*   ****策略模式用于创建一个可互换的算法族，在运行时可以从中选择所需的进程。****

****[**状态**](https://www.geeksforgeeks.org/state-design-pattern/) **:******

*   ****状态模式用于随着对象内部状态的变化而改变对象的行为。该模式允许对象的类在运行时明显改变。****

****[**访客**](https://www.geeksforgeeks.org/visitor-design-pattern/) **:******

*   ****访问者模式用于将一组相对复杂的结构化数据类与可能对其持有的数据执行的功能分开。****

****[**调解员:**](https://www.geeksforgeeks.org/mediator-design-pattern/)****

*   ****中介器设计模式用于在系统中的不同对象之间提供集中的通信媒介。这种模式在多个对象相互交互的企业应用程序中非常有用。****

****[](https://www.geeksforgeeks.org/memento-design-pattern/)****:********

*   ****memento 模式是一种软件设计模式，它提供了将对象恢复到其先前状态(通过回滚撤消)的能力。****

****[**责任链**](https://www.geeksforgeeks.org/chain-responsibility-design-pattern/) **:******

*   ****责任链模式用于处理不同的请求，每一个请求都可以由不同的处理程序处理。****