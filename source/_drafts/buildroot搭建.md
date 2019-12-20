title: buildroot搭建
author: yaoxingwei
tags: []
categories: []
date: 2019-12-20 14:14:00
---
### 1. 默认项目启动

1. Download buildroot latest version：
[Download buildroot](https://buildroot.org/download.html)

2. build 默认配置好的项目，如qemu-aarch64:
		$ make qemu_aarch64_virt_defconfig
        $ make
> 不要多线程，会导致先后顺序出错
        
3. 默认配置会download/build kernel和文件系统，生成在output/images，运行：
		$ qemu-system-aarch64 -M virt -cpu cortex-a53 -nographic -smp 1 -kernel output/images/Image -append "rootwait root=/dev/vda console=ttyAMA0" -netdev user,id=eth0 -device virtio-net-device,netdev=eth0 -drive file=output/images/rootfs.ext4,if=none,format=raw,id=hd0 -device virtio-blk-device,drive=hd0
        

### 2. 添加UBOOT

1. 在配置里面选中UBOOT
		$ make menuconfig
          -> Bootloaders
            -> U-Boot
              -> U-Boot configuration(using an in-tree board defconfig file)
              (qemu_arm64) Board defconfig
        $ make
        
2. load Uboot
		$ qemu-system-aarch64 -M virt -cpu cortex-a53 -m 256 -bios output/images/u-boot.bin --nographic


### 3. 添加UBOOT启动参数，load kernel和fs
              