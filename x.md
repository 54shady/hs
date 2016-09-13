```shell
sudo mkdir -p /usr/local/portage/sys-apps/rkflashkit
sudo ebuild /usr/local/portage/sys-apps/rkflashkit/rkflashkit-0.1.4.ebuild manifest
sudo emerge -v sys-apps/rkflashkit

rkflashkit usage example
sudo rkflashkit part
sudo rkflashkit flash @kernel kernel.img @resource resource.img reboot
```
