# MotoPilot

> **An open-source, software-first motorcycle companion platform for Android and Wear OS, with optional open hardware extensions and a third-party developer ecosystem.**

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-planning%20%2F%20early%20development-orange.svg)]()
[![Platforms](https://img.shields.io/badge/platform-Android%20%7C%20Wear%20OS-green.svg)]()

MotoPilot is designed to make useful motorcycle software available using devices riders already own. An Android phone is the primary platform; a Wear OS watch is an optional companion. External MotoPilot or third-party hardware can add sensors, physical controls and connectivity, but users should not need to build or buy hardware to use the core application.

**Project status:** This repository currently contains product concepts and architecture specifications. The documents describe a target design, not a claim that all listed applications, firmware, protocols or features are implemented. See [implementation status](#implementation-status).

## Product principles

- **Software first; hardware optional.** Start with an Android phone. Add Wear OS or external hardware when useful.
- **Local first; offline first.** Core ride features should work without a MotoPilot account or mandatory cloud service.
- **Privacy by default.** No advertising/tracking SDKs or automatic telemetry uploads are intended. Sensor processing still occurs locally when a feature is enabled.
- **Open ecosystem.** Publish protocols, SDKs, hardware sources and developer documentation for independent clients and devices.
- **Rider attention first.** Prefer voice, haptics and tactile controls. Avoid complex screen interaction while moving.
- **Safety claims must be earned.** Emergency detection is best-effort until validated; no feature guarantees crash detection or emergency dispatch.

## Applications and extensions

| Component | Role | Required? |
|---|---|---|
| Android app | Primary cockpit, navigation, ride recording, voice, local settings and optional emergency detection | Yes for initial software product |
| Wear OS app | Glanceable cues, haptics, quick controls and emergency alert companion | No |
| Android launcher | Optional home-screen integration | No |
| Dedicated Android display | Larger cockpit profile using Android application | No |
| MotoPilot reference hardware | Optional sensors and physical controls | No |
| Third-party clients/devices | Independent integrations using published APIs and protocol | No |

## Planned capabilities

- **Navigation:** OpenStreetMap-based navigation with offline map support under evaluation.
- **Ride recording:** Local GPS-based ride sessions and history.
- **Voice and interaction:** Voice, tactile handlebar controls, touch and calibrated gestures, with interaction constrained by riding context.
- **Emergency response:** Optional phone-sensor-based possible-crash detection, cancellation countdown and user-configured contact notification. Not a certified crash detector.
- **Wear OS companion:** Navigation cues, haptics, ride status and emergency countdown mirroring.
- **Mini-apps:** Hybrid native and sandboxed web extension model, planned after SDK and permission system stabilize.
- **Optional hardware:** Modular ESP32-S3 reference-device candidate, external IMU/GNSS and handlebar controls.

All items above are planned unless explicitly marked implemented in a future release note.

## Architecture at a glance

~~~text
Android phone app / optional launcher / dedicated display
                 |
          MotoPilot Android Core
                 |
    +------------+-------------+
    |            |             |
 Core features  Mini-apps   Wear OS companion
    |            |             |
    +----- SDK / capability APIs
                 |
        Device abstraction layer
                 |
       MotoPilot Device Protocol
                 |
       BLE / USB / future transports
                 |
        Optional external hardware
~~~

The Android application must work without hardware. The Wear OS application is optional and must not be required for phone functionality.

## Documentation

### Product and architecture
- [Product vision](docs/PRODUCT_VISION.md)
- [System architecture](docs/architecture/SYSTEM_ARCHITECTURE.md)
- [Android architecture](docs/architecture/ANDROID_ARCHITECTURE.md)
- [Wear OS architecture](docs/architecture/WEAR_OS_ARCHITECTURE.md)
- [Hardware abstraction](docs/architecture/HARDWARE_ABSTRACTION.md)
- [Data flow and ownership](docs/architecture/DATA_FLOW.md)

### Features and developer platform
- [Navigation and rider interaction](docs/features/NAVIGATION_AND_INTERACTION.md)
- [Emergency detection and response](docs/features/EMERGENCY_RESPONSE.md)
- [Mini-app runtime](docs/features/MINI_APP_RUNTIME.md)
- [MotoPilot Device Protocol proposal](docs/protocol/DEVICE_PROTOCOL.md)

### Trust, safety and delivery
- [Privacy and security](docs/privacy/PRIVACY_AND_SECURITY.md)
- [Roadmap](docs/ROADMAP.md)
- [Existing hardware specifications](docs/HARDWARE_SPECS.md)
- [Existing telemetry concepts](docs/TELEMETRY_ARCHITECTURE.md)
- [MotoQuest and mesh concepts](docs/MOTOQUEST_GAMIFICATION_AND_MESH.md)

## Implementation status

The current repository is an early-stage concept/specification repository. The Android app, Wear OS app, stable MDP release, mini-app runtime, emergency detection pipeline and reference hardware are not established as implemented by these documents.

Existing hardware, telemetry and MotoQuest documents are retained as design material. Proposed sensor integrations, algorithms, thresholds, performance claims and health-related measurements must be validated before being treated as achievable or production-ready. Ordinary phone/watch sensors do not provide medical-grade blood glucose or blood pressure measurements.

Use these labels in future documentation and release notes:
- **Implemented:** present in code and tested.
- **In progress:** actively being implemented.
- **Proposed:** designed but not implemented.
- **Experimental:** prototype only; not validated for general use.
- **Unavailable:** unsupported by current device or platform.

## Contributing

Contributions should preserve software-first, hardware-optional and privacy-first principles. New device integrations should use documented abstractions and protocol contracts. Safety-related changes require test evidence, failure-mode analysis and clear user-facing limitations.

## Licensing

The repository currently declares MIT licensing. The intended long-term licensing model for firmware, hardware, SDKs, applications and documentation has not been finalized. Do not assume proposed per-component licensing has been adopted. Any licensing migration requires compatibility and legal review.

## Disclaimer

MotoPilot is a development project, not a certified vehicle system, medical device or emergency response service. Riders remain responsible for safe motorcycle operation and compliance with local laws. Do not interact with the screen while riding in a way that distracts from road conditions.
