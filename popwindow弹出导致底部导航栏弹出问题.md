### 解决全屏状态下，popwindow弹出导致的底部导航栏弹出，挤压布局问题

1，将activity设置为全屏,需要在setContentView之前
```kotlin
 requestWindowFeature(Window.FEATURE_NO_TITLE)
        window.setFlags(
            WindowManager.LayoutParams.FLAG_FULLSCREEN,
            WindowManager.LayoutParams.FLAG_FULLSCREEN
        )
        val docView = window?.decorView
        val uiOptions = (View.SYSTEM_UI_FLAG_HIDE_NAVIGATION
                or View.SYSTEM_UI_FLAG_FULLSCREEN);
        docView?.systemUiVisibility = uiOptions
```

2，show popwindow的时候，focusable需要为false，如果设置为true聚焦导致的底部导航栏弹出

```java
  public PopupWindow(View contentView, int width, int height, boolean focusable) {
        if (contentView != null) {
            mContext = contentView.getContext();
            mWindowManager = (WindowManager) mContext.getSystemService(Context.WINDOW_SERVICE);
        }

        setContentView(contentView);
        setWidth(width);
        setHeight(height);
        setFocusable(focusable);
    }
```
new 出pop 对象的时候，可以不指定focusable,默认就是false

3，当focusable为fasle的时候，点击pop外部是无法dismiss的，首先想到的是通过下面代码处理
```kotlin
popWindow.setTouchInterceptor(OnTouchListener { v, event ->
        val x = event!!.rawX.toInt()
        val y = event.rawY.toInt()
        if (x < 0 || x >= v!!.width || y < 0 || y >= v.height) {
            popWindow.dismiss()
            v.performClick()
           return@OnTouchListener true
        }
        false
    })
```
这样实际只能捕获pop内部的，外面是无法捕获的，通过设置isOutsideTouchable = true解决