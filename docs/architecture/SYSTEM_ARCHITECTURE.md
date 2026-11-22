# MotoPilot System Architecture

**Status:** Target architecture; not an implementation claim.

## Overview

MotoPilot is software-first and hardware-optional. Android must deliver core functionality using built-in phone capabilities. Wear OS is an optional companion. External hardware adds capabilities through stable interfaces and an open protocol.

~~~text
Android phone app / optional launcher / dedicated display
                    |
             Android Core
                    |
       +------------+-------------+
       |            |             |
   Core features  Mini-apps   Wear bridge
       |            |             |
       +------ SDK / capability APIs
                    |
        Capability and permission layer
                    |
          Device abstraction / adapters
                    |
          MotoPilot Device Protocol
                    |
       BLE / USB / local Wi-Fi / future
                    |
         Optional external hardware
~~~

The Android app must not require an external MotoPilot device to start or provide phone-native capabilities.

## Layers

**Client layer:** Android phone app, optional launcher, dedicated-display cockpit, Wear OS companion and future third-party clients.

**Application services:** navigation, offline map management, ride recording, emergency response, voice/audio, input normalization, mini-app host, device management.

**Platform abstractions:** location, motion, audio, notifications, storage, connectivity and motorcycle-device capabilities. Implement phone-native providers first.

**Device integration:** MDP is independent of transport. BLE GATT and USB CDC are initial candidates. Local Wi-Fi may follow. MQTT, mesh and LoRa are optional future transports.

## Android and display

Phone and dedicated display share domain logic, SDK and design system, with responsive presentation profiles. The optional launcher is a separate integration; MotoPilot remains usable as an ordinary app. Do not assume a dedicated display has phone-equivalent sensors or connectivity.

## Wear OS

The watch is a lightweight companion. The phone normally handles maps, routing, storage and heavier processing. The watch receives compact events and provides haptic, audio or glanceable feedback. Phone functionality must continue if the watch is absent.

## Local-first operation

Process motion and ride data locally by default. Persist ride history on-device. Do not upload telemetry automatically. Make export and sharing explicit. Handle loss of GPS, network, watch, hardware and permissions as degraded operating conditions.

## Safety boundaries

MotoPilot must not control brakes, throttle, steering, lights or other safety-critical vehicle functions. AI advice is non-authoritative. Emergency detection is best-effort, not guaranteed crash detection or emergency response.

## Compatibility

Version public APIs and MDP independently from app releases. Publish capability discovery, schemas, unsupported-capability responses and compatibility tests. The architecture does not establish that the Android app, Wear OS app, MDP or mini-app runtime already exists.
