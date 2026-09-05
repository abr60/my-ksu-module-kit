# ZRAM Manager — Interactive WebUI Fork

A WebUI-based fork of reiryuki's [ZRAM-Swap-Configurator-Magisk-Module](https://github.com/reiryuki/ZRAM-Swap-Configurator-Magisk-Module) (MIT licensed).

## What's New
- **WebUI**: opens from KernelSU manager with status readout + full settings panel
- **Apply & Reboot**: saves config and immediately reboots — changes take effect on next boot (fast, always-clean)
- **Defaults**: 50% of RAM (safe default); override by pre-seeding `/sdcard/optionals.prop` with `zram.resize=65%` + `zram.algo=lz4`

## Releases

| Variant | Tag | Recommendation |
|---|---|---|
| **v3** | `zram-v4-azenith` (latest) | ✅ **Use this one** — 3-page UI, profiles, live calculator, `ksu.exec` fix, Apply & Reboot |
| v2 | `zram-v4-zygisk` | Zygisk-Next-style dark UI — has known `ksu.exec` callback bug (status stuck at `--`) |
| v1 | `zram-v4-draft` | First iteration — minimal status card UI |

All three zips are also mirrored under [`zram-manager/releases/`](./releases/). See [`CHANGELOG.md`](./CHANGELOG.md) for SHAs.

## Installation
```bash
su -c '/data/adb/ksud module install /sdcard/Download/zram-manager/ZRAM-Swap-Configurator-v4.0-v3-azenith.zip'
adb reboot
```

## Gotcha
The original v3.7 module defaults to **100% of RAM** if `optionals.prop` is unset — this can leave little room on a 4 GB device. This fork defaults to **50%** and adds a WebUI for easy tuning.

## Credits
Based on [reiryuki's ZRAM-Swap-Configurator](https://github.com/reiryuki/ZRAM-Swap-Configurator-Magisk-Module) (MIT). WebUI uses KernelSU-Next `ksu.exec` root-shell API.
