# Android ROM Development Notes

This is the place where I'll put my notes, so anyone who is interested in developing/building Android
ROMs by himself could use this as guide... I hope this would help...

This guide mostly focuses on building [LineageOS](https://lineageos.org/)...

## Contents

- [About Creating Device Tree](#about-creating-device-tree)
  - [BoardConfig.mk](#boardconfigmk)
- [Resources](#resources)

## About Creating Device Tree

These files are the essentials of the device tree: BoardConfig.mk, [codename].mk, *.mk, fstab..

I'll start with **BoardConfig.mk**

### BoardConfig.mk

This file contains build info your device's CPU, motherboard, and other hardware...
Some bare_bone configurations:

- **TARGET_ARCH**: this is the architecture of the device it is usually something like arm, arm64, omap3...
- **BOARD_KERNEL_CMDLINE**: this is the kernel parameters for your device to boot properly, not all devices pass kernel parameters.
anyway you could easily find this information on *ramdisk.img* or you could just do this:
```bash
file boot.img
```
this should print sth. like:
```
boot.img: Android bootimg, kernel, ramdisk, page size: 2048, cmdline (androidboot.console=ttyHSL0 androidboot.hardware=qcom user_debug=30 msm_rtb.filter=0x237 ehci-hcd.park=3 androidboot.bootdevice)
```
a part of the kernel parameters can be easily pointed with just with `file` command...
- **BOARD_KERNEL_PAGESIZE**: the pagesize of the stock boot.img and must be set properly in order to boot. Typical values for this are 2048 and 4096 and this information can be extracted from the stock kernel. You can also get this attribute via the above command `file boot.img`.

## Resources

- [https://fat-tire.github.io/porting-intro.html#Some_tips_on_porting_CyanogenMod_to_your_own_device](https://fat-tire.github.io/porting-intro.html#Some_tips_on_porting_CyanogenMod_to_your_own_device)
