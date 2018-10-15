# Android混淆

## Proguard基本语法
    1.保留类名
    2.保留方法名
    3.保留类名和方法名
    
    问题：混淆为什么要保留类名或方法名
    （1）让C/C++程序可以通过jni使用对应的java方法
    （2）四大组件由于在AndroidManifest.xml里面注册了，所以需要保留
    （3）R文件混淆会导致引用错误
    
## 使用Proguard去除日志信息
    我们在开发时，经常会输出各种日志来debug代码。但是等到应用发布的apk运行时却不希望它输出日志
    我们可以通过配置proguard，将android.util.Log类的方法置为无效代码，可以去除apk中打印日志的代码
    
    不输出log的两种方式：
    （1）封装一个log wrapper
    （2）直接删除打印log代码
    -assumenosideeffects class android.util.Log{
        public static boolean isLoggable(java.lang.String,int);
        public static int v(...);
        public static int i(...);
        public static int w(...);
        public static int d(...);
        public static int e(...);
    }
    
## 对抗反编译工具
    对抗反编译是指让apk文件或者dex文件无法正常通过反编译工具，而且有可能导致工具异常或者崩溃，如apktool，baksmali，dex2jar，JEB等等工具
   

