# Android ADB VPN IP Rotator

[![License](https://img.shields.io/github/license/VoxHash/android-adb-vpn-ip-rotator)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.8+-blue)](https://www.python.org/)
[![Release](https://img.shields.io/github/v/release/VoxHash/android-adb-vpn-ip-rotator)](https://github.com/VoxHash/android-adb-vpn-ip-rotator/releases)

> Rotate public IPs on Android devices and emulators via ADB by automating a compatible VPN app (currently Windscribe). Built by VoxHash Technologies.

**Not affiliated with Windscribe Limited.** Windscribe is a trademark of its respective owner. This project is an independent ADB automation tool.

## Features

- Connects to Android devices/emulators via ADB
- Fully automated UI automation (taps/text input; no manual GUI steps)
- Rotates IP by connecting to different VPN server locations
- Supports physical devices and Android emulators
- Multi-device support with independent locations per device
- Configurable server list (`servers.json`)
- Automatic rotation mode (`--rotate`)
- Current IP and connection status checks

## Table of Contents

- [Quick Start](#quick-start)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Examples](#examples)
- [Architecture](#architecture)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)

## Quick Start

```bash
# 1) Clone repository
git clone https://github.com/VoxHash/android-adb-vpn-ip-rotator.git
cd android-adb-vpn-ip-rotator

# 2) Optional: isolated Python env (recommended on Arch/PEP 668 systems)
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# 3) Verify ADB and a connected device
adb devices

# 4) Install and log into the Windscribe Android app on the device, then run
python3 windscribe_ip_changer.py --list-devices
python3 windscribe_ip_changer.py --device YOUR_DEVICE_ID
```

## Installation

See [docs/installation.md](docs/installation.md) for platform-specific steps.

### Prerequisites

| Dependency | Required | Notes |
|------------|----------|-------|
| Python 3.8+ | Yes | Standard library only; optional packages in `requirements.txt` |
| ADB | Yes | `android-tools` / platform-tools in PATH |
| Android device or emulator | Yes | USB debugging enabled and authorized |
| Windscribe Android app | Yes (current target) | Package `com.windscribe.vpn`; logged-in account |
| Env vars / API secrets | No | Configuration is CLI + JSON files |

## Usage

### Single IP change

```bash
python3 windscribe_ip_changer.py
```

### Automatic IP rotation

```bash
python3 windscribe_ip_changer.py --rotate --count 10 --interval 300
```

### Custom server list

```bash
cp servers.json.example servers.json
python3 windscribe_ip_changer.py --servers servers.json
```

### Device selection

```bash
python3 windscribe_ip_changer.py --list-devices
python3 windscribe_ip_changer.py --device emulator-5554
```

### Multi-device

```bash
cp multi_device_config.json.example multi_device_config.json
python3 windscribe_ip_changer.py --multi-device multi_device_config.json
```

### All options

```bash
python3 windscribe_ip_changer.py \
  --adb-path /custom/path/to/adb \
  --device emulator-5554 \
  --servers servers.json \
  --rotate \
  --count 20 \
  --interval 600 \
  --wait 8
```

## Configuration

| Option | Description | Default |
|--------|-------------|---------|
| `--adb-path` | Path to ADB executable | Auto-detected |
| `--device` | Specific device ID | First authorized device |
| `--list-devices` | List connected devices and exit | — |
| `--multi-device` | JSON multi-device config path | — |
| `--servers` | JSON server list path | Built-in defaults |
| `--wait` | Seconds to wait after connecting | 5 |
| `--rotate` | Enable automatic IP rotation | False |
| `--count` | Number of rotations | 5 |
| `--interval` | Seconds between rotations | 300 |

Full reference: [docs/configuration.md](docs/configuration.md)

## Examples

- [Basic IP change](docs/examples/example-01.md)
- [Automatic rotation](docs/examples/example-02.md)

## Architecture

1. Connect to the device via ADB  
2. Detect the Windscribe app/CLI  
3. Read current IP and VPN status  
4. Disconnect if needed (UI automation + system VPN helpers)  
5. Navigate the app UI (tap/text) to select a location and connect  
6. Verify the new public IP  

Details: [docs/architecture.md](docs/architecture.md)

## Roadmap

See [ROADMAP.md](ROADMAP.md). Changes are tracked in [CHANGELOG.md](CHANGELOG.md).

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) and use the PR template.

## Security

Report vulnerabilities via [SECURITY.md](SECURITY.md).

## License

MIT — see [LICENSE](LICENSE). Copyright (c) 2026 VoxHash Technologies.

## Support

See [SUPPORT.md](SUPPORT.md) or email contact@voxhash.dev.
