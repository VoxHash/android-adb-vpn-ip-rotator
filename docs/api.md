# API Documentation

Python API for Android ADB VPN IP Rotator.

The module file remains `windscribe_ip_changer.py` for compatibility with the current Windscribe automation target.

## WindscribeIPChanger

Main class for ADB-driven VPN IP changes.

### `__init__(adb_path=None, device_id=None)`

**Parameters:**

- `adb_path` (str, optional): ADB executable path  
- `device_id` (str, optional): Device serial; auto-selects first authorized device if omitted  

```python
changer = WindscribeIPChanger(device_id="emulator-5554")
```

### `list_devices() -> List[dict]`

Returns `[{"device_id": "...", "status": "device"}, ...]` for authorized devices/emulators.

### `check_adb_connection() -> bool`

True when the selected (or any) device is connected.

### `get_connected_device() -> Optional[str]`

Selected or first available device ID.

### `check_windscribe_installed() -> bool`

True if Windscribe CLI or Android package is present.

### `get_windscribe_package_name() -> Optional[str]`

Android package name when detected (e.g. `com.windscribe.vpn`).

### `get_windscribe_status() -> Optional[str]`

Best-effort connection status string.

### `disconnect_windscribe() -> bool`

Disconnect current VPN session (system + UI fallbacks).

### `connect_windscribe(location: str) -> bool`

Connect to a location code such as `"us-east"`.

### `get_current_ip() -> Optional[str]`

Best-effort public/local IP discovery from the device.

### `change_ip(servers=None, wait_time=5) -> bool`

Pick a server and rotate IP.

### `rotate_ips(count=5, interval=300, servers=None)`

Repeated `change_ip` with sleeps between iterations.

## Module helper

### `manage_multiple_devices(adb_path, device_configs, servers=None) -> dict`

Connect several devices to configured locations. Each config item needs `device_id` and `location`.

## Example

```python
from windscribe_ip_changer import WindscribeIPChanger

changer = WindscribeIPChanger()
if changer.check_adb_connection() and changer.check_windscribe_installed():
    if changer.change_ip(wait_time=5):
        print(changer.get_current_ip())
```

## See Also

- [Usage Guide](usage.md)
- [Examples](examples/example-01.md)
