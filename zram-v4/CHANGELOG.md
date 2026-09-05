# Changelog — ZRAM Swap Configurator v4.0 (Interactive WebUI Fork)

All v4.0 snapshots are flashable via `ksud module install`. See the [releases page](https://github.com/abr60/my-ksu-module-kit/releases) to download; all three zips are also mirrored under [`zram-v4/releases/`](./releases/).

| Release | Tag | Zip | SHA-256 |
|---|---|---|---|
| v1 Draft | [`zram-v4-draft`](https://github.com/abr60/my-ksu-module-kit/releases/tag/zram-v4-draft) | `ZRAM-Swap-Configurator-v4.0-v1-draft.zip` | `11bd1796b24eb0f66810dfa808e80c9db7530b9348f9eac042ff740bb3095881` |
| v2 Zygisk-Next | [`zram-v4-zygisk`](https://github.com/abr60/my-ksu-module-kit/releases/tag/zram-v4-zygisk) | `ZRAM-Swap-Configurator-v4.0-v2-zygisk.zip` | `e0d6309413731dbc643f9aeaff150fa64fdacf91f0c89083c47da497463c2f04` |
| v3 AZenith-inspired | [`zram-v4-azenith`](https://github.com/abr60/my-ksu-module-kit/releases/tag/zram-v4-azenith) (latest) | `ZRAM-Swap-Configurator-v4.0-v3-azenith.zip` | `61bb0947b54fb6d3b73d47a80dbed7385497446d38ffa7d6067d984591acc818` |

---

## v3 — AZenith-inspired (`zram-v4-azenith`) ✅ **recommended**

Full 3-page redesign in a cyber-obsidian theme, inspired by (but not copying) the AZenith WebUI style.

- 3-page layout with floating glass bottom pill nav: **Status / Tuning / Advanced**
- **Status**: hero memory-core card (zram size, algorithm, priority, live utilization bar), 2×2 stat grid (physical RAM, zram ratio, algorithm, swappiness), device memory architecture readout
- **Tuning**: 1-tap tuned profiles (Eco Saver 35%, Balanced 50%, Performance 65%), allocation slider with live byte calculator (0–150%, custom value input), compression algorithm chips (lzo/lz4/zstd), swappiness stepper, swap priority
- **Advanced**: `min_free_kbytes`, `extra_free_kbytes`, `swap_ratio` (enable/ratio), LMKD props (`sflp`, `sum`, `scr`, `scrd`, `med`, `low`) with `def`/`clear`/`unset`/`toggle` helpers
- Save & Apply-Now modal with live terminal output; 12 s command timeout
- **Bug fix**: correct `ksu.exec` callback protocol (per-call callback slot + timeout) — live status no longer stuck at `--`
- Verified: headless-rendered all 3 pages (412 px mobile viewport), `bash -n` clean on all scripts, live apply tested on device

## v2 — Zygisk-Next style (`zram-v4-zygisk`)

Dark obsidian single-page UI (Zygisk-Next inspired): real-time memory calculators, tuned profiles, live apply.

- ⚠️ **Known bug**: `ksu.exec` called with a JS function object as callback instead of the name of a registered global callback — live status stays at `--` (applies still work). Fixed in v3.

## v1 — Draft (`zram-v4-draft`)

First interactive WebUI iteration: simple status card with **Live status** readout and **Refresh** button. Baseline for the v4.0 fork.