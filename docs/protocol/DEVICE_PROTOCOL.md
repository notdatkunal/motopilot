# MotoPilot Device Protocol (MDP)

**Status:** Protocol proposal; no stable released specification exists yet.

## Goals

MDP is an open, versioned protocol between MotoPilot clients and compatible external devices. It is independent of transport and official applications. A third-party client should be able to implement it from this specification alone once v1 is finalized.

## Initial transport candidates

1. BLE GATT for wireless communication.
2. USB CDC serial for development and wired integration.
3. Local Wi-Fi API may follow after the first version stabilizes.
4. MQTT, mesh and LoRa are future optional transports, not initial interoperability commitments.

## Initial message families

- Device identity and firmware information.
- Protocol version negotiation.
- Capability discovery.
- Pairing/session establishment.
- Telemetry events.
- Configuration read/write.
- Supported control commands.
- Error and diagnostic events.

## Encoding

JSON is a candidate for initial human-readable messages. CBOR may be evaluated for constrained transports. Final encoding must be specified per transport and covered by canonical test vectors.

## Required properties

- Explicit protocol and schema versions.
- Stable capability identifiers.
- Timestamps and source identity for telemetry.
- Defined units, ranges, precision and missing-value semantics.
- Authentication and authorization for privileged commands.
- Replay resistance for state-changing operations.
- Clear error codes and unsupported-capability responses.
- Backward-compatibility and deprecation policy.

## Security

Pairing must establish trust. Use authenticated sessions and transport-appropriate encryption. Privileged operations require authorization. Firmware updates must be authenticated; secure boot should be enabled where supported.

## Interoperability deliverables

A stable MDP release requires a normative specification, machine-readable schemas, BLE/USB mappings, example sequences, positive and negative test vectors, reference implementations and a compatibility test suite. Until then, MDP is proposed, not implemented.
