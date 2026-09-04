# AZenith v5.2

## Overview
AIO performance module for KernelSU-Next with auto game detection, process priority control, game preload, CPU governor, I/O scheduler, CPU freq limiter, thermal management, and per-app tweaks.

- **Auto Profiles**: Detects games via `dumpsys` → switches between Performance/Balanced/ECO
- **Process Priority**: "Intelligently freees unnecessary background bloatware" to free RAM
- **Game Preload**: Preloads game libraries on open
- **WebUI → Manager APP**: `zx.azenith` with 84 languages
- **Rust daemons**: `sys.azenith-service`, `sys.azenith-profilesettings`, `sys.azenith-appmonitoring`, `sys.azenith-preloadbin`, `sys.azenith-utilityconf`, `sys.azenith-rianixiathermalcore`
- **Config**: per-file SHA256 verified in zip, 84 languages
- **Compatibility**: Android 11+ (v5.0.4 lowered min to A11); v1.9 earlier had "Special Performance Module for MediaTek!" tag but v5.2 is universal

## Installation
```bash
su -c '/data/adb/ksud module install /sdcard/Download/AZenith-5.2.zip'
adb reboot
```

## Credits
- **Author**: Liliya2727
- **Repo**: https://github.com/Liliya2727/AZenith
- **License**: Apache 2.0
- **Stars**: 119 (as of Aug 2026)

## Notes
- v5.2 is the latest (Aug 19, 2026); earlier v1.9 era carried MediaTek tag but universal build
- Do not stack with DragonBoost (conflicting CPU/GPU tweaks)
- Gamespace (`io.chaldeaprjkt.gamespace`) operates at SystemUI/display layer — no kernel/perf conflict