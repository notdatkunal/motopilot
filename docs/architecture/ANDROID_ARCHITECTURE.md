# Android Application Architecture

**Status:** Proposed architecture; implementation and minimum Android version are not yet established.

## Role

Android is the primary MotoPilot product. It must work without MotoPilot hardware and without Wear OS. Phone-native sensors and services provide baseline capabilities; optional hardware is discovered through adapters.

## Suggested technology

Kotlin, Jetpack Compose, Coroutines/Flow, Room/SQLite, Android location and sensor APIs, Android audio/speech APIs. Use foreground services only for user-visible ride sessions that require ongoing background work and comply with Android platform policy. These are proposed choices, not existing dependencies.

## Logical modules

| Module | Responsibility |
|---|---|
| app | Composition, lifecycle and navigation |
| core | Domain models, configuration and common utilities |
| location | Phone location and optional external GNSS |
| motion | Accelerometer, gyroscope and orientation |
| ride | Ride lifecycle, recording and local history |
| navigation | Maps, offline packages and route guidance |
| emergency | Event evaluation, countdown and response |
| voice | Voice interaction and audio feedback |
| interaction | Touch, physical controls and gesture events |
| device-api | Device abstraction and MDP client |
| mini-app-host | Native/web app lifecycle and permissions |
| watch-bridge | Phone/watch synchronization |
| storage | Local persistence, export and deletion |

Create modules incrementally when implementation begins; do not create empty scaffolding just to match this proposal.

## Device abstraction

Phone-native providers are first-class. External providers must not be required for app startup. Provider contracts should include lifecycle, permissions, availability, timestamps, accuracy/quality, source identity and errors.

## Display profiles

Share domain logic and feature APIs. Select presentation based on display dimensions and available inputs. A dedicated display may lack GNSS, cellular connectivity, sensors or suitable battery capacity.

## Permissions and background work

Request permissions just in time and explain their purpose. Location, microphone, Bluetooth, notifications and background operation are optional unless the user enables the relevant feature. Respect Android foreground-service types, background-location restrictions, notification requirements and OEM battery management. Report when a feature cannot run.

## UI safety

Prioritize glanceable information and audio/haptic feedback. Keep controls large and predictable. Restrict complex touch interaction during active rides. Detailed configuration belongs in stationary mode. Never require visual confirmation for routine riding tasks.

## Testing

Test multiple Android versions, phone models, screen sizes, sensor configurations and battery-management implementations. Include permission denial, sensor absence, process termination, low battery, GPS loss and connectivity interruption.
