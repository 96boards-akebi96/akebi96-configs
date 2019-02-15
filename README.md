# Akebi96 Kernel Configs

## What is this?

This is an independent repository of linux and u-boot configurations
for Akebi96 board.
Akebi96 board consists of UniPhier LD20 SoC and some on-board chips. These
configurations enables required drivers and options. Also there is a config
file which provides some additional options for AOSP kernel and bootloader.

## How can I use this?

You can use these configs merging with arm64 defconfig as below;

```
 $ AKEBI96=<this repositry>
 $ cd linux
 $ make defconfig
 $ ./scripts/kconfig/merge_config.sh .config ${AKEBI96}/linux/akebi96-base.config
```

For AOSP, you have to merge it with [Android Kernel Configs](https://android.googlesource.com/kernel/configs) as below;

```
 $ AKEBI96=<this repositry>
 $ AKC=<Android Kernel Configs>
 $ KVERSION=<base kernel version>
 $ cd linux
 $ make defconfig
 $ ./scripts/kconfig/merge_config.sh .config \
   ${AKEBI96}/linux/akebi96-base.config \
   ${AKC}/android-${KVERSION}/android-base.config \
   ${AKC}/android-${KVERSION}/android-recommended.config \
   ${AKC}/android-${KVERSION}/android-recommended-arm64.config \
   ${AKEBI96}/linux/akebi96-aosp-vendor.config
```

In addition, you can enable development features by linux/akebi96-development.config.
