# ZRAM Swap Configurator

## Overview
ZRAM Swap Configurator for KernelSU(-Next) — manages zram size, algorithm, priority, and VM sysctls live or at boot.

### v3.7 (Original)
- **Install-time only**: customize.sh sed-bakes values into service.sh at flash time
- **Optionals**: `/sdcard/optionals.prop` read once at install; unset → silently defaults to **100% of RAM** (the gotcha)
- **Algorithm**: lzo / lz4 / zstd (chosen at install, baked into service.sh)
- **Boot**: service.sh runs at every boot, re-applies baked values
- **Live**: not interactive — zero vol-key/prompt code; customize.sh sourced non-interactively
- **Uninstall**: no upstream uninstall.sh → module dir removal cleans most state

### v4.0 (Interactive WebUI Fork)
- **WebUI**: opens from KernelSU manager — status readout + full settings panel
- **Apply now**: live reconfiguration with swap-busy retry loop (~60s); falls back to "applies at next boot"
- **Save**: persists config.prop for next boot only
- **Defaults**: 50% of RAM (safe default)
- **Config storage**: plain file `/data/adb/modules/ZRAMSwapConfigurator/config.prop` (survives reboots, wiped on uninstall)
- **Defaults.prop**: records ROM stock values for "def" restore semantics
- **Full expert set**: resize (%), algorithm, priority, swappiness, swap_ratio_enable/ratio, min/extra_free_kbytes, 6× lmkd props (sflp/sum/scr/scrd/med/low)
- **`ksud module config`**: NOT available on KSU-Next v1.1.1 → use plain config file instead
- **WebUI API**: uses global `ksu.exec(cmd)` — verified on device (zygisksu bundle)
- **Boot always works**: service.sh → apply.sh at every reboot; live apply depends on swap availability

## Installation
```bash
# v3.7 (original):
su -c '/data/adb/ksud module install /sdcard/Download/ZRAM-Swap-Configurator-v3.7.zip'

# v4.0 (interactive fork):
su -c '/data/adb/ksud module install /sdcard/Download/zram-v4/ZRAM-Swap-Configurator-v4.0.zip'
adb reboot
```

## Gotcha
The original v3.7 module defaults to **100% of RAM** if `optionals.prop` is unset — this can leave little room on a 4 GB device. This v4.0 fork defaults to **50%** and adds an interactive WebUI for live reconfiguration.

## Credits
- **Based on**: reiryuki's ZRAM-Swap-Configurator-Magisk-Module (MIT licensed)
- **v4.0 WebUI fork**: abr60
- **Original repo**: https://github.com/reiryuki/ZRAM-Swap-Configurator-Magisk-Module
- **Device verified**: KSU-Next v1.1.1 / driver 12851 on Redmi Note 11 (spesn, SM6225/Kryo 265, 4 GB RAM)

## Installation Notes
- First install: `/sdcard/optionals.prop` is read at install time
- To preserve existing tuning: pre-seed with `zram.resize=65%` + `zram.algo=lz4`
- After install: configure via WebUI or edit `/data/adb/modules/ZRAMSwapConfigurator/config.prop` directly
- Rollback: uninstall module → config.prop cleaned automatically