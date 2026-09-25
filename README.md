<div align="center">

# Shizuku+

The advanced privileged-process manager for Android.

An enhanced version of [Shizuku](https://github.com/RikkaApps/Shizuku) built on top of [thedjchi/Shizuku](https://github.com/thedjchi/Shizuku), with quality-of-life improvements, backported optimizations, and exclusive Plus APIs.

Shizuku lets normal apps use system-level APIs directly via a privileged process started with adb or root. Shizuku+ keeps full compatibility while adding features for power users and developers.

[![Stars](https://img.shields.io/github/stars/thejaustin/ShizukuPlus?style=for-the-badge&color=bfb330&labelColor=807820)](https://github.com/thejaustin/ShizukuPlus/stargazers)
[![Downloads](https://img.shields.io/github/downloads/thejaustin/ShizukuPlus/total?style=for-the-badge&color=bf7830&labelColor=805020)](https://github.com/thejaustin/ShizukuPlus/releases)
[![Latest Release](https://img.shields.io/github/v/release/thejaustin/ShizukuPlus?style=for-the-badge&color=3060bf&labelColor=204080&label=Latest)](https://github.com/thejaustin/ShizukuPlus/releases/latest)

**🌐 Languages:** **English** · [Simplified Chinese](README.zh-CN.md)

</div>

> **Contributors welcome!** If you've found a bug or want to improve the codebase, please open an issue or pull request — the project is actively looking for contributors and collaborators.

## 🇨🇳 Simplified Chinese (zh-rCN) Localization

Simplified Chinese is maintained in this fork. **To contribute Chinese translations, or to report a wording issue, open an issue or a pull request in this repository — feedback and submissions are reviewed on a daily schedule.**

Chinese documentation: [README.zh-CN.md](README.zh-CN.md)

### Coverage

| Metric | Value |
| --- | --- |
| Strings covered | **2095 / 2095** |
| Coverage | **100.00%** |
| Missing translations | 0 |
| Blocked (cannot translate) | 0 |
| Warnings | 0 |
| Localized files | 9 × `values-zh-rCN/*.xml` |

Modules covered: `manager`, `core/ui`, `compat` (compat stub), `common`, `app-process`, `database`, `server`, `shell`, `starter`, `api`, `core/common`, `core/data`

### Not yet covered

| Item | Status | Notes |
| --- | --- | --- |
| Hardcoded strings | 1 suggestion | One UI string is hardcoded in source and cannot be localized through resources; it needs an upstream code change, so it is out of scope for localization |
| `translatable="false"` entries | Intentionally untranslated | Debug/internal identifiers — excluded by upstream convention |
| Reference arrays (`@string/`) | Intentionally untranslated | They only alias other strings, and inherit their translations |
| Enum-valued arrays (e.g. `none` / `open_app` / `DEFAULT`) | Intentionally untranslated | Machine-read values — translating them would break behavior |
| Brand and technical names | Intentionally kept as-is | E.g. **Shizuku+**, **AMOLED+**, **Material You**, **ADB**, **One UI**, **Hex Installer**, **Magisk**, **Dhizuku** (a trailing `+` must never be dropped) |
| Other locale folders | Untouched | `values-<other locale>/`, `values-night/`, `values-v31/`, etc. are preserved — only Chinese additions are made |
| English README / docs | Not translated | Only the Chinese entry point and the Chinese README are added |

### Terminology and rules

The Chinese translations follow the machine-readable glossary `tools/glossary_zh_rCN.json` and the specification `tools/LOCALIZATION_SPEC_zh-rCN.md`. Key constraints:

- **Translated entry by entry — no batch operations.** Every entry is independently logged (rationale, glossary comparison, self-checks); a change without such a record is rejected by the quality gate before commit.
- **UI resources only.** Only `*/src/main/res/values-zh-rCN/*.xml` is written — Kotlin/Java/Gradle/Manifest/CI files are never touched.
- **Placeholders and escapes preserved.** `%1$s`, `%d`, literal escapes, CDATA and HTML tags are carried over verbatim.
- **Daily upstream sync.** English changes are synced, terminology drift is checked, and feedback/submissions in this repository are reviewed every day.

## ⬇️ Download

Get the latest release from [GitHub Releases](https://github.com/thejaustin/ShizukuPlus/releases) — see the release notes there for what's changed recently.

## ✨ Shizuku+ Core Features

*   **Universal Privilege Provider**: One interface for **Root**, **ADB Shell**, and **Dhizuku (Device Owner)**.
*   **OneUI 8+ Theming Fix**: Lets theming engines like Hex Installer or Substratum keep working on Android 16/17 and OneUI 8+.
*   **Dhizuku Mode**: Share the system Device Owner binder with any app that has Shizuku permissions — set up via ADB, no root needed.
*   **Customizable Gestures**: Swipe left, swipe right, and long-press actions, configurable per app.
*   **In-App Changelogs**: See what's new after an update without leaving the app.
*   **Bulk Management**: Multi-select apps to grant/revoke permissions or hide them in one tap.
*   **Activity Log**: Audit trail of API calls and `su` bridge commands, with app icons and real-time updates.
*   **Root Compatibility Hub**: Dashboard for legacy root apps, with granular module control (Magisk mocking, auto-grant, file interceptor, and more).
*   **Universal SU Automation**: One-tap 'Magic Setup' to point all installed root apps at the Shizuku+ SU Bridge.
*   **Service Doctor**: Diagnoses and fixes service startup issues (Samsung Auto Blocker included).
*   **Integrated Feature Guides**: Every Plus feature has an info icon with a plain-language explanation of what it does.
*   **Quick Settings Tile**: Check and toggle the service status from your notification panel.

## 🚀 Plus API Features

Shizuku+ provides exclusive system interfaces for advanced automation and tools — none of these exist in stock Shizuku:

*   **AICore+ Automation Bridge**: Privileged UI automation (hierarchy dumps, tap/swipe) for AI-driven tools — no root needed. ([added](https://github.com/thejaustin/ShizukuPlus/commit/e9bd1187))
*   **AVF (Virtual Machine) Manager**: Run isolated Linux/Microdroid VMs with GPU acceleration. ([added](https://github.com/thejaustin/ShizukuPlus/commit/c8e962f6))
*   **Privileged Storage Proxy**: Authenticated access to restricted paths for backups and file management. `/data/app/` and external `/Android/data/` work in ADB mode; `/data/data/` requires root (the server must run as UID 0 to cross app-private directory boundaries). ([added](https://github.com/thejaustin/ShizukuPlus/commit/c8e962f6))
*   **Device Spoofing** (*Spoof Device Identity* in Settings): Present a different device identity to bypass device-specific restrictions. ([added](https://github.com/thejaustin/ShizukuPlus/commit/11867f44))
*   **Intelligence Bridge** (*AI Core Plus*): Privileged NPU scheduling and screen context intelligence. ([added](https://github.com/thejaustin/ShizukuPlus/commit/e9bd1187))
*   **Window Manager Plus**: Force free-form resizing, manage the Bubble Bar, and resilient overlays. ([added](https://github.com/thejaustin/ShizukuPlus/commit/e9bd1187))
*   **System Theming Bridge** (*Overlay Manager Plus*): Privileged overlay management for rootless theming (e.g. Hex Installer). ([added](https://github.com/thejaustin/ShizukuPlus/commit/55f6b7c7))
*   **Network & DNS Governor**: Manage Private DNS and firewall routing for rootless ad-blockers. ([added](https://github.com/thejaustin/ShizukuPlus/commit/55f6b7c7))
*   **Deep Process Control** (*Activity Manager Plus*): Lets process managers kill apps and set standby buckets more aggressively. ([added](https://github.com/thejaustin/ShizukuPlus/commit/55f6b7c7))
*   **Continuity Bridge**: Secure state and task handoff between Shizuku+ devices. ([added](https://github.com/thejaustin/ShizukuPlus/commit/20cf14f7))

## 🛠️ Backporting & Optimizations

Shizuku+ makes regular Shizuku apps faster and more compatible without any code changes:

*   **Transparent Shell Interceptor**: Routes common `pm`, `am`, and `settings` commands through faster native APIs.
*   **Local ADB Proxy**: Emulates an ADB server on port 15555, so legacy apps can use Shizuku without Wireless ADB staying on.
*   **SU Bridge**: A Shizuku-backed `su` drop-in for non-rooted apps that support a custom root path. Common root commands are translated into real framework operations where shell UID allows it — `iptables --uid-owner` per-app blocks become live `NetworkPolicy` restrictions, `resetprop` reads/writes real system properties, and `chmod`/`chown` apply for real — falling back to mocked success only when an operation genuinely requires root (e.g. flashing partitions or loading kernel modules).
*   **`plus` CLI Helper**: A privileged command-line utility, available inside `rish`.
*   **Dynamic App Database**: Keeps app descriptions and suggestions in the UI up-to-date from GitHub.

## ⚙️ Modular Control

Everything in Shizuku+ is optional. Use the **Plus Features** category in Settings to toggle:
*   Transparent Shell Interception
*   Individual Plus APIs (AVF, Storage, Intelligence, etc.)
*   Home screen card visibility
*   Activity Logging

## 🔌 Third-Party App Compatibility

Shizuku+ installs under its own package (`af.shizuku.plus.api`) so it can coexist with stock Shizuku. Because most Shizuku-aware apps look specifically for the `moe.shizuku.privileged.api` package, Shizuku+ ships a lightweight **Compat Hub** — a tiny companion app that registers that package name and forwards binder/permission requests to Shizuku+.

**If third-party apps don't detect Shizuku+:**
1. Start the Shizuku+ service (ADB or root).
2. On the home screen, use the **Compat Hub** card to install the companion (it's bundled in the app; installation goes through the running service, so start the service first).
3. Re-open the third-party app — it should now detect Shizuku and receive the service binder.

Alternatively, install the **drop-in** build, which registers as `moe.shizuku.privileged.api` directly (do not install it alongside stock Shizuku).

## ☑️ Requirements

**Minimum: Android 7+ · Fully supported through Android 17 (SDK 37)**
- **Root mode:** Requires a rooted device
- **Wireless Debugging mode:** Android 11+ and all Android TVs
- **PC mode:** All devices
- **Start on boot:** Available only with Wireless Debugging or Root mode

On **Android 16+**, Shizuku+ requests the new Local Network Protection permissions so wireless-debugging discovery and pairing keep working; on **Android 17**, it transparently handles the hidden-API `deviceId` change so authorized apps still appear and permission grants still apply.

## 📱 Developer Guide

See the [Shizuku+-API](https://github.com/thejaustin/ShizukuPlus-API) repository for documentation on the exclusive Plus APIs.

## 🙏 Acknowledgements & Licenses

Shizuku+ is a community-driven enhancement and fork of [thedjchi/Shizuku](https://github.com/thedjchi/Shizuku), which is itself a fork of the original [RikkaApps/Shizuku](https://github.com/RikkaApps/Shizuku). This project is not affiliated with the original RikkaApps team.

Thanks to the following upstream contributors and projects whose work makes Shizuku+ possible:

- **[RikkaApps / Rikka](https://github.com/RikkaApps)** — For the foundational Shizuku project and its elegant API design.
- **[thedjchi](https://github.com/thedjchi)** — For the intermediate fork and quality-of-life improvements, and for carrying the **Android 17 (SDK 37) compatibility** work that Shizuku+'s A17 support is adapted from.
- **[kerneldroid / Nightzuku](https://github.com/kerneldroid/Nightzuku)** — Origin of the Android 17 hidden-API `deviceId` compatibility approach (the `Android17Compat` / `InstalledPackagesCompat` reflection layer) and Local Network Protection handling that this fork's A17 support descends from.
- **[LandonMoran](https://github.com/LandonMoran)** — For porting Nightzuku's Android 17 support into the thedjchi fork and **verifying it end-to-end on a physical Android 17 device** (pairing, service start, and the authorized-apps list), which is the field validation Shizuku+'s port builds on.
- **[Muntashir Akon](https://github.com/MuntashirAkon)** — For the aShell You codebase, which inspired the terminal and shell automation features.
- **[iamr0s](https://github.com/iamr0s)** — For Dhizuku, enabling the unified Device Owner privilege mode, and AndroidAppProcess for standalone Java process execution.
- **[pascua28](https://github.com/pascua28)** — For native Samsung System UID 1000 escalation integration.
- **[kerneldroid](https://github.com/kerneldroid)** — For the Nightzuku fork, which inspired our Android 16/17 (SDK 37) hidden API resilience (handling `deviceId`) and UI modernizations.
- **[ShizukuExt-SystemUID](https://github.com/ShizukuExt)** — For conceptualizing systemic UID 1000 privilege escalation beyond standard limits.

### Upstream Projects

| Project | Author | License | Role |
|---------|--------|---------|------|
| [Shizuku](https://github.com/RikkaApps/Shizuku) | RikkaApps / Rikka | Apache 2.0 | Foundational privileged-process architecture |
| [Shizuku (fork)](https://github.com/thedjchi/Shizuku) | thedjchi | Apache 2.0 | Intermediate fork with QoL improvements; carried the Android 17 compat work Shizuku+ adapted |
| [Nightzuku](https://github.com/kerneldroid/Nightzuku) | kerneldroid | Apache 2.0 | Origin of the Android 17 hidden-API `deviceId` + Local Network Protection compatibility approach |
| [Shizuku (fork)](https://github.com/pascua28/Shizuku) | pascua28 | Apache 2.0 | Samsung UID 1000 system execution exploit |
| [Nightzuku](https://github.com/kerneldroid/Nightzuku) | kerneldroid | Apache 2.0 | Android 16/17 API resilience & UI modernizations |
| [ShizukuExt-SystemUID](https://github.com/ShizukuExt) | ShizukuExt Team | Apache 2.0 | System UID privilege escalation concepts |
| [Dhizuku](https://github.com/iamr0s/Dhizuku) | iamr0s | Apache 2.0 | Device Owner binder sharing (Dhizuku Mode) |
| [AndroidAppProcess](https://github.com/iamr0s/AndroidAppProcess) | iamr0s | LGPL-3.0 | Standalone high-privileged Java process wrapper |

### Open Source Libraries

| Library | Author | License |
|---------|--------|---------|
| [AndroidX Jetpack](https://developer.android.com/jetpack) | Google / AOSP | Apache 2.0 |
| [Material Components](https://github.com/material-components/material-components-android) | Google | Apache 2.0 |
| [Material Symbols](https://fonts.google.com/icons) | Google | Apache 2.0 |
| [Kotlin / Coroutines / Serialization](https://github.com/JetBrains/kotlin) | JetBrains | Apache 2.0 |
| [RikkaX Libraries](https://github.com/RikkaApps) (appcompat, material, insets, html, recyclerview, preference, lifecycle, parcelablelist) | Rikka | Apache 2.0 |
| [Hidden API / Refine](https://github.com/RikkaApps/HiddenApiCompat) | Rikka | Apache 2.0 |
| [Mavericks (MvRx)](https://github.com/airbnb/mavericks) | Airbnb | Apache 2.0 |
| [Lottie](https://github.com/airbnb/lottie-android) | Airbnb | Apache 2.0 |
| [Coil](https://github.com/coil-kt/coil) | Coil Contributors | Apache 2.0 |
| [Koin](https://github.com/InsertKoinIO/koin) | Koin Contributors | Apache 2.0 |
| [Timber](https://github.com/JakeWharton/timber) | Jake Wharton | Apache 2.0 |
| [libsu](https://github.com/topjohnwu/libsu) | topjohnwu | Apache 2.0 |
| [AndroidHiddenApiBypass](https://github.com/LSPosed/AndroidHiddenApiBypass) | LSPosed | Apache 2.0 |
| [libcxx](https://github.com/lsposed/libcxx) | LSPosed / LLVM | Apache 2.0 + LLVM Exception |
| [AppIconLoader](https://github.com/zhanghai/AppIconLoader) | Zhang Hai | Apache 2.0 |
| [BoringSSL (NDK)](https://github.com/vvb2060/ndk-boringssl) | vvb2060 / Google | Apache 2.0 / ISC |
| [Gson](https://github.com/google/gson) | Google | Apache 2.0 |
| [LeakCanary](https://github.com/square/leakcanary) | Square | Apache 2.0 |
| [AboutLibraries](https://github.com/mikepenz/AboutLibraries) | Mike Penz | Apache 2.0 |
| [Bouncy Castle](https://www.bouncycastle.org/) | Legion of Bouncy Castle | MIT |
| [Sentry Android SDK](https://github.com/getsentry/sentry-java) | Sentry | MIT |
| [SQLite (C Recovery API / CLI)](https://sqlite.org/) | D. Richard Hipp / SQLite Consortium | Public Domain |

Full license texts and per-library details: [OPEN_SOURCE_LICENSES.md](OPEN_SOURCE_LICENSES.md) | [NOTICE](NOTICE)

## 📃 License

[Apache 2.0](LICENSE)

### Contributors

Thank you to everyone who has contributed code, translations, and testing to Shizuku+:

**Code Contributors**

| Contributor | Contribution |
|-------------|--------------|
| [thejaustin](https://github.com/thejaustin) | Project founder & primary maintainer — all core Plus features, UI/UX, and infrastructure |
| [thedjchi](https://github.com/thedjchi) | Intermediate fork base; Android 17 (SDK 37) compatibility groundwork |
| [Kevin Doremy](https://github.com/doremylover) | Dead code removal, unused import cleanup, layout & class refactoring |
| [Ryfter](https://github.com/Ryfter) | mDNS timeout improvements, FGS subtype refactoring, notification UX |
| [vvb2060](https://github.com/vvb2060) | AGP build system updates, LTO optimization, license clarifications |
| [Haruue Icymoon](https://github.com/haruue) | Documentation & README improvements |

**Translation Contributors**

| Language | Contributor |
|----------|-------------|
| Brazilian Portuguese | [odorizzioficial](https://github.com/odorizzioficial) |
| French | [Ryfter](https://github.com/Ryfter), [T. Clement](https://github.com/thibaultclement) |
| Vietnamese | [ThePrimalPea](https://github.com/ThePrimalPea) |
| Filipino | [IverCoder](https://github.com/IverCoder) |
| Italian | [Dany-coder778](https://github.com/Dany-coder778) |
| Japanese | [MES-mitutti](https://github.com/MES-mitutti) |

*Plus many more via community translation through Weblate — thank you to all translators!*

### Acknowledgments
- Special thanks to **AkayamiShurui42** for the proactive security research and stability patches (Reference: #239).
- Thank you to **AlexeiCrystal** for identifying MIUI crash bugs and suggesting the Compat Hub workaround for legacy apps (#241, #242).
- Thank you to **ddnexus** and **kai-bash** for highlighting the Device Owner factory reset trap and Google Backup conflicts (#237).
- Thank you to **Kevinco1** for feedback on root compat app detection issues (#243).
- Thank you to **aragortsantiago6-beep** and **Scoop2389** (Pixel 9a) and **ConversionRituals** (Xiaomi) for on-device Android 16/17 testing, crash reports, and logs that drove the SDK 37 hidden-API and Local Network Protection compatibility fixes (#317, #323).
- Thank you to **gmm96** for extensive multi-round logcat debugging across several builds that pinned down the Cached Apps Freezer binder-delivery bug (#371).
- Thank you to **[odorizzioficial](https://github.com/odorizzioficial)** for the complete Brazilian Portuguese translation (#409), and for the detailed report on the Samsung "Sleeping apps" Watchdog freeze (#415).
