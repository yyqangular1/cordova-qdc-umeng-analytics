# 友盟统计cordova插件

# 安装
cordova/ionic plugin add https://github.com/yyqangular1/cordova-qdc-umeng-analytics.git

# 卸载
cordova/ionic plugin rm https://github.com/yyqangular1/cordova-qdc-umeng-analytics.git

# 使用

Android
-------------------------------------
### 1.配置AppKey和Channel
打开插件目录下的plugin.xml文件
```
    <meta-data android:name="UMENG_CHANNEL" android:value="YOUR_CHANNEL"/>
    <meta-data android:name="UMENG_APPKEY" android:value="YOUR_APP_KEY"/>
```
    YOUR_CHANNEL：填写渠道名称，如360、wodajia、QQ等，可以自定义渠道，在统计后台可以看到渠道信息
    YOUR_APP_KEY：填写从友盟获取的APPKey

### 2.更改包名
打开插件目录\src\android\UmengAnalyticsPlugin.java 文件，找到import your.package.name.R，将其替换为：import 你实际项目包的名称.R。


### 3.配置代码
在app.js文件中添加插件所需的代码
```javascript
    .run(['$ionicPlatform', function ($ionicPlatform) {
            $ionicPlatform.ready(function () {
                if (window.cordova && window.cordova.plugins.Keyboard) {
                    cordova.plugins.Keyboard.hideKeyboardAccessoryBar(true);
                }
                if (window.StatusBar) {
                    // org.apache.cordova.statusbar required
                    StatusBar.styleDefault();
                }

                //初始化友盟统计配置
                window.plugins.umengAnalyticsPlugin.init();
                //调试模式
                window.plugins.umengAnalyticsPlugin.setDebugMode(true);

                //注意，这段代码是应用退出前保存统计数据，请在退出应用前调用
                //window.plugins.umengAnalyticsPlugin.onKillProcess();
            });
        }])
```
### 4.参考资料
[友盟统计分析Android文档 ](http://dev.umeng.com/analytics/android-doc/integration)


IOS
-------------------------------------
### 1.配置AppKey和Channel
打开插件目录下的ios\UmengAnalyticsPlugin.m文件
```Objective-C
 [MobClick startWithAppkey:@"YOU_APP_KEY" reportPolicy:BATCH   channelId:@"YOUR_CHANNEL"];
```
    YOUR_APP_KEY：填写从友盟获取的APPKey
    YOUR_CHANNEL：填写渠道名称，默认为"App Store"渠道，可以自定义渠道，在统计后台可以看到渠道信息

### 2.配置代码
在app.js文件中添加插件所需的代码
```javascript
    .run(['$ionicPlatform', function ($ionicPlatform) {
            $ionicPlatform.ready(function () {
                if (window.cordova && window.cordova.plugins.Keyboard) {
                    cordova.plugins.Keyboard.hideKeyboardAccessoryBar(true);
                }
                if (window.StatusBar) {
                    // org.apache.cordova.statusbar required
                    StatusBar.styleDefault();
                }

                //初始化友盟统计
                window.plugins.umengAnalyticsPlugin.init();
            });
        }])
```
### 3.参考资料
[友盟统计分析IOS文档 ](http://dev.umeng.com/analytics/ios-doc/integration)