# MotoPilot Roadmap

**Status:** Proposed sequence. No delivery dates or commitments have been assigned.

The roadmap prioritizes a useful software product before optional hardware.

## Phase 0 — Product and architecture baseline
- Confirm software-first, hardware-optional direction.
- Define Android, Wear OS and optional display roles.
- Specify device abstraction and MDP requirements.
- Define privacy, security and emergency safety requirements.
- Review licensing and existing speculative claims.

**Exit:** Architecture and API boundaries reviewed; proposed features separated from implemented work.

## Phase 1 — Android software MVP
- App foundation and local settings.
- Ride session lifecycle and local recording.
- Phone location and motion providers.
- Basic cockpit and privacy controls.
- Emergency detection prototype with test mode and no automatic public emergency dispatch.

**Exit:** Core ride session works on supported phones without MotoPilot hardware; limitations and sensor availability are visible.

## Phase 2 — Wear OS companion
- Phone/watch synchronization.
- Navigation cues and haptics.
- Ride status and quick controls.
- Emergency countdown mirror and cancellation.
- Disconnection and stale-data handling.

**Exit:** Watch is optional; phone remains functional without it.

## Phase 3 — Navigation and rider interaction
- Select map renderer and routing engine.
- Offline regional map packages.
- Voice instructions.
- Input normalization for touch and handlebar controls.
- Gesture support only after calibration and safety testing.

**Exit:** Routine navigation and interaction avoid complex screen use while moving.

## Phase 4 — Open SDK and device protocol
- Stabilize MDP v1.
- Publish schemas and test vectors.
- Implement Kotlin and Python SDKs.
- Provide CLI and simulator.
- Add reference device adapter.

**Exit:** An independent client interoperates with a reference implementation.

## Phase 5 — Optional reference hardware
- ESP32-S3 reference design.
- External IMU/GNSS and physical controls.
- Protected motorcycle power design.
- BLE and USB transports.
- Open schematics, PCB, BOM, enclosure and assembly docs.

**Exit:** Hardware is reproducible and adds capabilities without being required by Android.

## Phase 6 — Mini-app ecosystem
- Native mini-app API.
- Capability broker and manifest.
- Sandboxed web runtime.
- Developer examples and conformance tests.

**Exit:** Third-party extensions operate with least privilege and cannot access raw hardware drivers.

## Phase 7 — Ecosystem expansion
- Optional Android launcher.
- Additional hardware adapters.
- Rider mesh and community features.
- AI/MCP integrations with read-only defaults.
- Additional client platforms.

## Release discipline

Every feature needs implementation status, supported device/OS matrix, permission/privacy impact, degraded-mode behaviour, tests, acceptance criteria and clear limitations. Safety-related claims require test evidence.
