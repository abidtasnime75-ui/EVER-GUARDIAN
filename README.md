# EVER-GUARDIAN
             Wearable Elderly Monitoring device; Fall Detection System — IEEE RAS FST


🛡️ EVER GUARDIAN

## 📖 About The Project

**EVER GUARDIAN** is a wearable IoT device designed for elderly individuals (65+). It continuously monitors health and safety, and automatically sends alerts to a guardian's smartphone in case of a fall, physiological anomaly, or emergency.

The device is worn on the wrist like a smartwatch, and communicates with a mobile app via Wi-Fi and GSM cellular network — ensuring coverage both at home and outdoors.

> Developed under the **IEEE Robotics & Automation Society — FST Student Branch**
> DIY IT Internal Development Program 

---

 ✨ Features

| Feature                    | Description                                                    |
|----------------------------|----------------------------------------------------------------|
| 🤸 **Fall Detection**      | 3-phase kinematic algorithm (impact → orientation → stillness) |
| 💓 **Heart Rate & SpO₂**   | Continuous PPG monitoring via MAX30102                         |
| 🌡️ **Skin Temperature**    | Contact-based measurement via MAX30205                         |
|  **glucose estimation *    | Contact-based measurement via MAX30205                         |
| 📍 **GPS Tracking**        | Real-time location with geofencing (500m safe zone)            |
| 😴 **Sleep Tracking**      | Overnight HR and SpO₂ monitoring                               |
| 🆘 **safety button **      | One long press → false alert                                   |
| 💊 **Medication Reminder** | Scheduled caregiver notifications                              |
| 📱 **Guardian App**        | Flutter mobile app — alerts, map, vitals dashboard             |
| 📡 **Dual Communication**  | Wi-Fi (primary) + GSM/GPRS (fallback)                          |
| 🔋 **Battery**             | LiPo 3.7V 1500 mAh — ~9-10h daily autonomy                     |

---

 🏗️ System Architecture

```
┌─────────────────────────────┐        ┌──────────────────────────────┐
│      WEARABLE DEVICE        │        │       CLOUD + MOBILE         │
│                             │        │                              │
│  SENSORS                    │        │  ☁️  Firebase RTDB           │
│  ├── MAX30102  (HR / SpO/ glucose)  │        │  ☁️  MQTT Broker             │
│  ├── MPU6050  (Fall IMU)    │──────▶ │  ☁️  FCM Notifications       │
│  ├── MAX30205 (Temperature) │        │                              │
│  ├── NEO-6M   (GPS)         │        │  📱 GUARDIAN APP             │
│  └── Safety Button          │        │  ├── Push Alerts             │
│                             │        │  ├── Live GPS Map            │
│  🧠 ESP32 MCU               │        │  ├── Vitals Dashboard        │
│  ├── Signal Processing      │        │  └── History & Logs          │
│  ├── Fall Detection (ML)    │        │                              │
│  ├── Alert Decision Logic   │        └──────────────────────────────┘
│  └── Wi-Fi + GSM Manager    │
│                             │
│  📶 SIM800L GSM             │
│  🔋 LiPo 1500mAh            │
└─────────────────────────────┘

        I²C / UART                GPRS · MQTT · HTTPS · FCM
```

---
 🔧 Hardware Components

| Component        | Role                                       | Interface |
|------------------|--------------------------------------------|-----------|
| ESP32-WROOM-32D  | Main MCU — 240 MHz dual-core               | __________|
| MAX30102         | Heart Rate & SpO₂ sensor                   | I²C 0x57  |
| MPU6050          | Accelerometer + Gyroscope (fall detection) | I²C 0x68  |
| MAX30205         | Skin temperature sensor                    | I²C 0x48  |
| NEO-6M           | GPS module — real-time location            | UART 9600 |
| SIM800L          | GSM/GPRS module — cellular fallback        | UART 9600 |
| TP4056           | USB-C LiPo battery charger                 | __________|
| AMS1117-3.3      | 3.3V LDO regulator (ESP32 + sensors)       | __________|
| MT3608           | 4.0V boost converter (SIM800L)             | __________|
| DW01A            | Battery protection BMS                     | __________|



---

---

 🚀 Development Phases

```
Phase 1 ██████████  DONE     Research & System Architecture
Phase 2 ░░░░░░░░░░  NEXT     Hardware Prototyping
Phase 3 ░░░░░░░░░░  TODO     Firmware Development (ESP32 FreeRTOS)
Phase 4 ░░░░░░░░░░  TODO     Cloud & Guardian Mobile App
Phase 5 ░░░░░░░░░░  TODO     PCB Design (KiCad)
Phase 6 ░░░░░░░░░░  TODO     3D Enclosure & Assembly
Phase 7 ░░░░░░░░░░  TODO     Testing & Validation
Phase 8 ░░░░░░░░░░  TODO     Final Documentation & Presentation





 📄 License

This project is licensed under the MIT License.




 Built with ❤️ for elderly safety — IEEE RAS FST Student Branch
