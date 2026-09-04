# ZRAM Swap Configurator v4.0 — Interactive WebUI Fork

A WebUI-based fork of reiryuki's [ZRAM-Swap-Configurator-Magisk-Module](https://github.com/reiryuki/ZRAM-Swap-Configurator-Magisk-Module) (MIT licensed).

## What's New
- **WebUI**: opens from KernelSU manager with status readout + full settings panel
- **Apply now**: live reconfiguration with swap-busy retry loop (~60s)
- **Save**: persists config for next boot
- **Defaults**: 50% of RAM (safe default); override by pre-seeding `/sdcard/optionals.prop` with `zram.resize=65%` + `zram.algo=lz4`

## Installation
```bash
su -c '/data/adb/ksud module install /sdcard/Download/zram-v4/ZRAM-Swap-Configurator-v4.0.zip'
adb reboot
```

## Gotcha
The original v3.7 module defaults to **100% of RAM** if `optionals.prop` is unset — this can leave little room on a 4 GB device. This v4.0 fork defaults to **50%** and adds an interactive WebUI for live reconfiguration.

## Credits
Based on [reiryuki's ZRAM-Swap-Configurator](https://github.com/reiryuki/ZRAM-Swap-Configurator-Magisk-Module) (MIT). WebUI uses KernelSU-Next `ksu.exec` root-shell API.
