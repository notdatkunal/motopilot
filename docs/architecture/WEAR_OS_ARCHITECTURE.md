# Wear OS Companion Architecture

**Status:** Proposed; Wear OS is the first smartwatch target. No implementation is implied.

## Role

The watch is a lightweight companion endpoint for glanceable cues, haptics and quick actions. The phone remains the normal primary compute and navigation device.

## Initial capabilities

- Next-turn instruction and distance.
- Haptic navigation cues.
- Ride recording start/stop.
- Ride duration and selected telemetry.
- Emergency countdown notification and cancellation action.
- Quick voice activation where supported.
- Phone/watch connection and feature availability status.

Do not promise full offline map rendering, independent routing or continuous crash monitoring on the watch in the first release.

## Communication

Use Wear OS Data Layer APIs for phone/watch synchronization where appropriate. Direct BLE communication with optional MotoPilot hardware may be evaluated later, but is not required for the first watch release.

Define compact, versioned messages for navigation cues, ride state, telemetry summary, emergency alert state, acknowledgement/cancellation and connection status.

The phone must remain functional when the watch is disconnected. The watch must indicate stale data and loss of phone connectivity.

## Suggested technology

Kotlin, Jetpack Compose for Wear OS, Wear OS Data Layer APIs, haptic APIs and Health Services only for supported, explicitly authorized measurements.

## Emergency interaction

The watch may mirror a countdown and provide acknowledgement/cancellation. It is not the authoritative detector in the initial design. Handle delayed/duplicate messages and watch disconnection safely.

## Privacy and validation

Synchronize only the minimum data needed. Test watch models, battery use, disconnected-phone behaviour, delayed messages, notification permissions and haptic availability. Do not assume identical sensors across Wear OS devices.
