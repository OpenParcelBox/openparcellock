# Standalone Management Requirement

OpenParcelLock is a lock module and interface profile. It should not require a cloud service, a vendor app, Home Assistant, MQTT or an external bridge for basic local operation.

For OpenParcelBox-compatible standalone devices that use OpenParcelLock profiles, the host device should provide a local management path.

## M1 Requirement

Every standalone OpenParcelBox device using an OpenParcelLock-compatible lock path should provide local setup and management without external infrastructure.

For the first DHL parcel box retrofit beta, this means:

- local Wi-Fi access point setup mode
- embedded web server
- browser-based configuration interface
- local household, user, PIN and NFC management
- local network configuration
- local event/log view
- firmware and update status
- local admin or recovery path

The web interface does not need to be visually polished in M1, but it must be usable enough to configure and operate the device without cloud, bridge, Home Assistant, MQTT or a vendor app.

## Lock Boundary

OpenParcelLock itself should remain focused on lock behavior and interfaces:

- unlock command
- lock state
- door state
- tamper/sabotage state
- fail-safe or fail-secure assumptions
- emergency access assumptions

User management, rolling codes, audit logs, web UI and OTA are responsibilities of the OpenParcelBox device firmware or host controller, not of a passive lock module.

## Firmware Implication

Any firmware basis considered for an OpenParcelBox standalone controller must be evaluated against this requirement.

This means the firmware architecture must support:

- AP-mode setup
- embedded local web management
- durable local configuration storage
- local access-control data
- local logs or event buffers
- secure update or recovery path

This requirement does not force a specific implementation framework. ESP-IDF, Arduino Core, ESPHome custom components or hybrid approaches may still be evaluated, but the chosen path must satisfy standalone management without making Home Assistant or a cloud service mandatory.
