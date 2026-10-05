# Getting Started

Complete setup guide for Android ADB VPN IP Rotator.

## Overview

Android ADB VPN IP Rotator is a Python CLI that uses ADB to automate VPN location changes on Android devices, rotating the device’s public IP. The current supported app target is Windscribe (`com.windscribe.vpn`).

## Setup Process

### 1. Install dependencies

See [Installation](installation.md).

### 2. Enable Developer Options

On the Android device:

1. Settings → About phone  
2. Tap **Build number** seven times  
3. Settings → Developer options  
4. Enable **USB debugging**

### 3. Connect the device

**Physical device**

- Connect USB (or use `adb connect HOST:PORT` for wireless debugging)
- Accept the debugging authorization prompt
- Verify: `adb devices` shows `device` (not `unauthorized` / `offline`)

**Emulator**

- Start the emulator; ADB usually detects it automatically
- Verify: `adb devices`

### 4. Install and sign in to Windscribe

Install the Windscribe Android app and complete login on the device.

```bash
adb shell pm list packages | grep -i windscribe
# expect: package:com.windscribe.vpn
```

### 5. Smoke-test

```bash
python3 windscribe_ip_changer.py --list-devices
python3 test_connection.py
```

## Basic Usage

```bash
python3 windscribe_ip_changer.py
python3 windscribe_ip_changer.py --rotate --count 10 --interval 300
```

## Next Steps

- [Usage Guide](usage.md)
- [Examples](examples/example-01.md)
- [Configuration](configuration.md)
