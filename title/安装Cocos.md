# Mac安装配置Cocos

<h3>1、下载</h3>

<a href='http://cocos2d-x.org/filedown/CocosCreator_v1.9.0_mac'>快速下载</a>

<a href='http://www.cocos.com/download'>Cocos 版本选择</a>

<h3>2、安装</h3>
将下载好文件解压出来，然后移至 `/usr/local/` 目录下；

在终端切换路径至`cocos`目录下，运行命令`./setup.py`；

安装过程中需要配置 `Android NDK` `Android SDK` `Ant` 相关路径；

如未下载上述文件，可前往下载：

> <a href='android-ndk-r16b-darwin-x86_64.zip'>Android NDK快速下载</a>，
> <a href='https://developer.android.google.cn/ndk/downloads/index.html'>Android NDK版本选择<a>
> 
> <a href='https://dl.google.com/android/android-sdk_r24.4.1-macosx.zip'>Android SDK 24 下载</a>
> 
> <a href='http://mirrors.shu.edu.cn/apache//ant/binaries/apache-ant-1.10.2-bin.zip'>Ant 快速下载</a>，<a href='https://ant.apache.org/bindownload.cgi'>Ant 版本选择</a>
> 
> 然后将以上下载好文件解压出来，放至`/usr/local`中，（可放可不放）然后将对应的路径填给`NDK_ROOT` `ANDROID_SDK_ROOT` `ANT_ROOT`。

	配置如下： 
	NDK_ROOT = /usr/local/android-ndk-r16b
	ANDROID_SDK_ROOT = /usr/local/android-sdk
	ANT_ROOT = /usr/local/apache_ant-1.10/bin


<h1><a href='../README.md'>返回列表</a> </h1>