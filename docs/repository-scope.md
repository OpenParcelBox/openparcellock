# Repository Scope

Status: planning note.

OpenParcelLock is the lock-focused part of the OpenParcelBox ecosystem.

This repository should contain reusable lock-module and lock-interface knowledge. It should not become the full OpenParcelBox device, bridge or cloud project.

## Belongs Here

- lock profiles
- lock electrical interface requirements
- lock-driver measurement protocols
- solenoid, strike, cabinet-latch and motor-lock notes
- fail-safe / fail-secure behavior descriptions
- door state vs. lock state separation
- tamper and sabotage signal expectations
- emergency access assumptions
- connector and wiring expectations for lock paths
- prototype-only vs. reference lock-driver patterns

## Belongs In `openparcelbox`

- M1 DHL retrofit roadmap
- full device firmware architecture
- user, household and carrier access-control model
- audit-event model
- MQTT, API, Matter, Home Assistant and bridge integration
- cloud and self-hosting concepts
- GitHub Project planning
- standards and governance baseline

## Shared Boundary

The OpenParcelBox host controller decides whether to unlock.

OpenParcelLock describes how a lock path behaves once an authorized unlock is requested.

External integrations must not directly drive the lock output. They may only request an action from the OpenParcelBox controller, which applies local policy and logging before actuation.

## First Practical Source

The first real use case is the DHL parcel box retrofit. Mechanical lessons from that work should be copied here only when they become reusable beyond that one model.
