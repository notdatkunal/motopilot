# MotoPilot Data Flow and Ownership

**Status:** Proposed design.

## Data categories

| Data | Default processing | Default persistence |
|---|---|---|
| Motion samples | On-device processing | Short-lived buffers unless recording enabled |
| GPS/location | On-device navigation and ride session | Local ride history only when enabled |
| Ride records | Local | Local database |
| Emergency event | On-device evaluation | Minimal local event record |
| Watch state | Local phone/watch synchronization | Minimal transient state |
| Hardware telemetry | Local SDK/client | Feature-dependent local storage |
| Mini-app data | App sandbox | Per-app local storage with controls |

## Rules

1. Collect only what an enabled feature needs.
2. Process locally by default.
3. Do not transmit data to a MotoPilot-operated service by default.
4. Require explicit user action or clearly configured consent before sharing/exporting.
5. Identify destination and data fields before sharing.
6. Allow users to inspect, export and delete local ride records.
7. Isolate mini-app data by app identity and permissions.
8. Do not reuse emergency contact details for unrelated purposes.

## Optional network services

Future group rides, mesh relays, map downloads and notification gateways require separate documentation describing data sent, recipient, purpose, retention and disable path.

## Reliability

Handle offline operation, partial data, delayed messages, duplicate events, stale timestamps and interrupted writes. Emergency notifications may be queued, but the UI must not imply delivery until a provider confirms it.
