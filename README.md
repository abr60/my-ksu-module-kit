# my-ksu-module-kit

Curated KernelSU module collection for Redmi Note 11 (spes) on crDroid 9.34 (Android 13) with KernelSU-Next v1.1.1.

---

## 📦 Modules included (all verified installed on device)

| Module | Version | Author / Original Repo |
|---|---|---|
| **AZenith** | v5.2 (1823-bf02195-Dazzling) | Liliya2727 / https://github.com/Liliya2727/AZenith (Apache 2.0) |
| **Zygisk Next** | 1.5.0 (843-5217106-release) | Dr-TSNG / https://github.com/Dr-TSNG/ZygiskNext |
| **ZRAM Swap Configurator** | v3.7 | Rei Ryuki (The Fixer) / https://github.com/reiryuki/ZRAM-Swap-Configurator-Magisk-Module (MIT) |
| **systemless-hosts-KernelSU-module** | v1.2.2 | symbuzzer (avalibeyaz.com/github) / https://github.com/symbuzzer/systemless-hosts-KernelSU-module (GPL/as-is) |

---

## 🛠 Installation

Each module can be installed via `ksud module install /path/to/module.zip`.

Example (via ADB):

```bash
su -c '/data/adb/ksud module install /sdcard/Download/AZenith-5.2.zip'
adb reboot
```

All modules are compatible with KernelSU-Next v1.1.1 / driver 12851 on the Redmi Note 11 (spes, SM6225/Kryo 265, 4 GB RAM).

---

## 📄 License

This repo and its README are published under the [MIT License](LICENSE). Each module zip retains its original license — see each module's own LICENSE file inside its zip.

---

## 📬 Contact

Maintained for personal use on a Redmi Note 11 (spes). Questions or issues? Open an issue on the relevant upstream repo linked above.

---

### Build / generate this repo

```bash
git init
git add .
git commit -m "Initial: curated KernelSU modules for Redmi Note 11 spes"
git remote add origin git@github.com:abr60/my-ksu-module-kit.git
git push -u origin main
```