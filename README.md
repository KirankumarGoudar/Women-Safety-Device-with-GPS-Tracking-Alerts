# Women-Safety-Device-with-GPS-Tracking-Alerts
Technologies: Arduino/ESP32, GPS Module (NEO-6M), GSM Module (SIM800L), Embedded C, IoT, Sensors 


# 🚨 Emergency Alert and GPS Tracking Device for Women Safety

> A compact, embedded hardware solution that sends real-time GPS location via GSM to emergency contacts or authorities at the press of a button.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Hardware Components](#hardware-components)
- [Circuit Diagram](#circuit-diagram)
- [How It Works](#how-it-works)
- [System Architecture](#system-architecture)
- [Getting Started](#getting-started)
- [Future Improvements](#future-improvements)
- [Team](#team)
- [Guide](#guide)
- [License](#license)

---

## Overview

Increasing incidents of harassment and violence against women highlight the urgent need for quick, reliable safety solutions. Traditional alert methods (phone calls, apps) are often inaccessible during high-stress emergencies.

This project implements a **standalone, wearable emergency alert device** that:
- Requires only a **single button press** to trigger
- Automatically fetches **real-time GPS coordinates** via the NEO-6M GPS module
- Transmits the location as an **SMS via GSM (SIM800L)** to pre-configured emergency contacts or authorities
- Operates independently — **no smartphone required**

---

## Features

- ⚡ **One-press SOS trigger** — minimal interaction needed in distress
- 📍 **Real-time GPS tracking** — live latitude/longitude via NEO-6M module
- 📱 **GSM-based SMS alert** — location sent instantly via SIM800L modem
- 📡 **RF communication** — 433 MHz transmitter/receiver for local range signaling
- 🔋 **Battery-powered** — portable and wearable form factor
- 🔒 **No internet dependency** — works on GSM network alone

---

## Hardware Components

| Component | Description |
|-----------|-------------|
| **Arduino Nano** | Main microcontroller unit |
| **SIM800L GSM Modem** | Sends SMS with GPS coordinates |
| **NEO-6M GPS Module** | Acquires real-time GPS location |
| **433 MHz RF Transmitter & Receiver** | Local wireless communication |
| **Push Button** | Emergency trigger input |
| **Li-Po Battery + Charging Module** | Portable power supply |
| **Breadboard & Jumper Wires** | Prototyping connections |

---

## Circuit Diagram

```
[Push Button] ──────────────────────────────────────┐
                                                     ▼
[Battery + Charger] ──── [Arduino Nano] ──── [SIM800L GSM]
                                │
                                ├──── [NEO-6M GPS Module]
                                │
                                └──── [433 MHz RF Tx/Rx]
```

> Full circuit diagram is available in the `/docs/circuit_diagram.png` file.

---

## How It Works

```
1. User presses the emergency button
        │
        ▼
2. Arduino Nano reads button interrupt
        │
        ▼
3. NEO-6M GPS module acquires coordinates (lat, long)
        │
        ▼
4. SIM800L formats and sends SMS:
   "EMERGENCY! Location: https://maps.google.com/?q=<lat>,<long>"
        │
        ▼
5. SMS delivered to pre-configured emergency contacts / police
```

---

## System Architecture

```
┌─────────────────────────────────────────────┐
│              HARDWARE LAYER                 │
│  Button → Arduino Nano → GPS + GSM + RF     │
└─────────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────┐
│            COMMUNICATION LAYER              │
│   GSM Network (SMS) + 433MHz RF Signal      │
└─────────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────┐
│             RESPONSE LAYER                  │
│  Emergency Contact / Police receives SMS    │
│  with Google Maps location link             │
└─────────────────────────────────────────────┘
```

---

## Getting Started

### Prerequisites

- Arduino IDE (v1.8.x or later)
- Required libraries:
  - `TinyGPS++` — GPS parsing
  - `SoftwareSerial` — serial communication with GSM & GPS
  - `VirtualWire` — 433 MHz RF communication

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/women-safety-gps-alert.git

# Open the Arduino sketch
cd women-safety-gps-alert/src
# Open main.ino in Arduino IDE
```

### Configuration

Edit the following in `main.ino` before uploading:

```cpp
// Set your emergency contact number
String emergencyNumber = "+91XXXXXXXXXX";

// Set the SMS message prefix
String alertMessage = "EMERGENCY ALERT! Location: ";
```

### Upload

1. Connect Arduino Nano via USB
2. Select board: `Arduino Nano` and correct COM port
3. Click **Upload**

---

## Expected Result

When the emergency button is pressed **once**:
- The GPS module fetches the current coordinates
- The SIM800L sends an SMS to the registered emergency number containing a Google Maps link to the victim's live location
- The RF transmitter simultaneously broadcasts a local distress signal

---

## Challenges & Limitations

- GPS fix may take 30–60 seconds in indoor environments (cold start delay)
- SIM800L requires a stable GSM network connection
- Battery life depends on GPS polling frequency
- Privacy considerations must be addressed before deployment

---

## Future Improvements

- [ ] Integration with a mobile app for real-time live tracking dashboard
- [ ] AI-based distress detection (voice/motion triggers) using ML on edge
- [ ] Miniaturization into a wearable wristband or jewellery form factor
- [ ] Multi-contact SMS broadcasting
- [ ] Geofencing alerts for safe zone boundary detection
- [ ] WhatsApp / Telegram API integration for richer alerts

---

## Team

| Name | USN |
|------|-----|
| Kirankumar Goudar | 1HK22EC072 |
| M JaganMohan Reddy | 1HK22EC081 |
| M. Sathya Sai | 1HK22EC100 |
| Prutviraj Tuppad | 1HK22EC128 |

**Department:** Electronics & Communications Engineering
**Institution:** H.K.B.K College of Engineering, Bangalore – 560045
**University:** Visvesvaraya Technological University (VTU)

---

## Guide

**Dr. Surendiran J**
Assistant Professor, Dept. of ECE
HKBK College of Engineering, Bangalore

---

## License

This project is developed for academic purposes under **H.K.B.K College of Engineering**.
Feel free to fork and build upon this for non-commercial, educational use.

---

<p align="center">
  Built with ❤️ for women's safety | HKBKCE Bangalore
</p>
