# Hardware Abstraction and Optional Device Integration

**Status:** Proposed target design.

## Principle

MotoPilot must be useful without custom hardware. Phone-native sensors and services provide baseline implementations. External hardware integrates through public interfaces rather than app-specific driver code.

## Capability providers

| Capability | Baseline provider | Optional provider |
|---|---|---|
| Motion | Android accelerometer/gyroscope | External IMU |
| Location | Phone GNSS/location APIs | External GNSS |
| Input | Touch, voice and phone controls | Handlebar controller |
| Audio | Phone/headset audio | Dedicated accessory |
| Vehicle data | Not assumed available | Compatible adapter/sensor |
| TPMS | Not assumed available | Supported BLE TPMS |

Capabilities may be absent, permission-restricted, stale or degraded. Clients must query availability.

## Provider contract

Expose capability identifier/version, availability and permission state, data timestamp and source, accuracy/quality, lifecycle, errors and consent requirements.

## Reference hardware

ESP32-S3 is the initial reference-platform candidate, not a required component. Firmware should separate hardware abstraction, drivers, services, transports and security. Other MCU families may be considered after the first reference implementation is stable.

## Electrical and mechanical safety

Motorcycle power is a harsh environment. A reference device needs transient suppression, reverse-polarity protection, regulated supply, brownout handling, thermal design, vibration-resistant connectors and environmental protection. Never connect an unprotected development board directly to motorcycle power.

Vehicle bus access must be read-only by default and must not issue commands to safety-critical systems.

## Open hardware deliverables

Publish schematics, editable PCB sources, BOM with alternatives, enclosure CAD, assembly instructions, flashing guide, test procedures and revision history.

## MDP integration

Hardware exposes capabilities through the MotoPilot Device Protocol. Transport details must not leak into domain APIs. Third-party devices may implement the protocol without using MotoPilot firmware.
