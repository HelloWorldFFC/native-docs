
## 微信分享 

[微信appkey申请方法](http://ask.dcloud.net.cn/article/208)

### 需要拷贝添加的文件

| 路径 | 文件 | 
| :-------: | :-------: |
| uniMPSDK\Features\libs | share-weixin-release.aar，wechat-sdk-android-with-mta-5.4.3.jar |

将表格中的文件拷贝至主Module中的libs下。

![](https://img.cdn.aliyun.dcloud.net.cn/nativedocs/nativeplugin/android_plugin_img_3_1.png)

### Androidmainfest.xml文件需要修改的项

**需要在application节点前添加权限**

~~~
<uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS"/>
~~~

**<application>节点下配置如下代码**

~~~
<!-- 微信分享 配置begin -->
<meta-data android:name="WX_APPID" android:value="%微信开放平台申请应用的AppID%">
</meta-data>
<meta-data android:name="WX_SECRET" android:value="%微信开放平台申请应用的Secret%">
</meta-data>
<activity
    android:name="【包名】.wxapi.WXEntryActivity"
    android:label="@string/app_name"
    android:exported="true"
    android:launchMode="singleTop">
		<intent-filter>
            <action android:name="android.intent.action.VIEW"/>
            <category android:name="android.intent.category.DEFAULT"/>
            <data android:scheme="%微信开放平台申请应用的AppID%""/>
        </intent-filter>
</activity>
<!-- 微信分享 配置 end -->
~~~

### 修改dcloud_properties.xml配置

dcloud_properties.xml文件在assets/data目录下 

![](https://img.cdn.aliyun.dcloud.net.cn/nativedocs/nativeplugin/android_plugin_img_3_2.png)

在dcloud_properties.xml添加以下信息

#### features节点下设置

~~~
<feature name="Share" value="io.dcloud.share.ShareFeatureImpl"><module name="Weixin" value="io.dcloud.share.mm.WeiXinApiManager"/></feature>
~~~
**提示：**

1) androidmanifest.xml文件中声明的包名必须与申请微信appkey使用的包名一致，否则分享插件会调用失败

2) 微信分享测试需要使用在微信开放平台申请应用时使用的应用签名文件进行签名打包，否则无法获取好友列表。


## QQ分享

### 需要拷贝添加的文件

| 路径 | 文件 | 
| :-------: | :-------: |
| uniMPSDK\Features\libs | share-qq-release.aar，qq_mta-sdk-1.6.2.jar，qq_sdk_v3.5.2.152.jar |

将表格中的文件拷贝至主Module中的libs下。

![](https://img.cdn.aliyun.dcloud.net.cn/nativedocs/nativeplugin/android_plugin_img_3_1.png)

### Androidmainfest.xml文件需要修改的项

**需要在application节点前添加权限**

~~~
<uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS"/>
~~~

**<application>节点下配置如下代码**

~~~
<!-- Share QQ start -->
<meta-data android:value="%appid%" android:name="QQ_APPID"/> 
<activity android:name="com.tencent.tauth.AuthActivity" android:launchMode="singleTask" android:noHistory="true"> 
    <intent-filter>
        <action android:name="android.intent.action.VIEW"/> 
        <category android:name="android.intent.category.DEFAULT"/> 
        <category android:name="android.intent.category.BROWSABLE"/>
        <data android:scheme="%appid%"/> 
    </intent-filter> 
</activity> 
<activity android:name="com.tencent.connect.common.AssistActivity" android:theme="@android:style/Theme.Translucent.NoTitleBar" android:screenOrientation="portrait"/>
<!-- Share QQ end -->
~~~

### 修改dcloud_properties.xml配置

dcloud_properties.xml文件在assets/data目录下 

![](https://img.cdn.aliyun.dcloud.net.cn/nativedocs/nativeplugin/android_plugin_img_3_2.png)

在dcloud_properties.xml添加以下信息

#### features节点下设置

~~~
<feature name="Share" value="io.dcloud.share.ShareFeatureImpl"><module name="QQ" value="io.dcloud.share.qq.QQApiManager"/></feature>
~~~

## 新浪微博

[新浪微博appkey申请步骤](http://ask.dcloud.net.cn/article/209)

### 需要拷贝添加的文件

| 路径 | 文件 | 
| :-------: | :-------: |
| uniMPSDK\Features\libs | sina-libs-release.aar，share-sina-release.aar|

将表格中的文件拷贝至主Module中的libs下。

![](https://img.cdn.aliyun.dcloud.net.cn/nativedocs/nativeplugin/android_plugin_img_3_1.png)

### Androidmainfest.xml文件需要修改的项

**需要在application节点前添加权限**

~~~
<uses-permission android:name="android.permission.CHANGE_WIFI_STATE"/>   
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>     
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>   
~~~

**application节点下配置如下代码**

~~~
<!-- Share - 新浪微博分享 -->
<!-- 官方网站：http://open.weibo.com/ -->
<meta-data android:name="SINA_APPKEY" android:value="_%新浪微博开放平台申请应用的Appkey，注意前面要添加下划线%" />
<meta-data android:name="SINA_SECRET" android:value="%新浪微博开放平台申请应用的Secret%" />
<meta-data android:name="SINA_REDIRECT_URI" android:value="%新浪微博开放平台申请应用配置的回调地址%" />
<activity android:name="com.sina.weibo.sdk.web.WeiboSdkWebActivity"
    android:configChanges="keyboardHidden|orientation"
    android:exported="false"
    android:windowSoftInputMode="adjustResize">
</activity>

<activity android:name="com.sina.weibo.sdk.share.WbShareTransActivity"
    android:launchMode="singleTask"
    android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen">
    <intent-filter>
        <action android:name="com.sina.weibo.sdk.action.ACTION_SDK_REQ_ACTIVITY" />
		<category android:name="android.intent.category.DEFAULT" />
    </intent-filter>
</activity>
~~~

### 修改dcloud_properties.xml配置

dcloud_properties.xml文件在assets/data目录下 

![](https://img.cdn.aliyun.dcloud.net.cn/nativedocs/nativeplugin/android_plugin_img_3_2.png)

在dcloud_properties.xml添加以下信息

#### features节点下设置

~~~
<feature name="Share" value="io.dcloud.share.ShareFeatureImpl"><module name="Sina" value="io.dcloud.share.sina.SinaWeiboApiManager"/></feature>
~~~

**提示：**androidmanifest.xml文件中声明的包名必须与申请新浪微博appkey使用的包名一致，否则分享插件会调用失败
