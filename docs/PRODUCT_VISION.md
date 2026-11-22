# MotoPilot Product Vision

**Status:** Approved product direction; implementation is not implied.

MotoPilot is an open-source, software-first motorcycle companion platform for Android and Wear OS. Riders should be able to use meaningful core features with devices they already own. Optional open hardware extends sensing, controls and connectivity; it is not a prerequisite.

## Principles
1. Software first; hardware optional.
2. Android is the primary platform; Wear OS is the first companion.
3. Local-first and offline-first operation for core ride features.
4. No mandatory account, cloud service, advertising, tracking SDK or automatic telemetry upload.
5. Open protocols and SDKs enable independent clients and compatible hardware.
6. Safety features are conservative and never presented as guarantees.
7. Prefer voice, haptics and tactile controls over screen interaction while riding.
8. Licensing decisions require a separate compatibility and legal review.

## Product surfaces
- Android app: primary cockpit, navigation, ride recording, voice, emergency detection and mini-app host.
- Optional Android launcher: home-screen integration, never required.
- Dedicated Android display: responsive cockpit profile using shared Android logic.
- Wear OS app: glanceable navigation cues, haptics, quick controls and emergency alert companion.
- Optional hardware: reference device and third-party modules.
- Developer ecosystem: SDKs, protocol specification, mini-app APIs and examples.

## Operating configurations

| Configuration | Intended capabilities |
|---|---|
| Android phone only | Core navigation, ride recording, phone-sensor features and local data |
| Android + Wear OS | Watch haptics, glanceable cues, quick controls and mirrored alerts |
| Android + optional hardware | Additional IMU/GNSS inputs, physical controls and device-specific capabilities |

Availability depends on hardware, OS version, permissions, connectivity and power state.

## Initial non-goals
- Requiring users to build or buy a custom device.
- Requiring a MotoPilot account or cloud connection.
- Allowing mini-apps or AI to operate safety-critical motorcycle controls.
- Claiming medical-grade measurements from ordinary phone/watch sensors.
- Claiming certified crash detection or guaranteed emergency dispatch.
- Building a full app store before APIs and permissions stabilize.

## Status language
Use **Implemented** only when code exists and has been tested; **In progress** for active implementation; **Proposed** for design not implemented; **Experimental** for unvalidated prototypes; and **Unavailable** when a device/platform cannot provide a capability.

This repository is currently an early planning/specification project. These documents describe target design, not existing functionality.
