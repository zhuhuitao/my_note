
引入头文件

```
#include <android/log.h>
```

```
#define LOGD(...) __android_log_print(ANDROID_LOG_DEBUG, "Native", __VA_ARGS__)
#define LOGI(...) __android_log_print(ANDROID_LOG_INFO, "Native", __VA_ARGS__)
#define LOGE(...) __android_log_print(ANDROID_LOG_ERROR, "Native", __VA_ARGS__) 
```



使用

```
 LOGD("jni接收到的值result = %d\n", result);
```