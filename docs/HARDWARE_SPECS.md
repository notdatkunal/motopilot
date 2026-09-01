# 🛠️ MotoPilot Hardware Specifications & Sensor Protocol

## 1. Hardware Module Overview

MotoPilot is designed to interface with modular hardware attachments:
1. **Handlebar Controller / Core Hub:** ESP32-S3 microcontroller with CAN Bus (MCP2515), dual-core 240MHz, BLE 5.0, Wi-Fi.
2. **Helmet Audio & Mic Pod:** Ultra-low-power BLE audio interface with CVC noise cancellation for wind resistance.
3. **Biometric Wearable / Grip Band:** Flexible PPG optical sensor + continuous glucose monitor integration.
4. **Tire Pressure Monitoring (TPMS):** Valve cap BLE sensors broadcasting pressure and temperature at 1Hz.
5. **Dashcam Trigger Node:** GPIO/BLE signal trigger to save rolling buffer video on incident.

---

## 2. Microcontroller Wiring & Pinout (ESP32-S3)

| Component | Interface | ESP32 Pins | Description |
| :--- | :--- | :--- | :--- |
| **MPU-6050 / ICM-42670** | I2C | SDA (GPIO 21), SCL (GPIO 22) | 6-Axis Gyroscope & Accelerometer (Lean Angle & Crash) |
| **MCP2515 CAN Controller** | SPI | SCK (18), MISO (19), MOSI (23), CS (5) | Motorcycle OBD-II / CAN Bus Engine Data |
| **Status RGB LED / HUD** | GPIO | GPIO 4 | Visual alerts on cockpit / visor edge |
| **Push-to-Talk (PTT) Button**| GPIO | GPIO 15 (Pullup) | Handlebar mesh comms and incident bookmark |
| **Power Management** | 12V to 5V 3A DC-DC | 12V Switched Ignition | Powers on automatically with bike ignition |

---

## 3. Road Violation & Incident Capture Protocol

When the PTT button is held for 1.5s or the voice command *"Moto, report violation"* is issued:
1. **Camera Trigger:** Sends an active-low trigger signal to the dashcam buffer to permanently write the preceding 30s and following 30s of video.
2. **Telemetry Snapshot:** Captures exact GPS position, current speed, time, heading, and bike lean.
3. **Incident Manifest:** Packs the video hash + telemetry metadata into an encrypted report packet ready for user confirmation and one-click submission to traffic portals.
