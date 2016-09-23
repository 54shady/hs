# rkflashkit

### fetch source code

sudo mkdir -p /usr/local/portage/sys-apps/rkflashkit

sudo ebuild /usr/local/portage/sys-apps/rkflashkit/rkflashkit-0.1.4.ebuild manifest

sudo emerge -v sys-apps/rkflashkit

### rkflashkit usage example
sudo rkflashkit part

sudo rkflashkit flash @kernel kernel.img @resource resource.img reboot

# rkflashtool

### fetch source code

git@github.com:linux-rockchip/rkflashtool.git

### compile

make

### usage

rkflashtool b                         reboot device

rkflashtool r partname > file          read flash partition

rkflashtool w partname < file          write flash partition

# depend
[I] dev-libs/libusb 1.0.19-r1

[I] dev-libs/libusb-compat 0.1.5-r2

#命令行启动android应用程序

[参考文章http://blog.csdn.net/wlsfling/article/details/42527083](http://blog.csdn.net/wlsfling/article/details/42527083)

[参考文章http://www.cnblogs.com/greatverve/archive/2012/02/10/android-am.html](http://www.cnblogs.com/greatverve/archive/2012/02/10/android-am.html)

###使用am命令

```shell
# am start -n ｛(package)包名｝/｛包名｝.{活动(activity)名称}
程序的入口类可以从每个应用的AndroidManifest.xml的文件中得到,以计算器(calculator)为例,它的
AndroidManifest.xml文件位于packages/apps/Calculator/AndroidManifest.xml

<manifest xmlns:android="http://schemas.android.com/apk/res/android"

package="com.android.calculator2"

由此计算器(calculator)的启动方法为:# am start -n com.android.calculator2/com.android.calculator2.Calculator
```

```shell
播放本地视频
# am start -a android.intent.action.VIEW -d your_video_file.mp4 -t "video/*"
```
