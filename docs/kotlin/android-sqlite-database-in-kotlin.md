# 科特林安卓 SQLite 数据库

> 原文:[https://www . geesforgeks . org/Android-SQLite-database-in-kot Lin/](https://www.geeksforgeeks.org/android-sqlite-database-in-kotlin/)

安卓自带一个内置的数据库包实现，这就是 [SQLite](https://www.geeksforgeeks.org/introduction-to-sqlite/) ，一个开源的 SQL 数据库，在设备中以文本的形式存储数据。在本文中，我们将研究安卓 SQLite 在 Kotlin 中的实现。

SQLite 是一个独立、高可靠性、嵌入式、全功能、公共域的 SQL 数据库引擎。它是世界上使用最多的数据库引擎。它是一个进程内库，其代码是公开的。它可以免费用于任何目的，商业或私人。它基本上是一个嵌入式的 SQL 数据库引擎。普通的磁盘文件可以很容易地被 SQLite 读写，因为它没有像 SQL 那样的独立服务器。SQLite 数据库文件格式是跨平台的，因此任何人都可以轻松地在 32 位和 64 位系统之间复制数据库。由于所有这些特性，它作为应用程序文件格式是一种流行的选择。

### **这篇文章我们要构建什么？**

我们将构建一个简单的应用程序，使用 SQLite 存储数据，我们还将实现检索数据的方法。下面是一个示例视频，展示了我们将要做的事情。

<video class="wp-video-shortcode" id="video-670110-1" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210820193645/gfg.mp4?_=1">[https://media.geeksforgeeks.org/wp-content/uploads/20210820193645/gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210820193645/gfg.mp4)</video>

### 逐步实施

**第一步:创建新项目**

要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。

**第二步:授予访问 AndroidManifest.xml 文件中存储的权限**

导航到**应用程序> AndroidManifest.xml** 并添加下面的代码。

## 可扩展标记语言

```kt
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
```

**步骤 3:使用 activity_main.xml 文件**

导航至**应用程序> res >布局> activity_main.xml** 。将以下代码添加到您的文件中。下面是 **activity_main.xml** 的代码。

## 可扩展标记语言

```kt
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <!-- Edit text to enter name -->
    <EditText
        android:id="@+id/enterName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Name"
        android:textSize="22sp"
        android:layout_margin="20sp"/>

    <!-- Edit text to enter age -->
    <EditText
        android:id="@+id/enterAge"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="20sp"
        android:textSize="22sp"
        android:hint="Enter Age"/>

    <!-- Button to add Name -->
    <Button
        android:id="@+id/addName"
        android:layout_width="150sp"
        android:layout_gravity="center"
        android:background="@color/colorPrimary"
        android:text="Add Name"
        android:textColor="#ffffff"
        android:textSize="20sp"
        android:layout_height="wrap_content"
        android:layout_marginTop="20sp"/>

    <!-- Button to print Name -->
    <Button
        android:id="@+id/printName"
        android:layout_width="150sp"
        android:layout_gravity="center"
        android:background="@color/colorPrimary"
        android:text="Print Name"
        android:textColor="#ffffff"
        android:textSize="20sp"
        android:layout_height="wrap_content"
        android:layout_marginTop="20sp"/>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <!-- Text view to get all name -->
        <TextView
            android:id="@+id/Name"
            android:textAlignment="center"
            android:layout_weight="1"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_margin="20sp"
            android:text="Name\n\n"
            android:textSize="22sp"
            android:padding="10sp"
            android:textColor="#000000"/>

        <!-- Text view to get all ages -->
        <TextView
            android:layout_weight="1"
            android:id="@+id/Age"
            android:textAlignment="center"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_margin="20sp"
            android:text="Age\n\n"
            android:textSize="22sp"
            android:padding="10sp"
            android:textColor="#000000"/>

    </LinearLayout>

</LinearLayout>
```

**第 4 步:为 SQLite 操作创建一个新类**

导航到 **app > java >你的项目的包名>右键点击它>新建> Kotlin 类**并将其命名为 **DBHelper** 并添加下面的代码。为了使代码更容易理解，添加了注释。

## 我的锅

```kt
package com.release.gfg1

import android.content.ContentValues
import android.content.Context
import android.database.Cursor
import android.database.sqlite.SQLiteDatabase
import android.database.sqlite.SQLiteOpenHelper

class DBHelper(context: Context, factory: SQLiteDatabase.CursorFactory?) :
    SQLiteOpenHelper(context, DATABASE_NAME, factory, DATABASE_VERSION) {

    // below is the method for creating a database by a sqlite query
    override fun onCreate(db: SQLiteDatabase) {
        // below is a sqlite query, where column names
        // along with their data types is given
        val query = ("CREATE TABLE " + TABLE_NAME + " ("
                + ID_COL + " INTEGER PRIMARY KEY, " +
                NAME_COl + " TEXT," +
                AGE_COL + " TEXT" + ")")

        // we are calling sqlite
        // method for executing our query
        db.execSQL(query)
    }

    override fun onUpgrade(db: SQLiteDatabase, p1: Int, p2: Int) {
        // this method is to check if table already exists
        db.execSQL("DROP TABLE IF EXISTS " + TABLE_NAME)
        onCreate(db)
    }

    // This method is for adding data in our database
    fun addName(name : String, age : String ){

        // below we are creating
        // a content values variable
        val values = ContentValues()

        // we are inserting our values
        // in the form of key-value pair
        values.put(NAME_COl, name)
        values.put(AGE_COL, age)

        // here we are creating a
        // writable variable of
        // our database as we want to
        // insert value in our database
        val db = this.writableDatabase

        // all values are inserted into database
        db.insert(TABLE_NAME, null, values)

        // at last we are
        // closing our database
        db.close()
    }

    // below method is to get
    // all data from our database
    fun getName(): Cursor? {

        // here we are creating a readable
        // variable of our database
        // as we want to read value from it
        val db = this.readableDatabase

        // below code returns a cursor to
        // read data from the database
        return db.rawQuery("SELECT * FROM " + TABLE_NAME, null)

    }

    companion object{
        // here we have defined variables for our database

        // below is variable for database name
        private val DATABASE_NAME = "GEEKS_FOR_GEEKS"

        // below is the variable for database version
        private val DATABASE_VERSION = 1

        // below is the variable for table name
        val TABLE_NAME = "gfg_table"

        // below is the variable for id column
        val ID_COL = "id"

        // below is the variable for name column
        val NAME_COl = "name"

        // below is the variable for age column
        val AGE_COL = "age"
    }
}
```

**第五步:使用 MainActivity.kt 文件**

转到 **MainActivity.kt** 文件，参考以下代码。下面是 **MainActivity.kt** 文件的代码。代码中添加了注释，以更详细地理解代码。

## 我的锅

```kt
package com.release.gfg1

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Toast
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // below code is to add on click
        // listener to our add name button
        addName.setOnClickListener{

            // below we have created
            // a new DBHelper class,
            // and passed context to it
            val db = DBHelper(this, null)

            // creating variables for values
            // in name and age edit texts
            val name = enterName.text.toString()
            val age = enterAge.text.toString()

            // calling method to add
            // name to our database
            db.addName(name, age)

            // Toast to message on the screen
            Toast.makeText(this, name + " added to database", Toast.LENGTH_LONG).show()

            // at last, clearing edit texts
            enterName.text.clear()
            enterAge.text.clear()
        }

        // below code is to add on  click
        // listener to our print name button
        printName.setOnClickListener{

            // creating a DBHelper class
            // and passing context to it
            val db = DBHelper(this, null)

            // below is the variable for cursor
            // we have called method to get
            // all names from our database
            // and add to name text view
            val cursor = db.getName()

            // moving the cursor to first position and
            // appending value in the text view
            cursor!!.moveToFirst()
            Name.append(cursor.getString(cursor.getColumnIndex(DBHelper.NAME_COl)) + "\n")
            Age.append(cursor.getString(cursor.getColumnIndex(DBHelper.AGE_COL)) + "\n")

            // moving our cursor to next
            // position and appending values
            while(cursor.moveToNext()){
                Name.append(cursor.getString(cursor.getColumnIndex(DBHelper.NAME_COl)) + "\n")
                Age.append(cursor.getString(cursor.getColumnIndex(DBHelper.AGE_COL)) + "\n")
            }

            // at last we close our cursor
            cursor.close()
        }
    }
}
```

现在运行您的应用程序并查看输出。

**输出:**

<video class="wp-video-shortcode" id="video-670110-2" width="640" height="360" preload="metadata" controls=""><source type="video/mp4" src="https://media.geeksforgeeks.org/wp-content/uploads/20210820193645/gfg.mp4?_=2">[https://media.geeksforgeeks.org/wp-content/uploads/20210820193645/gfg.mp4](https://media.geeksforgeeks.org/wp-content/uploads/20210820193645/gfg.mp4)</video>