# Roadmap — Android ADB VPN IP Rotator

Maintained by VoxHash Technologies. Items marked complete ship in v0.2.0+.

## Now (v0.2.x)

- ✅ Full Windscribe Android UI automation (tap/text/swipe)
- ✅ Smart screen-size detection
- ✅ Multi-device simultaneous connections
- ✅ Device list / device select CLI
- Harden `uiautomator` hierarchy parsing for UI layout changes
- Clearer errors when the VPN app is missing or unauthorized
- JSON schema validation for `servers.json` and multi-device configs

## Next (v0.3.x)

- Retry/backoff for flaky ADB and VPN connect races
- Emulator-based CI smoke tests (no physical device required)
- Optional structured logging (`--verbose` / `--json-log`)
- Improve public-IP detection without relying on `curl`/`wget` on-device

## Later

- Additional VPN provider adapters (plugin-style; keep Windscribe as first target)
- Optional desktop wrapper (thin GUI over the CLI)
- Scheduled rotation helpers (systemd timer / cron examples in docs)
- Dockerized ADB host for lab environments

## Non-goals (near term)

- Official affiliation or branding with any VPN vendor
- Shipping VPN credentials or bypassing VPN account requirements
- Root-only device control paths
