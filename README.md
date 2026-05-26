<p align="center">
  <a href="https://openparcelbox.org">
    <img src="https://openparcelbox.org/assets/openparcelbox-readme-banner.png" alt="OpenParcelBox" width="900">
  </a>
</p>

# OpenParcelLock

OpenParcelLock is an open lock module and interface profile for parcel boxes, cabinets and retrofit delivery lockers.

This repository is in the early planning and specification phase. It does not yet contain production-ready hardware, firmware, CAD files or safety certification.

## Purpose

OpenParcelLock is intended as the lock-focused building block of the OpenParcelBox ecosystem.

It should help with two common scenarios:

- replacing unreliable or discontinued proprietary parcel-box electronics
- adding a documented lock module to existing boxes, cabinets or new builds

## Design Goals

- open electrical interface
- documented lock states
- clear separation between unlock command, door state and lock state
- support for different lock types
- support for local-first OpenParcelBox devices
- usable with self-hosted or standalone setups
- optional integration with external controllers
- retrofit-friendly mechanical concepts
- no mandatory cloud, vendor app, Home Assistant, MQTT or bridge for basic local operation when used in a standalone OpenParcelBox device

## Planned Lock Profiles

- solenoid lock
- motor lock
- cabinet latch
- relay-controlled lock
- lock with end-position feedback
- lock with door/reed contact
- lock with sabotage/tamper contact
- retrofit profile for existing parcel boxes

## Current Focus

OpenParcelLock should capture reusable lock knowledge that is not specific to one parcel-box model.

The first OpenParcelBox milestone is a DHL parcel box retrofit, but the lock lessons should be documented here when they can apply to other boxes, cabinets or retrofit mechanisms.

Current reusable topics:

- 12 V pulse-driven lock outputs
- lock-driver measurement protocol
- fail-safe vs. fail-secure behavior
- door state vs. lock state separation
- tamper/sabotage state
- emergency access assumptions
- prototype-only vs. reference lock-driver patterns

## Important Safety Notes

- A lock must not rely on blind motor timing as the only source of truth where a safer feedback option is possible.
- Door state and lock state should be treated as separate signals.
- Fail-safe and fail-secure behavior must be documented per lock profile.
- Prototype designs must not include mains voltage on the board.
- Mechanical emergency access must be considered early.
- Generic MOSFET or relay modules are not automatically safe for a lock output; current, transients, boot state and thermal behavior must be measured.

## Standalone Management

OpenParcelLock modules are only one part of a local-first device. A standalone OpenParcelBox controller using an OpenParcelLock-compatible lock path should provide local AP-mode setup and an embedded web management interface.

See:

- [Standalone management requirement](docs/standalone-management.md)
- [Lock driver measurement protocol](docs/lock-driver-measurement.md)
- [Repository scope](docs/repository-scope.md)

## Relationship to OpenParcelBox

OpenParcelLock is a reference module and profile family for the OpenParcelBox ecosystem. It should not become a mandatory proprietary dependency.

OpenParcelBox should be able to support:

- OpenParcelLock modules
- third-party locks
- documented adapter profiles
- retrofit lock setups

Main project:

https://github.com/OpenParcelBox/specs
