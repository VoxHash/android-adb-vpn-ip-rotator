# Troubleshooting

Common issues for Android ADB VPN IP Rotator.

## No devices listed by the script

**Symptom:** `adb devices` shows a `device`, but `--list-devices` printed nothing (fixed in v0.2.0).

**Still empty?**

1. Confirm status is `device`, not `offline` / `unauthorized`  
2. `adb kill-server && adb start-server`  
3. Disconnect stale wireless targets: `adb disconnect`  
4. Re-plug USB and re-accept the RSA prompt  

## ADB: no devices/emulators found

1. Install platform-tools / `android-tools`  
2. Enable USB debugging  
3. Accept the authorization dialog  
4. For wireless debugging, use a current `adb connect` pair  

## Windscribe not found on device

```bash
adb shell pm list packages | grep -i windscribe
```

Install from Play (`com.windscribe.vpn`), open the app once, and sign in.

## Many offline entries in `adb devices`

Harmless for listing if at least one `device` remains. Clear them with:

```bash
adb disconnect
```

## Connection timeouts / UI miss

1. Increase `--wait` (e.g. `10`)  
2. Unlock the device screen  
3. Ensure the VPN app UI language/layout matches expected English labels  
4. Retry after manually opening the app once  

## IP detection fails

Some devices lack `curl`/`wget` in the shell. The script uses multiple fallbacks; if all fail, verify VPN status in the app UI and check host-side connectivity through the device network.

## Externally managed Python environment

On Arch and similar PEP 668 systems:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Still stuck?

- [FAQ](faq.md)
- GitHub issues on [android-adb-vpn-ip-rotator](https://github.com/VoxHash/android-adb-vpn-ip-rotator)
- contact@voxhash.dev
