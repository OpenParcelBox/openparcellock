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

## Planned Lock Profiles

- solenoid lock
- motor lock
- cabinet latch
- relay-controlled lock
- lock with end-position feedback
- lock with door/reed contact
- lock with sabotage/tamper contact
- retrofit profile for existing parcel boxes

## Important Safety Notes

- A lock must not rely on blind motor timing as the only source of truth where a safer feedback option is possible.
- Door state and lock state should be treated as separate signals.
- Fail-safe and fail-secure behavior must be documented per lock profile.
- Prototype designs must not include mains voltage on the board.
- Mechanical emergency access must be considered early.

## Relationship to OpenParcelBox

OpenParcelLock is a reference module and profile family for the OpenParcelBox ecosystem. It should not become a mandatory proprietary dependency.

OpenParcelBox should be able to support:

- OpenParcelLock modules
- third-party locks
- documented adapter profiles
- retrofit lock setups

Main project:

https://github.com/OpenParcelBox/openparcelbox
