# ESP32-CAM Wi-Fi Camera Car 

This project lets you remotely control a camera car using the ESP32-CAM. The car supports real-time video streaming over Wi-Fi, pan-tilt camera control using servo motors, and movement via dual DC motors driven by an L298N motor driver.

---

## 🧰 Components Required

- ESP32-CAM module
- L298N Motor Driver
- 2x DC Motors (TT gear motors recommended)
- 2x SG90 Servo Motors (for Pan and Tilt)
- 18650 Battery or 7.4V Li-ion Battery Pack
- Voltage Regulator (AMS1117 or Buck Converter)
- Jumper Wires, Chassis, Wheels

---

## ⚡ Wiring Guide

| Component | ESP32-CAM Pin | Notes |
|----------|----------------|-------|
| Motor A IN1 | GPIO 14 | Left/Right control |
| Motor A IN2 | GPIO 12 | |
| Motor B IN1 | GPIO 13 | Forward/Backward control |
| Motor B IN2 | GPIO 15 | |
| Pan Servo | GPIO 2 | Horizontal rotation |
| Tilt Servo | GPIO 4 | Vertical rotation |
| L298N VCC | Battery + | 7.4V-12V input |
| L298N GND | GND | Shared with ESP32 |
| ESP32 VCC (5V) | From Regulator | Must be regulated! |
| ESP32 GND | GND | Shared ground |

---

## 🔌 Power Setup

- Use a **buck converter** to step down 7.4V/12V battery to **5V** for ESP32-CAM.
- Do **not connect** unregulated voltage directly to the ESP32.

---

## 💻 Code Upload (Arduino IDE)

### 1. Prerequisites

Install the following in **Arduino IDE**:

- **ESP32 board** support (via Board Manager)
- Libraries:
  - `ESPAsyncWebServer`
  - `ESPAsyncTCP`
  - `Servo`

### 2. Uploading the Code

1. Connect ESP32-CAM using a USB-to-Serial adapter.
2. Connect GPIO0 to GND before uploading.
3. Select Board: `AI Thinker ESP32-CAM`.
4. Choose the correct COM port.
5. Upload the code.
6. After uploading, **disconnect GPIO0 from GND**, then press **RESET**.

---

## 🌐 Wi-Fi Configuration

In the code, update:

```cpp
const char* ssid = "Your_SSID";
const char* password = "Your_WIFI_Password";
