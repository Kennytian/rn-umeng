# React Native Umeng

A Umeng lib for React Native

# iOS Install

```bash
$ npm install --save rn-umeng2
$ react-native link rn-umeng2
```

# Android Install (Manual)

```bash
$ npm install --save rn-umeng2
```

#### Add Gradle Module Manually

Module Source:

```bash
$PROJECT_DIR/node_modules/rn-umeng2/android
```

![image](https://raw.githubusercontent.com/Kennytian/rn-umeng/master/screenshots/screenshot0.png)

![image](https://raw.githubusercontent.com/Kennytian/rn-umeng/master/screenshots/screenshot1.png)

#### Add UmengPackage

```java
ReactInstanceManager.builder() ...
.addPackage(new UmengPackage())
```

#### onResume and onPause
```java
@Override
protected void onResume() {
	super.onResume();
	MobclickAgent.onResume(this);
}

@Override
protected void onPause() {
	super.onPause();
	MobclickAgent.onPause(this);
}
```

# Usage

The api mapping below

React Native Side        | iOS Side           | Android Side   
--------------------------|---------------------|-----------------------
startWithAppkey(string)   | startWithAppkey(NSString)   | AnalyticsConfig.setAppkey(String appkey)
startWithAppkeyAndChannel(string,string)   | N/A   | UMAnalyticsConfig(Context context, String appkey, String channelId)  
setAppVersion(string)     | setAppVersion(string)       | Not need to set it
setDebugMode(bool)        | setLogEnabled(BOOL)         | MobclickAgent.setDebugMode( true )  
enableEncrypt(boole)      | setEncryptEnabled(BOOL)          | AnalyticsConfig.enableEncrypt(boolean enable)   
setCrashReportEnabled(boole)      | setCrashReportEnabled(BOOL)           | MobclickAgent.setCatchUncaughtExceptions(false)
onEvent(string)      |event:(NSString *)eventId           | MobclickAgent.onEvent(Context context, String eventId)
onEvent(string,{key:"value"})      | onEvent:(NSString *)eventId attributes:(NSDictionary *)attributes           | MobclickAgent.onEvent(Context context, String eventId, HashMap map)
onEvent(string,{key:"value"},0)    | onEvent:(NSString *)eventId attributes:(NSDictionary *)attributes counter:(NSString *)counter           | MobclickAgent.onEventValue(Context context, String id, Map<String,String> m, int du)
onProfileSignIn('ID')      | profileSignInWithPUID:(NSString *)puid           | onProfileSignIn(String ID)
onProfileSignIn('ID','Provider')      | profileSignInWithPUID:(NSString *)puid provider:(NSString *)provider           | onProfileSignIn(String Provider, String ID)
onProfileSignOff()      | profileSignOff           | onProfileSignOff()
onPageStart(string)      | beginLogPageView:(NSString *)pageName           | MobclickAgent.onPageStart(String pageName)
onPageEnd(string)      | endLogPageView:(NSString *)pageName           | MobclickAgent.onPageEnd(String pageName)
onLogPageViewInseconds('pageName',10)      | logPageView:pageName seconds:seconds          | N/A
openActivityDurationTrack(boole)      |  N/A           | MobclickAgent.openActivityDurationTrack(boolean value)
onResume()      | N/A           | MobclickAgent.onResume()
onPause()      | N/A            | MobclickAgent.onPause()
getDeviceInfo((infoStr)=>{})      | getDeviceInfo           | getDeviceInfo

In your project code

```javascript
import MobclickAgent from 'rn-umeng2';
MobclickAgent.startWithAppkey('your appkey');
MobclickAgent.setDebugMode(true);
MobclickAgent.onEvent("testEvent");
```

# Changelog

### - 1.0.10
 - 升级 Android 端编译版本
   - compileSdkVersion 26
   - buildToolsVersion "26.0.3"
 - 新增 .editorconfig 文件
 - 新增 .gitignore 项
 - 删除 Android 端无用的 manifest 内容
 - 删除 Android 端下 res/values 目录
 - 删除 iOS 端 project.xcworksapce
 - 删除 iOS 端 xcuserdata
 
### - 1.0.9
 - 同步 @zbtang 分支代码
 - 感谢 @zbtang

### - 1.0.8
 - 修改 npm 包名 

### - 1.0.7
 - Android / iOS 升级至 umeng-analytics-v6.1.0
 - 感谢 @ljspace

### - 1.0.6
 - support RN 0.40

### - 1.0.5

 - fix error in LazyReactPackage

### - 1.0.4

 - add Android channel set

### - 1.0.3

 - add Android lib (but Manually,rnpm link not works,fix later)
 - update readme.md


### - 1.0.2
 - Project initialization

# License
MIT


