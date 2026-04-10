<img src="https://raw.githubusercontent.com/droserasprout/io.drsr.hotspotadb/main/screenshot.png" align="right" width="300">

# Hotspot Wireless Debugging

Xposed module that allows Wireless Debugging (ADB over Wi-Fi) to work over Wi-Fi Hotspot on Android 15.

Android 11+ only enables Wireless Debugging when the device is connected to Wi-Fi as a client. This module hooks the Settings app and system framework to bypass that restriction, so hotspot guests can connect via ADB.

## Requirements

- Android 15 (older versions not tested)
- LSPosed or compatible Xposed framework

## Installation

1. Install the APK
2. Enable the module in LSPosed for both scopes:
   - `com.android.settings`
   - `android` (System Framework)
3. Reboot

## Usage

1. Enable Wi-Fi Hotspot
2. Use the Wireless Debugging toggle on the hotspot settings screen, or go to Developer Options > Wireless Debugging
3. Pair your client device: `adb pair <ip>:<pairing_port> <pairing_code>`
4. Connect: `adb connect <ip>:<port>`

On first use, Android prompts to trust a network matching your hotspot name. Renaming the hotspot will reset this trust. The MAC address is hardcoded because Android randomizes the hotspot MAC on each enable, which would reset trust every time.

## Other solutions

[Magisk-WiFiADB](https://github.com/mrh929/magisk-wifiadb) — Magisk module, enables legacy `adb tcpip` on boot. Simpler (just Magisk, any Android), but unencrypted and not hotspot-aware. This module hooks native Wireless Debugging (TLS, pairing) with Settings UI, but needs LSPosed and Android 15.

## License

[GPL-3.0](https://github.com/droserasprout/io.drsr.hotspotadb/blob/main/LICENSE)
