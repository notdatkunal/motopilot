# Privacy and Security Principles

**Status:** Target requirements; legal review and implementation remain outstanding.

## Privacy defaults

- No mandatory account or cloud service.
- No advertising or tracking SDKs.
- No analytics or telemetry upload by default.
- Local processing for ride, motion and emergency data wherever practical.
- Explicit user action or configured consent before export/sharing.
- User-accessible export and deletion for local records.
- Data minimization and documented retention periods.

The app necessarily processes sensor data when a feature is enabled. “No data collection” means no undisclosed or unnecessary collection/transmission, not no sensor processing.

## Permissions

Request Android permissions only when a user enables a feature that needs them. Explain location, microphone, Bluetooth, notifications, background operation and any health-data integration. Degrade gracefully when permissions are denied or revoked.

## Security controls

- Secure local storage for sensitive information.
- Authenticated device pairing and encrypted sessions.
- Least-privilege SDK and mini-app APIs.
- Replay protection for state-changing commands.
- Signed firmware updates.
- Secure boot where supported.
- Dependency review and vulnerability reporting.
- No secrets or personal data in logs by default.

## Optional sharing

For every future network feature, document data sent, recipient, purpose, retention, transport security and disable path. Do not silently upload ride history, location trails, sensor streams, emergency contacts or watch data.

## Emergency data

Emergency contact details and event locations are sensitive. Keep them local until an emergency workflow is triggered. Share only the minimum configured payload. Distinguish queued, attempted and confirmed delivery.

## Open-source governance

Publish threat models, security assumptions, supported versions, disclosure contact and release notes. Licensing across firmware, hardware, SDKs, apps and documentation requires a compatibility review; this document does not make a final legal determination.
