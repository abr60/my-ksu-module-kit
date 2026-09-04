# systemless-hosts KernelSU-module

## Overview
Required module to use applications such as AdAway on KernelSU(-Next) and APatch. Modifies the hosts system_ext partition to block ads and trackers at the DNS level.

- **Version**: v1.2.2
- **Author**: symbuzzer (avalibeyaz.com/github)
- **Compatibility**: KernelSU(-Next) and APatch
- **WebUI**: web=true — webroot/index.html exists (142B meta-refresh redirect to GitHub)
- **Module ID**: systemless-hosts-KernelSU-module

## Installation
```bash
su -c '/data/adb/ksud module install /sdcard/Download/systemless-hosts.zip'
adb reboot
```

## Credits
- **Author**: symbuzzer
- **Repo**: https://github.com/symbuzzer/systemless-hosts-KernelSU-module
- **License**: GPL/as-is

## Notes
- Hosts overlay mounted: `KSU /system/etc overlay ... upperdir=/data/adb/modules/systemless-hosts-KernelSU-module/system/etc`
- Confirmed no kernel/perf conflict with Gamespace or AZenith (different layer: SystemUI/display)
- `dumpsys game` = "No intervention found for package com.tencent.ig" — separate layer
- Also found RDTP (Poco F6 thermal) — unrelated to this module
- `android.hardware.power-service.xiaomi-libperfmgr` is the device PowerHAL (present, unrelated)