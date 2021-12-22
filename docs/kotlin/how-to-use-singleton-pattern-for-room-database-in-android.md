# 如何在安卓系统中对房间数据库使用单体模式？

> 原文:[https://www . geeksforgeeks . org/如何使用-单例模式-适用于 android 中的房间-数据库/](https://www.geeksforgeeks.org/how-to-use-singleton-pattern-for-room-database-in-android/)

**先决条件:**

*   [Room database in Android](https://www.geeksforgeeks.org/overview-of-room-in-android-architecture-components/)
*   [singleton pattern](https://www.geeksforgeeks.org/singleton-design-pattern/)

Room 是安卓中的 Jetpack 架构组件之一。这在 SQLite 数据库上提供了一个抽象层，用于在本地保存持久数据并对其执行操作。这是谷歌推荐的，而不是 SQLite 数据库，尽管 SQLite APIs 更强大，但它们相当低级，使用起来需要大量的时间和精力。但是，Room 使创建数据库并对其执行操作变得简单明了。单一模式是最简单的设计模式之一。有时我们只需要有一个类的实例，例如一个由多个对象共享的数据库连接，因为为每个对象创建一个单独的数据库连接可能成本很高。同样，应用程序中可以有一个配置管理器或错误管理器来处理所有问题，而不是创建多个管理器。简而言之，当我们需要实例化一个类的单个实例时，我们使用 Singleton 模式。我们以只能创建一个实例的方式定义一个类。

### **在安卓开发中，我们可以在哪里使用****单例模式？**

我们可以在 Android 中使用 Singleton Pattern 的几个例子是:

*   When we use Room database, we only need one instance of the roomdatabase class in the whole application. Too many instances of database will lead to memory leakage. Therefore, we use singleton pattern in the database.
*   In [MVVM architecture](https://www.geeksforgeeks.org/mvvm-model-view-viewmodel-architecture-pattern-in-android/) , when we create a repository, we only need one instance, because there is no change in the repository class during the whole execution of the application.

还有其他情况，我们更喜欢使用 Singleton 模式。在本文中，我们将关注如何在 android 中使用 Singleton 模式。由于我们已经有了在数据库中使用单例模式的想法，现在我们将进一步进行实现。

### 履行

在这里，我们将使用 Singleton 模式实现 Room 数据库(假设数据库存储联系人)。

*   **First, let's define the data entity.**
*   This will be a data class. Let's name it **contact.kt**

参考以下代码。

## 科特林

```kt
import androidx.room.Entity
import androidx.room.PrimaryKey

@Entity(tableName = "contact")
data class Contact(
    @PrimaryKey(autoGenerate = true)
    val id: Int,
    val name: String,
    val phoneNum: String
)
```

(autoGenerate = true)用于每当添加新数据时自动递增到 id。

*   **Then we need to create knives.**
*   Knife is an interface, so there is no need to define methods in it. The room needs to pay attention to the implementation of these methods.
*   Dao is used to access data objects in the database.

参考以下代码。

## 【科特林】

```kt
import androidx.lifecycle.LiveData
import androidx.room.Dao
import androidx.room.Insert
import androidx.room.Query

@Dao
interface ContactDao {
    @Insert
    fun insert(contact: Contact)

    @Query("Select * From contact")
    fun getContact():List<Contact>
}
```

*   Now we will create the database class, which is the main access point for the application's persistent data.
*   It is an abstract class that inherits RoomDatabase. We have achieved singleton pattern here.

参考以下代码。

## 【科特林】

```kt
import android.content.Context
import androidx.room.Database
import androidx.room.Room
import androidx.room.RoomDatabase

@Database(entities = [Contact::class], version = 1)
abstract class ContactDatabase : RoomDatabase() {
    abstract fun contactDao(): ContactDao

    companion object {
        private var INSTANCE: ContactDatabase? = null
        fun getDatabase(context: Context): ContactDatabase {
            if (INSTANCE == null) {
                synchronized(this) {
                    INSTANCE =
                        Room.databaseBuilder(context,ContactDatabase::class.java, "contact_database")
                            .build()
                }
            }
            return INSTANCE!!
        }
    }
}
```

*   When we create an instance of the Database class, we use a companion object to directly access the getDatabase () method.
*   We use a synchronization block to prevent different threads from making multiple calls at the same time.

因此，每当您想要在 Room 数据库中使用 Singleton 模式时，这个伴随对象是很常见的。