# react-native 打包APK

> Android要求所有应用都有一个数字签名才会被允许安装在用户手机上，所以在把应用发布到类似Google Play store这样的应用市场之前，你需要先生成一个签名的APK包。Android开发者官网上的如何给你的应用签名文档描述了签名的细节。本指南旨在提供一个简化的签名和打包js的操作步骤，不会涉及太多理论。

## 1. 生成一个签名密钥

```
keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
```

这条命令会要求你输入密钥库（keystore）和对应密钥的密码，然后设置一些发行相关的信息。最后它会生成一个叫做`my-release-key.keystore`的密钥库文件。

 在运行上面这条语句之后，密钥库里应该已经生成了一个单独的密钥，有效期为10000天。--alias参数后面的别名是你将来为应用签名时所需要用到的，所以记得记录这个别名。

**提示:如果上面的命令执行有错,它会给出新的命令行提示,使用新的命令行就可以了.**

## 2.设置gradle变量

1. 把`my-release-key.keystore`文件放到你工程中的`android/app`文件夹下。

2. 编辑`~/.gradle/gradle.properties`（没有这个文件你就创建一个），添加如下的代码（注意把其中的`****`替换为相应密码）

  **~表示用户目录，比如windows上可能是C:\Users\用户名，而mac上可能是/Users/用户名。**

  ```
  MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
  MYAPP_RELEASE_KEY_ALIAS=my-key-alias
  MYAPP_RELEASE_STORE_PASSWORD=*****
  MYAPP_RELEASE_KEY_PASSWORD=*****
  ```

## 3.添加签名到项目的gradle配置文件

编辑你项目目录下的`android/app/build.gradle`，添加如下的签名配置：

```
...
android {
    ...
    defaultConfig { ... }
    signingConfigs {
        release {
            storeFile file(MYAPP_RELEASE_STORE_FILE)
            storePassword MYAPP_RELEASE_STORE_PASSWORD
            keyAlias MYAPP_RELEASE_KEY_ALIAS
            keyPassword MYAPP_RELEASE_KEY_PASSWORD
        }
    }
    buildTypes {
        release {
            ...
            signingConfig signingConfigs.release
        }
    }
}
...
```
![这里写图片描述](https://img-blog.csdn.net/20180604150700807?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## 4. 生成发行APK包

```
$ cd android && ./gradlew assembleRelease
```

生成的APK文件位于android/app/build/outputs/apk/app-release.apk，它已经可以用来发布了。
如果生成的Apk的名称为app-release.apk,则说明可以了;否则,打包过程就是有问题的,这时候要检测哪一步有问题改好就可以