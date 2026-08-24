# lmkd psi mod(ified)

**An optimization module that optimizes the Android system's memory management mechanism, lmkd.**

## Overview

The module achieves efficient background process management by modifying memory management mechanisms (lmk, psi). And by improving background process management, the system can become smoother and more energy-efficient.

This is an extension of the SkyScene-Addon focused on improving the behavior of lmkd. If you want an optimization that improves the kernel's memory management behavior, check out the [SkyScene Add-on](https://github.com/WeirdMidas/SkySceneAddon), it specifically handles this aspect, such as swapping, reclaim, and others

It was intended to be a fork of [LMKD-PSI-Activator](https://github.com/lululoid/LMKD-PSI-Activator) that optimizes the lmkd psi part more efficiently and better for Android multitasking. However, it became an original project due to the enormous difference in philosophy and optimization aspects

### Main Features

- Pure memory management optimization module, not containing other placebo and supporting all mainstream platforms like Qualcomm, MediaTek, Unisoc, and many other platforms
- Follow the lmkd guidelines and standards based on AOSP/Google, while manually tuning some parameters, making lmkd more accurate and efficient based on the upstream
- In certain lmkd properties, a cleanup is performed to prevent the ROM or other modules via `device_config` from modifying our settings, allowing us to overwrite harmful changes
- Tune the behavior of lmkd based on: Go Devices, Normal Devices with LRU, and Normal Devices with MGLRU. Ensuring that each device is treated individually
- Make lmkd see the ideal compression ratio for each swap algorithm, being LRU 2.8x and MGLRU 3.1x, it is no longer based on the compression algorithm, but on the swap algorithm, after all the "universal standard" is lz4
- SELinux can still be enabled

## Requirement

- Android 10 or higher
- Have PSI enabled in the kernel
- Have lmkd as the only LMK mechanism on the device
- Having ZRAM enabled in the kernel
- 3GB or more of RAM (Optional)

## Installation

- Install the module, restart your device, and have fun
- Other LMKs are not compatible, only lmkd is compatible

## FAQ

### Sources

- [Official information about lmkd (Low Memory Killer Daemon)](https://source-android-com.translate.goog/docs/core/perf/lmkd?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt&_x_tr_pto=tc) provided by Google

### Suggestions for Complementary Modules

- [NoSwipeToKill](https://github.com/dantmnf/NoSwipeToKill): lsposed module by [dantmnf](https://github.com/dantmnf) to reduce the aggressiveness of HyperOS/MIUI in killing processes, recommended for users of Xiaomi ROMs that use lsposed
- [A1Memory](https://github.com/OneB1ank/A1Memory): A memory management module that implements an OEM-style memory management framework in the system server, allowing you to control certain parts of memory management more efficiently than modern Android. Exclusive to Android 8-14

## Credit

@Doug Hoyte  
@topjohnwu  
@卖火炬的小菇凉--改进在红米K20pro上的zram兼容性  
@钉宫--模块配置文件放到更容易找到的位置  
@予你长情i--发现与蝰蛇杜比音效共存版magisk模块冲突导致panel读写错误  
@choksta --协助诊断v4版FSCC固定过多文件到内存  
@yishisanren --协助诊断v5版FSCC在三星平台固定过多文件到内存  
@方块白菜 --协助调试在联发科X10平台ZRAM相关功能  
@Simple9 --协助诊断在Magisk低于19.0的不兼容问题  
@〇MH1031 --协助诊断位于/system/bin二进制工具集的不兼容问题  
@yc9559 -- Obvious credits that I forgot to put, SkyScene only exists because of him, the GOAT of the 2018-2020 modules      
@Iamlooper -- For the magisk MMT Reborn template. Thanks to the template, I was able to replace the old qti-mem-opt template and keep all the features without extra additions! Also now the cpu usage of the module has reduced by 2%, little but useful      
