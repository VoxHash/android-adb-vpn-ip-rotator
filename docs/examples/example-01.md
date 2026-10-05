# Example 01: Basic IP Change

Change the device IP once via ADB automation.

## Scenario

Rotate to a random configured VPN location on a single authorized Android device.

## Steps

```bash
adb devices
python3 windscribe_ip_changer.py --list-devices
python3 windscribe_ip_changer.py --device YOUR_DEVICE_ID
```

## Expected behavior

1. Script prints the connected device ID  
2. Detects package `com.windscribe.vpn` (or variant)  
3. Disconnects if already connected  
4. Automates location selection and connect  
5. Prints a new IP when detection succeeds  

If the VPN app is missing, you will see:

```text
Error: Windscribe not found on device
```

Install the app, sign in, and retry.

## Python API

```python
from windscribe_ip_changer import WindscribeIPChanger

changer = WindscribeIPChanger()
if changer.check_adb_connection():
    ok = changer.change_ip(wait_time=5)
    print("ok" if ok else "failed")
```

## Next Steps

- [Example 02: Automatic Rotation](example-02.md)
- [Usage Guide](../usage.md)
