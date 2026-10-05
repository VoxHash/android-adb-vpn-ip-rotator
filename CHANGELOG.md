# Changelog — Android ADB VPN IP Rotator

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [0.2.0] - 2026-10-05

### Added
- Multi-device support with `--multi-device` JSON config (`manage_multiple_devices()`)
- Device targeting via `--device` and inventory via `--list-devices`
- Full in-app UI automation (tap, text, swipe, screen-size detection)
- Location name mapping for common server codes
- Connection verification after automation
- Example configs: `servers.json.example`, `multi_device_config.json.example`
- Standardized documentation kit under `docs/` and GitHub issue/PR templates

### Changed
- **Renamed project** from “Windscribe IP Changer for Android” to **Android ADB VPN IP Rotator** (`android-adb-vpn-ip-rotator`) to avoid third-party trademark branding; Windscribe remains the supported automation target (non-affiliated)
- All ADB commands support `-s DEVICE_ID` when a device is specified
- Device auto-selection uses the first authorized `device`/`emulator` entry
- Documentation and GitHub metadata updated for the new repository name and SEO topics
- Roadmap aligned with completed UI automation and multi-device work

### Fixed
- Fixed `list_devices()` indentation so every ADB device line is evaluated (previously only the last offline line was checked, hiding real devices)
- Fixed broken shell piping in `check_windscribe_installed()` (prior commit `fe179c0`)
- Fixed incorrect device ID extraction in `get_connected_device()` (prior commit `fe179c0`)
- Fixed connection flow that opened the app without completing connect (prior commit `fe179c0`)

### Removed
- Stray markdown outside the documentation kit (`DEVELOPMENT_GOALS.md`, `GITHUB_TOPICS.md`, `INSTALL_ADB.md`, `TEST_RESULTS.md`); useful content merged into kit docs

### Security
- Sensitive test identifiers sanitized in historical notes; do not commit device serials, account data, or real public IPs

## [0.1.0] - 2026-03-12

### Added
- Initial release
- ADB connection management
- VPN IP rotation via Windscribe on Android
- Support for Android devices and emulators
- Automatic IP rotation mode
- Configurable server locations
- Current IP and status checking
- Command-line interface with argparse
- Example usage and connection test utilities

[0.2.0]: https://github.com/VoxHash/android-adb-vpn-ip-rotator/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/VoxHash/android-adb-vpn-ip-rotator/releases/tag/v0.1.0
