# 游戏大厅接入文档(Android)

## 接入前准备工作：
*  需要引用的三方库：

    ``` implementation 'androidx.appcompat:appcompat:1.0.0'
    implementation 'androidx.recyclerview:recyclerview:1.0.0'
    implementation "androidx.tonyodev.fetch2:xfetch2:3.1.4"
    implementation "androidx.tonyodev.fetch2okhttp:xfetch2okhttp:3.1.4"
    implementation 'com.github.lzyzsd:jsbridge:1.0.4'
    implementation 'com.google.code.gson:gson:2.8.5'
    // retrofit 网络请求库
    implementation 'com.squareup.retrofit2:retrofit:2.5.0'
    implementation 'com.squareup.retrofit2:converter-gson:2.5.0'
    implementation 'com.squareup.okhttp3:logging-interceptor:3.4.1'
    // Glide 图片库
    implementation 'com.github.bumptech.glide:glide:3.7.0' 
    //适配器
    implementation 'com.github.CymChad:BaseRecyclerViewAdapterHelper:2.9.46'
    ```
*  配置App秘钥:
   ```
      manifestPlaceholders = [
                MPON_APPID: '1562893435',
                SECRET_KEY: '7e484c83028a71ce945881f8db568a39'
        ]
      ````
      其中MPON_APPID 和 SECRET_KEY 需到开发者后台管理界面申请
      
## SDK接入
*  build.gradle配置:将SDK的aar文件导入libs库中，然后在build.gradle中配置：
   ``` 
   repositories {
        flatDir {
            dirs 'libs'
        }
    }
   ```
   以及项目依赖；
   ```
       api(name: 'mpon_game_sdk', ext: 'aar')
   ```
*  初始化 
   在项目中的Application中的onCreate方法中初始化，代码如下
   ```
   MponSdk.getInstance().init(getApplicationContext(), MponParam.create().builder());
   ```
*  接入游戏列表页面
   游戏列表页面对应的是一个GameFragment，开发者只需要将此GameFragment附在指定界面即可:
   ```
            GameFragment  mGameFragment = new GameFragment();
                    getSupportFragmentManager()
                            .beginTransaction()
                            .add(android.R.id.content, mGameFragment)
                            .commitAllowingStateLoss();
   ```
   
*  代码混淆

  ```
-keep class com.bytedance.sdk.openadsdk.** {*;}
-keep public interface com.bytedance.sdk.openadsdk.downloadnew.** {*;}
-keep class com.ss.sys.ces.* {*;}

-keep public class * extends com.xiaozi.mpon.sdk.core.NoProguard{ *; }
-keep class com.google.gson.examples.android.model.** { *; }
-keepclassmembers class * implements java.io.Serializable {
static final long serialVersionUID;
private static final java.io.ObjectStreamField[] serialPersistentFields;
private void writeObject(java.io.ObjectOutputStream);
 private void readObject(java.io.ObjectInputStream);
 java.lang.Object writeReplace();
java.lang.Object readResolve();
}
-keep public class * implements java.io.Serializable {*;}

# Glide
-keep public class * implements com.bumptech.glide.module.GlideModule
-keep public enum com.bumptech.glide.load.resource.bitmap.ImageHeaderParser$** {
  **[] $VALUES;
  public *;
}

-keep class com.google.android.material.** {*;}
-keep class androidx.** {*;}
-keep public class * extends androidx.**
-keep interface androidx.** {*;}
-dontwarn com.google.android.material.**
-dontnote com.google.android.material.**
-dontwarn androidx.**
  ```
