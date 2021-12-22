# 如何在安卓中编程获取连接信息？

> 原文:[https://www . geeksforgeeks . org/如何在 android 中以编程方式获取连接信息/](https://www.geeksforgeeks.org/how-to-obtain-the-connection-information-programmatically-in-android/)

有时，查找网络相关的详细信息变得很有挑战性，尤其是设备的 IP 地址，这可能是通过调制解调器软件授予唯一首选项所必需的。由于多个安卓设备(三星、米、熔岩)向用户显示的信息存在差异，我们实现了一个应用程序，通过该应用程序，可以轻松获取当前网络的详细信息，并在一个地方可用。我们在程序中从设备提取的关于连接的信息或实体是:

1.  [**[IP address]**](https://www.geeksforgeeks.org/introduction-of-classful-ip-addressing/) **:** This is a digital label that is assigned to every connecting device connected to a network that uses Internet protocol for communication.
2.  **Link speed:** is the maximum achievable speed (in bits per second) at which a device can communicate with other devices on the same network.
3.  **Network ID:** is the IP address part where the host is located. It identifies TCP/IP networks.
4.  [**[SSID]**](https://www.geeksforgeeks.org/service-set-identifier-ssid-in-computer-network/) **(Service Set Identifier):** is a unique identifier consisting of 32 characters, which is used for naming wireless networks.
5.  **Hide SSID:** Same as SSID. Hiding SSID is an effective method to protect network security. When people scan nearby wireless network connections, this will prevent networks from appearing in the list of available wireless networks.
6.  [t0 T0】 BSsid: SSID keeps the data packet in the correct WLAN. Even if there are overlapping wireless LANs, the data packets are secure. However, there are multiple access points in each WLAN. **Basic Service Set Identifier (BSSID)** identifies these access points and related clients and is included in all wireless data packets.

不幸的是，一些实体，如 [**媒体访问控制地址**](https://www.geeksforgeeks.org/introduction-of-mac-address-in-computer-network/) ，无法正确获取，这是有真正原因的。

*   The MAC address is unique in the world, which makes every device unique. This label cannot be reset by the user, and is still valid after factory reset. Therefore, it is best not to uniquely identify users.
*   From **Android 6.0 (API 23)** and **Android 9 (API 28)** , MAC addresses of local devices, such as Bluetooth and Wi-Fi, cannot be obtained through third-party APIs.
*   **wifi 信息。get acaddresses()**费金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金·阿金**蓝星转接器。getdefaultadapter()。getAddress()** 朱庇特·朱庇特 2:00:00:00:00:00:00，你知道吗？
*   In addition, between Android 6 and Android 9, you must have the following permissions to access the MAC addresses of nearby external devices available through Bluetooth and Wi-Fi scanning:
*   所需方法/属性权限: **ACCESS_FINE_LOCATION** 或**访问 _ 粗略 _ 位置**

### **接近**

要获取安卓系统中的当前连接信息，我们将按照以下步骤操作。注意我们将使用**语言来实施这个项目。**

****第一步:创建新项目****

**要在安卓工作室创建新项目，请参考[如何在安卓工作室创建/启动新项目](https://www.geeksforgeeks.org/android-how-to-create-start-a-new-project-in-android-studio/)。注意选择**科特林**作为编程语言。**

****步骤 2:使用 AndroidManifest.xml 文件****

**转到[**AnDroidManifest . XML**](https://www.geeksforgeeks.org/application-manifest-file-android/)文件，添加这些使用权限: **ACCESS_WIFI_STATE** 、 **ACCESS-FINE-LOCATION** 、**ACCESS _ rough _ LOCATION**。**

> **<使用-权限安卓:name = " Android . permission . access _ WIFI _ STATE "/>
> 
> <使用-权限安卓:name = " Android . permission . access _ FINE _ LOCATION "/>
> 
> <使用-权限安卓:name = " Android . permission . access _ rough _ LOCATION "/>**

**以下是 **AndroidManifest.xml** 文件的完整版本。**

 **## XML

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="org.geeksforgeeks.connectioninfo">

      <!--Add these permissions-->
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```**