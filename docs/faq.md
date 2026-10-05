# FAQ

## What is Android ADB VPN IP Rotator?

A Python tool from VoxHash Technologies that uses ADB to automate VPN location changes on Android, rotating the device’s public IP. The current app target is Windscribe.

## Is this an official Windscribe product?

No. It is independent and not affiliated with Windscribe Limited. Windscribe is a trademark of its owner.

## Do I need root?

No. USB debugging (ADB) is enough.

## Physical devices and emulators?

Both are supported when ADB reports status `device`.

## Python version?

Python 3.8+ recommended (3.x required).

## Where do I get ADB?

- Linux: `adb` / `android-tools` packages  
- macOS: `brew install android-platform-tools`  
- Windows: Android platform-tools zip  

## Env vars or secrets?

None for the core tool. Use CLI flags and optional JSON configs.

## How do I change IP once?

```bash
python3 windscribe_ip_changer.py
```

## How do I rotate automatically?

```bash
python3 windscribe_ip_changer.py --rotate --count 10 --interval 300
```

## Custom servers?

Yes — `cp servers.json.example servers.json` then `--servers servers.json`.

## See Also

- [Troubleshooting](troubleshooting.md)
- [Usage Guide](usage.md)
- [Support](../SUPPORT.md)
