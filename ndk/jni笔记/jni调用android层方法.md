问题：
假如我在MainActivity定义了一个方法,在jni中能调用这个方法并拿到两数相加的和，log打印到控制台

```
    fun addNumber(a: Int, b: Int): Int {
        Log.d(TAG, "addNumber: 调用了kt方法")
        return  a + b
    }

```

1，定义nativi方法

```
  external fun callKtMethod(instance: MainActivity,a:Int,b:Int)
```

2，实现jni方法

```
extern "C"
JNIEXPORT void JNICALL
Java_com_atoto_usbdemo_NativeDef_callKtMethod(JNIEnv *env, jobject thiz, jobject instance, jint a,
                                              jint b) {
    jclass jclass1 = findKtClass(env, "com/atoto/usbdemo/MainActivity");
    jmethodID methodId = env->GetMethodID(jclass1, "addNumber", "(II)I");
    if (methodId == nullptr) return;
    jint result = env->CallIntMethod(instance, methodId, a, b);
    LOGD("jni接收到的值result = %d\n", result);
}
```

3，执行结果

```
2024-12-29 11:06:20.244 14291-14291 MainActivity            com.atoto.usbdemo                    D  addNumber: 调用了kt方法
2024-12-29 11:06:20.244 14291-14291 Native                  com.atoto.usbdemo                    D  jni接收到的值result = 14
```

