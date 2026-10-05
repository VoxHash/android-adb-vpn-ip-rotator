# Installation

Platform-specific installation for Android ADB VPN IP Rotator (VoxHash Technologies).

No API keys or environment variables are required. Configuration uses CLI flags and optional JSON files.

## Python 3.8+

### Linux (Debian/Ubuntu)

```bash
sudo apt-get update
sudo apt-get install python3 python3-pip python3-venv
```

### Linux (Arch)

```bash
sudo pacman -S python python-pip
```

On PEP 668 “externally managed” systems, use a venv (do not use `--break-system-packages` unless you know you need it):

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### macOS

```bash
brew install python3
```

### Windows

Install from [python.org](https://www.python.org/downloads/).

## ADB (Android Debug Bridge)

### Linux (Debian/Ubuntu)

```bash
sudo apt-get install adb
# or
sudo apt-get install android-tools-adb
```

### Linux (Arch)

```bash
sudo pacman -S android-tools
```

### macOS

```bash
brew install android-platform-tools
```

### Windows

1. Download [Android platform-tools](https://developer.android.com/studio/releases/platform-tools)  
2. Extract and add the folder to `PATH`  
3. Or install Android Studio (includes ADB)

### Verify ADB

```bash
adb version
adb devices
```

You should see at least one line with status `device`. Offline wireless entries can be ignored or disconnected with `adb disconnect HOST:PORT`.

### Authorize a physical device

1. Enable Developer options (tap Build number seven times)  
2. Enable USB debugging  
3. Connect USB and accept the RSA fingerprint prompt  
4. Re-run `adb devices`

## Windscribe Android app (current target)

1. Install from [Google Play](https://play.google.com/store/apps/details?id=com.windscribe.vpn) or the vendor site  
2. Log in on the device  
3. Confirm package presence:

```bash
adb shell pm list packages | grep -i windscribe
```

Optional CLI installs from the vendor are also detected when present on the device `PATH`.

## Project install

```bash
git clone https://github.com/VoxHash/android-adb-vpn-ip-rotator.git
cd android-adb-vpn-ip-rotator
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python3 -m py_compile windscribe_ip_changer.py
python3 windscribe_ip_changer.py --help
```

`requirements.txt` currently documents optional extras; the core script uses the Python standard library.

## Verify end-to-end readiness

```bash
adb devices
python3 windscribe_ip_changer.py --list-devices
python3 test_connection.py
```

## Next Steps

- [Quick Start](quick-start.md)
- [Usage Guide](usage.md)
