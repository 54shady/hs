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
