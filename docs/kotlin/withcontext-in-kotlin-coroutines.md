# 科特林 coroutines 中的 withcontext

> 原文:[https://www . geesforgeks . org/with context-in-kotlin-coroutines/](https://www.geeksforgeeks.org/withcontext-in-kotlin-coroutines/)

**先决条件:**

*   [The Corolla of Kettering on Android](https://www.geeksforgeeks.org/kotlin-coroutines-on-android/)
*   [in the cortland corolla](https://www.geeksforgeeks.org/launch-vs-async-in-kotlin-coroutines/)

中启动 vs 异步

众所周知[异步和启动](https://www.geeksforgeeks.org/launch-vs-async-in-kotlin-coroutines/)是启动[协同](https://www.geeksforgeeks.org/kotlin-coroutines-on-android/)的两种方式。由于已知 async 是用来取回结果的，所以&应该只在我们需要并行执行的时候使用，而 launch 是在我们不想取回结果的时候使用，用于数据更新等操作。正如我们所知，异步是到目前为止启动协同并返回结果的唯一方法，但是当我们不想进行并行网络调用时，异步的问题就出现了。众所周知，当使用异步时，需要使用****await()**函数，这将导致阻塞主线程，但这里出现了 **withContext** 的概念，它消除了阻塞主线程的问题。**

**withContext 只不过是写异步的另一种方式，在这种方式中，不必写**wait()**。当使用 withContext 时，它以串行方式而不是并行方式运行任务。因此，人们应该记住，当我们在后台有一个单一的任务，并且想要获得该任务的结果时，我们应该使用 withContext。让我们举一个例子来说明 withContext 的工作原理:**

 **## 【科特林】

```
// two kotlin suspend functions
// Suppose we have two tasks like below

private suspend fun doTaskOne(): String
{
  delay(2000)
  return "One"
}

private suspend fun doTaskTwo(): String
{
  delay(2000)
  return "Two"
}
```**