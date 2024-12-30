问题：假如在MainActivity中有个 name = "朱辉涛"，我想把它修改为 "Frank"

1，定义native方法

```
external fun changeName(instance:MainActivity):String
```

2,jni实现

```
extern "C"
JNIEXPORT jstring JNICALL
Java_com_atoto_usbdemo_NativeDef_changeName(JNIEnv *env, jobject thiz, jobject instance) {
    jclass mainClass = findKtClass(env, "com/atoto/usbdemo/MainActivity");
    jfieldID nameFiledId = env->GetFieldID(mainClass, "name", "Ljava/lang/String;");
    if (nameFiledId == nullptr) return nullptr;
    jstring newName = env->NewStringUTF("Frank");
    env->SetObjectField(instance, nameFiledId, newName);
    return newName;
}

```

运行结果
```
2024-12-29 11:06:20.244 14291-14291 MainActivity            com.atoto.usbdemo                    D  name = 朱辉涛
2024-12-29 11:06:20.244 14291-14291 MainActivity            com.atoto.usbdemo                    D  修改后的name = Frank
```