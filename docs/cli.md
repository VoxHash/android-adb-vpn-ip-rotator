# CLI Reference

Complete command-line interface for Android ADB VPN IP Rotator.

## Synopsis

```bash
python3 windscribe_ip_changer.py [OPTIONS]
```

## Options

### `--adb-path PATH`

Custom path to the ADB executable.

```bash
python3 windscribe_ip_changer.py --adb-path /usr/local/bin/adb
```

### `--device DEVICE_ID`

Target a specific device serial (from `adb devices` / `--list-devices`).

```bash
python3 windscribe_ip_changer.py --device emulator-5554
```

### `--list-devices`

Print authorized devices and exit.

```bash
python3 windscribe_ip_changer.py --list-devices
```

### `--multi-device FILE`

JSON array of `{ "device_id", "location" }` objects.

```bash
python3 windscribe_ip_changer.py --multi-device multi_device_config.json
```

### `--servers FILE`

JSON server list. See `servers.json.example`.

```bash
python3 windscribe_ip_changer.py --servers servers.json
```

### `--wait SECONDS`

Seconds to wait after connecting. Default: `5`.

### `--rotate`

Enable automatic IP rotation mode.

### `--count NUMBER`

Number of rotations when `--rotate` is set. Default: `5`.

### `--interval SECONDS`

Seconds between rotations when `--rotate` is set. Default: `300`.

## Examples

```bash
python3 windscribe_ip_changer.py
python3 windscribe_ip_changer.py --rotate --count 20 --interval 1800
python3 windscribe_ip_changer.py \
  --adb-path ~/Android/Sdk/platform-tools/adb \
  --servers my-servers.json \
  --wait 8
```

## Exit Codes

- `0` — success / clean exit (including empty device list for `--list-devices`)
- `1` — fatal error (ADB missing, invalid multi-device config, etc.)

## See Also

- [Usage Guide](usage.md)
- [Configuration](configuration.md)
