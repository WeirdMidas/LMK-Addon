# LMKD PSI Activation + Misc
An extension of the SkyScene Add-on, where it achieves the effect of preventing background apps from dying by modifying memory management mechanisms (lmk, psi). And by improving background process management, it's possible to achieve a smoother and more energy-efficient system.

If you want an optimization that improves the kernel's memory management behavior, check out the [SkyScene Add-on](https://github.com/WeirdMidas/SkySceneAddon), it specifically handles this aspect, such as swapping, reclaim, and others.

### Features
- Pure background memory management optimization module (lmk, psi), without other side effects or placebos, and compatible with all major platforms, from Qualcomm to Mediatek, Unisoc, and others. It only requires using lmkd as the primary LMK module in the ROM
- Utilize lmkd's modern pressure mechanism, PSI (pressure stall information), allowing lmkd to kill background processes based on whether the system can handle keeping them running in memory. It doesn't depend on fixed thresholds or anything like that
  - Based on hardware differences, not as a "one formula" for everyone, differentiate lmkd parameters based on hardware and others, allowing each device to have its efficiency respected
- Improve oom reaper scheduling, make it execute with the policies we want, as in the foreground cpuset and with the affinity in the big/prime cores, reducing the stalls that occur when killing a process in the background

## Requirement

- Compatible with ARM64 and standard ARM
- Magisk, KSU or Apatch, the most up-to-date version possible if you can
- Android 10 or higher. Not compatible with versions below 10
- You need at least 3GB of RAM to use it. Modern Android requires this as a minimum amount of RAM. However, it is still compatible with devices that have less RAM
- It is recommended to use an additional busybox module for situations where the module cannot use the busybox from Magisk or the ROM
- Depending on the ROM or kernel you are using on your device, you may experience compatibility issues if they are heavily modified

## Installation

- Install this module, restart your phone, wait 20 seconds before the final optimizations are applied, and voila, you can have fun with your device.
- Simple LMK is currently not supported.
- Per-Process LMK is currently not supported.
- Old LMK is currently not supported.

## FAQ

### Sources

- Official information about [LMKD (Low Memory Killer Daemon)](https://source-android-com.translate.goog/docs/core/perf/lmkd?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt&_x_tr_pto=tc) provided by Google.
- Some tips and reports on how the lmkd + oom reaper scheduling works on the AxionOS custom ROM. This is beneficial for reducing stalls that occur due to high memory usage when lmkd needs to kill something.

### Suggestions for Complementary Modules

- [A1Memory](https://github.com/OneB1ank/A1Memory): A memory management module that implements an OEM-style memory management framework in the system server, allowing you to control certain parts of memory management more efficiently than modern Android. Exclusive to Android 8-14.

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
