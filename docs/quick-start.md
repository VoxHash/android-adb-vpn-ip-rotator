# Quick Start

Get Android ADB VPN IP Rotator running in about five minutes.

## Prerequisites

1. Python 3.8+  
2. ADB installed and on `PATH`  
3. Android device or emulator connected and authorized  
4. Windscribe Android app installed and logged in  

## Steps

```bash
git clone https://github.com/VoxHash/android-adb-vpn-ip-rotator.git
cd android-adb-vpn-ip-rotator

python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt

adb devices
python3 windscribe_ip_changer.py --list-devices
python3 windscribe_ip_changer.py
```

The script selects a server location, drives the app UI over ADB, and reports the new IP when detection succeeds.

More detail: [Installation](installation.md) and [Usage](usage.md).
