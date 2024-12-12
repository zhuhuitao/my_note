Error running pod install
Error launching application on iPhone 15 Pro Max.

解决：只要修改ios目录下podfile 第二行 去掉#号



  [!] CocoaPods could not find compatible versions for pod "sqflite":       In Podfile:         sqflite (from `.symlinks/plugins/sqflite/darwin`)
打开podfile，将platform版本进行修改
platform :ios, '12.0'
![alt text](企业微信截图_98782c93-8d9f-4c25-a013-b0d7ba53a5dc-1.png) Inspecting targets to integrate
      Using `ARCHS` setting to build architectures of target `Pods-Runner`: (``)
    [!] Unable to find a target named `RunnerTests` in project `Runner.xcodeproj`, did find `Runner`.


MissingPluginException(No implementation found for method login on channel app.meedu/flutter_facebook_auth)


解决Module '… ’ not found

1:删除podfile 和podfile.lock文件
2:cd ios
3:flutter clean
4:flutter pub get
5:pod install

执行pod install如果报错 ，[图片]
找到podfile文件，将platform :ios, '12.0’前面的#号 去掉，这时根据提示修改版本号