# Configuration

Configuration for Android ADB VPN IP Rotator.

## Environment variables

None required. There are no API keys or cloud secrets for the core workflow.

Optional future support may add env vars; today everything is CLI + JSON files.

## Server list

```bash
cp servers.json.example servers.json
```

Example shape:

```json
[
  { "name": "US East", "location": "us-east" },
  { "name": "EU West", "location": "eu-west" }
]
```

```bash
python3 windscribe_ip_changer.py --servers servers.json
```

`servers.json` is gitignored; keep the `.example` committed.

## Multi-device config

```bash
cp multi_device_config.json.example multi_device_config.json
```

```json
[
  { "device_id": "emulator-5554", "location": "us-east" },
  { "device_id": "emulator-5556", "location": "eu-west" }
]
```

## Common location codes

- `us-east`, `us-west`, `us-central`
- `eu-central`, `eu-west`, `eu-east`
- `uk`, `uk-london`, `ca`, `jp`, `sg`, `au`, and others mapped in `LOCATION_NAME_MAP`

## ADB path

```bash
python3 windscribe_ip_changer.py --adb-path /usr/bin/adb
```

Typical locations:

- Linux: `/usr/bin/adb`
- macOS: `/usr/local/bin/adb` or `~/Android/Sdk/platform-tools/adb`
- Windows: `%LOCALAPPDATA%\Android\Sdk\platform-tools\adb.exe`

## See Also

- [Usage Guide](usage.md)
- [Examples](examples/example-01.md)
