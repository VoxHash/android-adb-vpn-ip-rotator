# Architecture

How Android ADB VPN IP Rotator works.

## Overview

The host runs a Python CLI that shells out to ADB. On the device, the tool drives the Windscribe Android UI (and optional CLI) to change VPN locations, which changes the device’s egress IP.

## Components

1. **ADB connection management** — locate `adb`, select device, validate state  
2. **VPN app detection** — package scan / CLI presence  
3. **UI automation** — `input tap`, `input text`, `input swipe`, optional `uiautomator` dump  
4. **IP verification** — read network state / public IP helpers  
5. **Multi-device orchestration** — sequential per-device connect with independent locations  

## Flow

```
CLI ──► ADB ──► Android device ──► Windscribe app UI ──► VPN server ──► new egress IP
```

## Process

1. Resolve ADB path and device ID  
2. Confirm VPN app installed  
3. Capture current IP / status  
4. Disconnect if needed  
5. Open app, search/select location, connect  
6. Wait (`--wait`) and verify  

## Error handling

- Missing ADB or unauthorized/offline devices  
- VPN app not installed (clear message; exit path returns `False`)  
- UI layout drift (coordinate fallbacks; hierarchy helpers)  
- Invalid JSON for servers / multi-device configs  

## See Also

- [Usage Guide](usage.md)
- [API Documentation](api.md)
