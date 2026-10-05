# Contributing to Android ADB VPN IP Rotator

Thanks for helping improve Android ADB VPN IP Rotator (VoxHash Technologies).

## Code of Conduct

Please read and follow our [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

## Development Setup

```bash
git clone https://github.com/VoxHash/android-adb-vpn-ip-rotator.git
cd android-adb-vpn-ip-rotator

python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

python3 --version
adb version
python3 windscribe_ip_changer.py --list-devices
python3 test_connection.py
```

## Project Structure

- `windscribe_ip_changer.py` — main CLI/library (Windscribe automation target)
- `test_connection.py` — connection smoke test
- `test_with_device.py` — interactive device tests
- `example_usage.py` — usage examples
- `servers.json.example` / `multi_device_config.json.example` — config templates
- `docs/` — documentation kit

## Branching & Commit Style

- Branches: `feature/...`, `fix/...`, `docs/...`, `chore/...`
- Conventional Commits: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`

## Pull Requests

- Link related issues
- Update docs and `CHANGELOG.md` when behavior changes
- Keep diffs focused
- Follow the PR template

## Testing

1. `python3 -m py_compile windscribe_ip_changer.py`
2. `python3 windscribe_ip_changer.py --list-devices`
3. With a device that has the Windscribe app installed: `python3 test_connection.py`

## Release Process

- Semantic Versioning (MAJOR.MINOR.PATCH)
- Update [CHANGELOG.md](CHANGELOG.md)
- Tag releases (`vX.Y.Z`) and publish a GitHub Release

## Contact

contact@voxhash.dev
