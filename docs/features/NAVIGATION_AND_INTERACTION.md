# Navigation and Rider Interaction

**Status:** Proposed product design.

## Navigation

OpenStreetMap is the intended map data source. Candidate components:
- MapLibre Native for map rendering.
- Offline regional vector map packages.
- GraphHopper or Valhalla for routing evaluation.
- SQLite for local metadata and route storage.
- GPX import/export.
- Android text-to-speech or local speech for turn instructions.

Select and test the routing engine and offline map packaging before implementation. Follow OSM attribution and licensing requirements. Public OSM tile servers are not unrestricted production tile hosting.

Motorcycle preferences may include scenic routes, avoiding highways, avoiding unpaved roads and touring-oriented routes. These are preferences, not guarantees; map tagging and routing profiles may be incomplete.

## Interaction model

Normalize four input classes through a shared interaction engine: voice commands, physical handlebar controls, touch and deliberate calibrated gestures. Normalize them into semantic events such as confirm, cancel, next, previous, push-to-talk and navigation action.

## Riding context

- Voice and tactile handlebar controls are primary while moving.
- Touch is restricted to simple, glanceable actions while moving.
- Detailed configuration and complex map interaction belong in stationary mode.
- Gesture recognition must reject ordinary lean, vibration, braking and road movement.
- Do not use phone or bike orientation as an unqualified generic gesture signal.

## Safety

Never require complex visual interaction for routine riding. Do not encourage screen interaction while moving. Provide audio/haptic feedback. AI and gesture inputs must not control brakes, throttle, steering, lights or other safety-critical vehicle systems.
