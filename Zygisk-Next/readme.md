# Zygisk Next 1.5.0

## Overview
Standalone Zygisk implementation for KernelSU-Next v1.1.1 (driver 12851). Provides zygote secondary support, root access (KernelSU 12851), and Zygisk-based features.

- **Version**: 1.5.0 (843-5217106-release)
- **Authors**: 5ec1cff, Nullptr, aviraxp
- **Root**: ✅ KernelSU (12851), ZL
- **Zygote**: ✅ zygote, zygote_secondary
- **WebUI**: enabled (uses `ksu.exec` API via compiled bundle)
- **Module ID**: zygisksu
- **Module list**: web=true, action=true

## Installation
```bash
su -c '/data/adb/ksud module install /sdcard/Download/Zygisk-Next-1.5.0-843-5217106-release.zip'
adb reboot
```

## Credits
- **Author**: Dr-TSNG
- **Repo**: https://github.com/Dr-TSNG/ZygiskNext
- **Release**: v1.5.0 released via GitHub (7,529,581 B)
- **Key commit**: 843-5217106-release

## Notes
- Module list confirmed: 4 modules total after install (AZenith, Zygisk Next, ZRAM, hosts)
- WebUI on this device uses global `ksu.exec` bridge (verified from zygisksu's compiled bundle)
- No `ksud module config` subcommand available on KSU-Next v1.1.1
- Stable on Redmi Note 11 (spesn, SM6225/Kryo 265, 4 GB RAM)