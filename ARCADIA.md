# VIIPER for Arcadia

This fork of [VIIPER](https://github.com/Alia5/VIIPER) (GPL-3.0) is what [Arcadia](https://github.com/jc-sw-git/Arcadia)
ships as `viiper.exe`, for its virtual Xbox 360 pad and its copy of the Steam Controller.

Changes against upstream (meant to go upstream):

- Device type `hidproxy` (`device/hidproxy`, [docs](docs/devices/hidproxy.md)): a copy of a real HID device whose
  descriptors and reports come from the client.
- `usb.NoInRepeatDevice`: a device can ask the server not to repeat its last input report every `bInterval`.
- Auto-attach on Windows connects usbip-win2 to `127.0.0.1`, not `localhost`: Arcadia binds the server to IPv4 loopback
  only, and `localhost` could reach another process listening on `[::1]` with the same port number.

The branch `arcadia` holds these changes; the workflow "Arcadia build" tests and builds `viiper.exe`, and "Run
workflow" with "publish" makes the release `arcadia-<commit>` that Arcadia pins by its SHA-256.
