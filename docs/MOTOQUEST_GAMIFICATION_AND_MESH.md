# 🎮 MotoQuest: Gamification, Pothole Scoring & Offline Mesh Protocol

## 1. Safety-First Audio Gaming Mechanics

MotoQuest is the interactive gamification engine integrated directly into **MotoPilot**. It requires **zero visual screen interaction while riding**.

### Audio Cue Taxonomy
- **Chime (Ascending):** Checkpoint entered / Territory claimed (+100 XP).
- **Radar Ping (Stereo Panned):** Nearby obstacle or pothole located ahead (Left ear = obstacle on left side; Right ear = obstacle on right).
- **Whoosh Sound:** Successful smooth evasive swerve / obstacle dodged (+50 XP).
- **Thud & Penalty Tone:** Direct pothole impact registered via accelerometer shock (-20 XP).
- **Triumph Fanfare:** New "Apex King/Queen" segment record achieved.

---

## 2. Pothole Detection & Avoidance Algorithm

```
                 IMU Accelerometer (Z-Axis & Lateral Y-Axis)
                                     │
                                     ▼
                   ┌───────────────────────────────────┐
                   │     High-Pass Filter (Noise Cut)  │
                   └─────────────────┬─────────────────┘
                                     │
         ┌───────────────────────────┴───────────────────────────┐
         ▼                                                       ▼
┌─────────────────────────────────┐             ┌───────────────────────────────────┐
│     Z-Axis Peak Shock > 2.5G    │             │   Lateral Y-Axis Smooth Shift     │
│   (Sudden Suspension Drop)      │             │   (Smooth Swerve around Obstacle) │
└────────────────┬────────────────┘             └─────────────────┬─────────────────┘
                 │                                                │
                 ▼                                                ▼
     🚨 Direct Impact Registered                     ⭐ Smooth Avoidance Registered
     • Log severity rating (1-5)                     • +50 Dodging Reflex XP
     • Mark road defect location                     • Reward "Smooth Operator" streak
```

---

## 3. Offline P2P Mesh Protocol (Biker BitChat Engine)

When riding through remote mountain canyons without cell reception, MotoPilot switches to an autonomous ad-hoc BLE/Wi-Fi mesh:

### A. Discovery & Handshake
- Nodes broadcast continuous BLE advertisement beacons containing `RiderID`, `PackID`, and a `CRDT_VectorClock`.
- Nearby nodes within 30–70 meters form transient star or multi-hop mesh clusters automatically.

### B. Gossip Data Packet Format
```json
{
  "packet_id": "pkt_998a12",
  "protocol_version": "1.0",
  "hop_count": 2,
  "max_hops": 5,
  "sender": {
    "rider_id": "usr_kunal_01",
    "callsign": "GhostRider"
  },
  "payload_type": "HAZARD_ALERT_OR_SCORE_SYNC",
  "data": {
    "type": "POTHOLE_REPORTED",
    "coordinates": {"lat": 13.0827, "lng": 80.2707},
    "severity": 4,
    "timestamp": 1756724000
  },
  "crdt_clock": {
    "usr_kunal_01": 42,
    "usr_alex_02": 19
  }
}
```

---

## 4. Leaderboard Titles & Gamification Tiers

| Title | Requirement | Perk / Badge |
| :--- | :--- | :--- |
| **Pothole Slayer** | 50 verified potholes dodged or reported | Unlocks Golden Handlebar icon & civic bounty reward |
| **Apex Maestro** | Top 10% smoothness score on 20 mountain twisty segments | Special Audio fanfare on pass summits |
| **Pack Alpha** | Leads a mesh group of 5+ riders with zero dropped packets | Mesh relay priority node status |
| **Iron Butt Explorer** | 500 km of territory exploration in a single quest | Global Explorer Tier III badge |
