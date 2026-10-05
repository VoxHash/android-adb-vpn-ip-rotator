# Example 02: Automatic IP Rotation

Rotate IPs on a schedule from the CLI.

## Scenario

Six rotations, ten minutes apart (about one hour).

## Steps

```bash
adb devices
python3 windscribe_ip_changer.py --rotate --count 6 --interval 600
```

With an explicit device and server file:

```bash
cp servers.json.example servers.json
python3 windscribe_ip_changer.py \
  --device YOUR_DEVICE_ID \
  --servers servers.json \
  --rotate \
  --count 6 \
  --interval 600
```

## Python API

```python
from windscribe_ip_changer import WindscribeIPChanger

changer = WindscribeIPChanger()
if changer.check_adb_connection():
    changer.rotate_ips(count=6, interval=600)
```

## Multi-device variant

```bash
cp multi_device_config.json.example multi_device_config.json
# set real device IDs and locations
python3 windscribe_ip_changer.py --multi-device multi_device_config.json
```

## Next Steps

- [Example 01: Basic IP Change](example-01.md)
- [Configuration](../configuration.md)
