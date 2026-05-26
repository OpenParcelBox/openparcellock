# Lock Driver Measurement Protocol

Status: planning draft.

This document defines what must be measured before an OpenParcelLock-compatible lock output is treated as reliable.

It is not a schematic, PCB design, compliance statement or production safety approval.

## Scope

This protocol applies to low-voltage lock paths such as:

- 12 V solenoid locks
- electric strikes
- cabinet locks
- motor latches
- reused or gutted retrofit lock mechanisms
- relay-driven or MOSFET-driven lock outputs

Prototype designs must not include mains voltage on the board.

## Core Requirement

A lock output must not be selected only because it clicks once on the bench.

The lock path must be measured under realistic cable length, supply and repeated-operation conditions.

## Required Measurements

Measure and record:

- lock cold resistance
- lock warm resistance where relevant
- inrush or pulse current
- minimum reliable unlock pulse duration
- voltage drop on the 12 V branch during actuation
- ESP/controller rail stability during actuation
- driver temperature after repeated attempts
- lock temperature after repeated attempts
- behavior with intended cable length and connector type
- behavior during controller boot
- behavior during controller reset
- behavior if firmware crashes while the output is active

## Driver Requirements

Evaluate whether the chosen driver path provides:

- real 3.3 V-compatible logic-level switching where driven by an ESP-class controller
- flyback or transient protection for inductive loads
- branch fuse or overcurrent protection on the lock output
- defined off-state during boot and reset
- gate/base pulldown or equivalent safe-state handling
- configurable pulse duration in firmware
- maximum-on-time protection
- no continuous solenoid energizing unless the part is explicitly rated and thermally validated

Generic marketplace MOSFET and relay modules are prototype candidates only until verified.

Avoid treating IRF520-style modules as automatically suitable for 3.3 V GPIO drive.

## Firmware Expectations

The host controller should provide:

- configurable pulse duration
- hard maximum activation time
- boot-safe initialization
- no unlock pulse during reboot/reset
- audit event for every unlock request
- audit event for driver error or unknown lock state where supported
- optional future driver fault/status input

## Lock State vs. Door State

Door state and lock state are separate.

Examples:

- the lock may be commanded open while the door remains closed
- the door may remain open after the lock pulse ends
- a lock may report locked while the door is physically ajar
- a door reed contact does not prove the lock is secured

Profiles should describe which signals exist and which assumptions are only inferred.

## Backplane Implications

A later OpenParcelBox Core/backplane should consider:

- dedicated protected 12 V lock output
- branch fuse or electronic overcurrent protection
- transient/flyback protection
- optional current measurement
- optional fault feedback
- connector and cable-rating expectations
- separation from the controller regulator path
- safe default state during firmware update and reset

## Relationship To OpenParcelBox M1

The first DHL parcel box retrofit can use this protocol to compare lock candidates, but the results should be documented separately in the main OpenParcelBox M1 roadmap or issue tracker.

Reusable findings should be copied back into this repository as lock profiles.
