# fastboot 烧写3288镜像(参考RockChip_Uboot_V3.3.pdf)

默认设备是处于未解锁状态的,所以先要解锁设备才可以使用fastboot烧写

## 查看设备解锁状态

1. 首先让设备进入到fastboot状态,可以在uboot命令行下执行fastboot

2. 在主机端查询解锁状态

	fastboot getvar unlocked

	如果提示未发现设备

	fastboot -i 0x2207 getvar unlocked

## 解锁设备
1. 主机端执行 fastboot oem unlock

2. 5秒内继续执行 fastboot oem unlock_accept

3. 机器会重启进入 recovery 恢复出厂设置

4. 再次进入 fastboot,则fastboot getvar unlocked 应该返回"yes"(设备已解锁)

## fastboot烧写镜像

### 烧写uboot(-i 执行设备idVendor, loader对应3288 uboot)

fastboot -i 0x2207 flash loader RK3288UbootLoader_V2.19.09.bin

### 烧写parameter

fastboot -i 0x2207 flash parameter parameter

### 重启进recovery

fastboot -i 0x2207 oem recovery

### 解锁和锁住设备

fastboot oem unlock 解锁

fastboot oem unlock_accept 确认解锁 (需要在 fastboot oem unlock 命令后,5 秒内输入)

fastboot oem lock 锁住设备

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
