[Using AndroidX](https://developer.android.google.cn/jetpack/androidx)  
在 `gradle.properties` 中添加下面的属性，AS 将自动添加X 的lib
```
android.useAndroidX=true
android.enableJetifier=true
```
> android.useAndroidX: When set to true, the Android plugin uses the appropriate AndroidX library instead of a Support Library. The flag is false by default if it is not specified.

> android.enableJetifier: When set to true, the Android plugin automatically migrates existing third-party libraries to use AndroidX by rewriting their binaries. The flag is false by default if it is not specified.



  

  

