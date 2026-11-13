<div align="center">

# 🎮 ReServerTools

**Run Minecraft Java servers on your Android — no root, no PC, no commands.**
**Everything is already set up. Just tap a button.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Android-green.svg)](https://www.android.com/)
[![Kotlin](https://img.shields.io/badge/Kotlin-1.9+-blue.svg)](https://kotlinlang.org/)
[![Status](https://img.shields.io/badge/Status-In%20development-orange.svg)]()

</div>

---

## 📖 What is ReServerTools?

**ReServerTools is Termux where every command is already a button.**

Termux gives you a full Linux terminal on Android, but you have to type everything: `pkg install openjdk-21`, `wget ...`, `java -jar ...`. You need to know Linux, remember commands, and fix errors by hand.

ReServerTools does all of that for you. There's nothing to type. Everything is already set up as buttons:

- **Install Paper 1.21.1** → one button
- **Install Vanilla 1.20.4** → one button
- **Install Fabric 1.21** → one button
- **Start server** → one button
- **Stop server** → one button
- **Backup world** → one button

The user never sees a command line unless they open the optional console.

## 🎯 Philosophy

> **"Termux for Minecraft — every command is a button."**

Under the hood, there is a small Linux environment (Debian via `proot`) running Java and the server. But the user never touches it. All the commands that would normally be typed in Termux are pre-built and exposed as buttons:

| What you'd type in Termux | What you tap in ReServerTools |
|---|---|
| `pkg install openjdk-21` | *(done automatically on first launch)* |
| `wget .../paper-1.21.1.jar` | **Install Paper 1.21.1** |
| `echo "eula=true" > eula.txt` | *(done automatically)* |
| `java -Xmx2G -jar server.jar nogui` | **Start Server** |
| *(Ctrl+C)* | **Stop Server** |
| `zip -r backup.zip world/` | **Backup World** |

No commands. No terminal. Just buttons.

## ✨ Features

- ✅ **Minecraft Java** servers without root
- ✅ **Paper**, **Vanilla** and **Fabric** support (Forge, Purpur coming soon)
- ✅ Download **any version** with one tap — no commands
- ✅ Everything is pre-configured — no terminal needed
- ✅ Optional console for advanced users who want to type commands
- ✅ Real-time log
- 🚧 In development: network tunnel, multi-server, backups

## 📱 Requirements

| Item | Minimum | Recommended |
|---|---|---|
| Android | 8.0 (API 26) | 11+ |
| Architecture | arm64-v8a (aarch64) | arm64-v8a |
| Free RAM | 2 GB | 4 GB+ |
| Storage | 500 MB | 2 GB+ |
| Network | Needed for setup & download | Wi-Fi recommended |

> ⚠️ Older phones or under 2 GB free RAM may experience lag and overheating. Not recommended for heavy modpacks.

## 🚀 Usage

1. Install the APK (via Releases or build from source)
2. Open the app — **everything installs automatically** (~2 min, only once)
3. Pick a **type** (Paper / Vanilla / Fabric) and a **version** — or just tap a pre-made button
4. Tap **"Install"** — the server jar is downloaded
5. Tap **"Start"** — the server boots up
6. Connect in Minecraft:
   - **Same phone**: `localhost:25565`
   - **Same Wi-Fi**: `phone-ip:25565`

That's it. No terminal, no commands, no config files.

## ⚙️ How it works

The first time you open the app, it prepares a small Linux environment inside your phone and installs Java and the required tools — all automatically. This takes a few minutes and only happens once.

After that, everything is done with buttons. Each button runs a pre-written script:

- **Install** → downloads the correct server jar for the chosen version
- **Start** → runs the server inside the prepared Linux environment
- **Stop** → safely shuts it down
- **Console** *(optional)* → for advanced users who want to type commands like `/op` or `/say`

The Linux part is invisible. You never see `apt`, `wget`, or `java -jar` unless you open the console. It's there, but it's not your problem.

## 🧠 Why not just use Termux?

You could. But you would need to:

- Install Termux
- Run `pkg install openjdk-21`
- Find the right server jar URL for your version
- Run `wget`
- Accept the EULA manually
- Type `java -jar server.jar nogui`
- Repeat everything for every server

ReServerTools takes all those commands and turns them into buttons. **It's Termux for people who just want to play Minecraft with their friends.**

## 🛠️ Build from source

**Requirements:** Android Studio (Hedgehog+), JDK 17, Git

```bash
git clone https://github.com/your-user/ReServerTools.git
cd ReServerTools

# Place in app/src/main/assets/:
#   - proot              (aarch64 binary)
#   - bootstrap.tar.xz   (Debian mini rootfs aarch64)

./gradlew assembleDebug
# APK at: app/build/outputs/apk/debug/app-debug.apk
