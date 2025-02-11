### 查看系统sdk版本
adb shell getprop ro.build.version.sdk

### 查看arm架构
adb shell getprop ro.build.version.sdk

### 查看cpu详细信息
adb shell cat /proc/cpuinfo

### 查看正在运行的应用
adb shell ps | grep atoto
remark：atoto 是标签，会列出所有的atoto包名相关的应用
