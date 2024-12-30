在 JNI（Java Native Interface）中，本地方法的定义是否需要加 static 修饰符是由 Java 端声明方式决定的，而不是本地代码本身的设计需求。这归因于 Java 静态方法与实例方法的区别。

Java 中的定义
1. 实例方法：在 Java 中定义的非静态方法。
2. 静态方法：在 Java 中定义的用 static 关键字修饰的方法。
JNI 和 Java 方法的对应关系
1. 实例方法：

1. 在 Java 中声明为实例方法的本地方法通常不使用 static 关键字。调用实例方法时，必须通过类的一个具体实例。
2. 在这种情况下，JNI 函数会接受一个 jobject 参数，指向调用该方法的具体 Java 对象（相当于 Java 中的 this）。
// Java实例方法的声明
public native void instanceMethod();
对应的 JNI 实现：

JNIEXPORT void JNICALL Java_PackageName_ClassName_instanceMethod(JNIEnv* env, jobject obj) {
    // 示例方法的实现
}
2. 静态方法：

1. 在 Java 中声明为静态方法的本地方法使用 static 关键字。调用静态方法时可以不需要具体的类实例，只需通过类名来进行调用。
2. 在这种情况下，JNI 函数的第二个参数是 jclass，而不是 jobject，用于提供调用该方法的类的引用。
// Java静态方法的声明
public static native void staticMethod();
对应的 JNI 实现：

JNIEXPORT void JNICALL Java_PackageName_ClassName_staticMethod(JNIEnv* env, jclass cls) {
    // 静态方法的实现
}
总结
1. 实例方法是在具体对象上调用的，因此 JNI 函数中需要一个 jobject 参数来进行操作。
2. 静态方法是与类相关联的，不需要具体实例，因此使用 jclass 参数指向这个类。Java 中的 static 修饰符只是用来指示这个方法属于类而不是实例。
最本质的区别在于 Java 层面的设计和调用方式，而不在于 JNI 本身的实现。在 Java 中编写本地方法时，是否使用 static 完全取决于方法语义是否需要与具体对象绑定。