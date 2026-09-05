# ZRAM Swap Configurator v4.0 — Interactive WebUI Fork

A WebUI-based fork of reiryuki's [ZRAM-Swap-Configurator-Magisk-Module](https://github.com/reiryuki/ZRAM-Swap-Configurator-Magisk-Module) (MIT licensed).

## What's New
- **WebUI**: opens from KernelSU manager with status readout + full settings panel
- **Apply now**: live reconfiguration with swap-busy retry loop (~60s)
- **Save**: persists config for next boot
- **Defaults**: 50% of RAM (safe default); override by pre-seeding `/sdcard/optionals.prop` with `zram.resize=65%` + `zram.algo=lz4`

## Releases

Three v4.0 variants are published — see the [releases page](https://github.com/abr60/my-ksu-module-kit/releases) or [`CHANGELOG.md`](./CHANGELOG.md) for details and SHA-256 checksums:

| Variant | Tag | Recommendation |
|---|---|---|
| **v3 AZenith-inspired** | `zram-v4-azenith` (latest) | ✅ **Use this one** — 3-page UI (Status/Tuning/Advanced), profiles, live calculator, `ksu.exec` fix |
| v2 Zygisk-Next style | `zram-v4-zygisk` | Historical — has a known `ksu.exec` callback bug (status stuck at `--`) |
| v1 Draft | `zram-v4-draft` | First iteration — minimal status card UI |

All three zips are also mirrored under [`zram-v4/releases/`](./releases/).

## Installation
```bash
su -c '/data/adb/ksud module install /sdcard/Download/zram-v4/ZRAM-Swap-Configurator-v4.0-v3-azenith.zip'
adb reboot
```

## Gotcha
The original v3.7 module defaults to **100% of RAM** if `optionals.prop` is unset — this can leave little room on a 4 GB device. This v4.0 fork defaults to **50%** and adds an interactive WebUI for live reconfiguration.

## Credits
Based on [reiryuki's ZRAM-Swap-Configurator](https://github.com/reiryuki/ZRAM-Swap-Configurator-Magisk-Module) (MIT). WebUI uses KernelSU-Next `ksu.exec` root-shell API.
