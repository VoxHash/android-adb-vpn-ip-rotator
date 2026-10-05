# Usage Guide

How to use Android ADB VPN IP Rotator.

## Single IP change

```bash
python3 windscribe_ip_changer.py
```

## Automatic IP rotation

```bash
python3 windscribe_ip_changer.py --rotate --count 10 --interval 300
```

## Target a specific device

```bash
python3 windscribe_ip_changer.py --list-devices
python3 windscribe_ip_changer.py --device emulator-5554
```

## Multi-device

```bash
cp multi_device_config.json.example multi_device_config.json
# edit device_id / location pairs
python3 windscribe_ip_changer.py --multi-device multi_device_config.json
```

## Command-line options

| Option | Description | Default |
|--------|-------------|---------|
| `--adb-path` | Path to ADB executable | Auto-detected |
| `--device` | Device serial/ID | First authorized device |
| `--list-devices` | List devices and exit | — |
| `--multi-device` | Multi-device JSON config | — |
| `--servers` | Server list JSON | Built-in defaults |
| `--wait` | Seconds after connect | 5 |
| `--rotate` | Rotation mode | False |
| `--count` | Rotation count | 5 |
| `--interval` | Seconds between rotations | 300 |

## Custom servers

```bash
cp servers.json.example servers.json
python3 windscribe_ip_changer.py --servers servers.json
```

## Python module usage

```python
from windscribe_ip_changer import WindscribeIPChanger

changer = WindscribeIPChanger(device_id=None)
if changer.check_adb_connection():
    changer.change_ip(wait_time=5)
```

See [API Documentation](api.md).

## Next Steps

- [Examples](examples/example-01.md)
- [Configuration](configuration.md)
- [CLI Reference](cli.md)
