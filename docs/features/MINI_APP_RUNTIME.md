# Mini-App Runtime and Developer Model

**Status:** Proposed; runtime and APIs are not implemented.

## Goal

Allow third-party developers to extend MotoPilot without granting unrestricted access to hardware, personal data or other applications.

## Runtime direction

Use a hybrid model:
- Native Kotlin/Compose experiences for trusted, performance-sensitive first-party features.
- Sandboxed web mini-apps for portable community extensions.

Start with first-party native modules. Introduce the web runtime only after SDK and permission design stabilize.

## Architecture

~~~text
MotoPilot Android host
  -> Mini-app lifecycle manager
  -> App identity and manifest validation
  -> Permission/capability broker
  -> Native or sandboxed web runtime
  -> Public MotoPilot SDK
  -> Device abstraction and approved APIs
~~~

Mini-apps must not call sensor drivers, Bluetooth APIs, filesystem APIs or MDP transports directly. They use the documented SDK and only granted capabilities.

## Manifest

A future manifest should declare app identifier/version, display name/publisher, runtime type, minimum API version, requested capabilities, storage needs, network access declaration and signing/trust metadata.

## Example capability identifiers

- location.read
- telemetry.read
- navigation.read
- navigation.control
- audio.output
- mesh.read
- device.configure

These identifiers are illustrative, not stable APIs.

## Security requirements

Least-privilege permissions, user-visible prompts, revocation, app identity/signing, runtime isolation, resource limits, no unrestricted network by default, and no access to emergency contacts or emergency controls unless a narrowly scoped reviewed API is later designed. Mini-apps must never control safety-critical vehicle functions.

## Developer experience

Publish SDK docs, sample mini-apps, simulator/test mode, compatibility matrix and conformance tests. Do not build a public app store until signing, review, distribution and update security are designed.
