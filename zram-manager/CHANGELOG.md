# Changelog — ZRAM Manager (Interactive WebUI Fork)

All builds flashable via `ksud module install`. See the [releases page](https://github.com/abr60/my-ksu-module-kit/releases) to download; all three zips are also mirrored under [`zram-manager/releases/`](./releases/).

| Release | Tag | Zip | SHA-256 |
|---|---|---|---|
| v1 Draft | [`zram-v4-draft`](https://github.com/abr60/my-ksu-module-kit/releases/tag/zram-v4-draft) | `ZRAM-Swap-Configurator-v4.0-v1-draft.zip` | `134af3abb84688910b3b7a162f60b8b9371c3e2057387f6afcbe3220fde5e810` |
| v2 Zygisk-Next | [`zram-v4-zygisk`](https://github.com/abr60/my-ksu-module-kit/releases/tag/zram-v4-zygisk) | `ZRAM-Swap-Configurator-v4.0-v2-zygisk.zip` | `563001c5d510fb39cdf4f6cb978e4e499c3cd38aec2f90c64ff5ed6aba34b545` |
| v3 AZenith-inspired (latest) | [`zram-v4-azenith`](https://github.com/abr60/my-ksu-module-kit/releases/tag/zram-v4-azenith) | `ZRAM-Swap-Configurator-v4.0-v3-azenith.zip` | `4df04b51ba2b3620b55fe7a63aaaac899ee018e6150e0a5841a96cbcf7005026` |

> **All three builds ship `updateJson`** → [`zram-manager/update.json`](./update.json) in this repo. Installing *any* of them wires KernelSU-Next Manager to the update channel: it will auto-offer the latest build (currently v3, versionCode 42). v1/v2 are versionCode 40; v3 is versionCode 42 so the channel always reports newer.

---

## v3 — ZRAM Manager (`zram-v4-azenith`) ✅ **recommended** — `v3 / versionCode 42`

Full 3-page redesign in a cyber-obsidian theme, inspired by (but not copying) AZenith styling.

- 3-page layout with floating glass bottom pill nav: **Status / Tuning / Advanced**
- **Status**: hero memory-core card, 2x2 stat grid, device memory architecture readout
- **Tuning**: 1-tap profiles (Eco/Balanced/Performance/Gaming/Disable), live allocation slider with byte calculator, algorithm chips, swappiness stepper, swap priority
- **Advanced**: `min_free_kbytes`, `extra_free_kbytes`, `swap_ratio` (enable/ratio), LMKD props (`sflp`, `sum`, `scr`, `scrd`, `med`, `low`) with helpers
- **Apply & Reboot**: saves `config.prop` and immediately reboots — no live swap rebuild (fast, always-clean)
- **Bench logger** (`bench.sh`): every Apply snapshots the outgoing config's session (compression ratio, swap fill, stall pressure, swap churn) into `/data/adb/zram-manager/bench.log`, which survives reboots + updates; boot marker per session; Advanced page has **Snapshot** (log now) + **Report** (per-resize scoreboard) buttons
- **Bug fix**: correct `ksu.exec` callback protocol — live status now updates correctly

## v2 — Zygisk-Next style (`zram-v4-zygisk`) — `v2 / versionCode 40`

Dark obsidian single-page UI (Zygisk-Next inspired): live calculators, profile presets.

- ⚠️ **Known bug**: `ksu.exec` called with JS function object as callback — live status stays at `--`. Fixed in v3.

## v1 — Draft (`zram-v4-draft`) — `v1 / versionCode 40`

First iteration: simple status card with live status + Refresh button.
