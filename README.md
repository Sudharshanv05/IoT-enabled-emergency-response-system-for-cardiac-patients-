# 💓 IoT-Based Emergency Response System for Cardiac Patients (ESP32)

This project is a wearable, real-time health monitoring system designed for cardiac patients. It uses an ESP32 microcontroller to measure vital signs such as heart rate, SpO₂, and blood pressure (simulated), and sends emergency alerts via GSM and updates through a Blynk mobile dashboard.

---

## 📦 Project Features

✅ Real-time monitoring of:
- Heart rate (bpm) and SpO₂ (%) via MAX30102 sensor  
- Simulated blood pressure (can be replaced with real analog sensor)  
- Optional motion tracking with MPU6050 (for fall detection)  

✅ Emergency alert system:
- Sends **SMS alerts via SIM800L** to emergency contact when vitals cross defined limits  
- Sends live data to a **Blynk mobile dashboard** via Wi-Fi  

✅ Wearable and battery-powered for portable use

---

## 🧰 Hardware Components

| Component        | Quantity | Description                        |
|------------------|----------|------------------------------------|
| ESP32 Dev Board  | 1        | Main microcontroller with Wi-Fi    |
| MAX30102 Sensor  | 1        | Heart Rate & SpO₂ monitoring       |
| SIM800L Module   | 1        | GSM/GPRS module for SMS alerts     |
| MPU6050          | 1        | Accelerometer & gyroscope          |
| Li-ion Battery (3.7V) | 1    | Portable power source              |
| Level Shifter / Resistor | 2 | For SIM800L RX voltage protection |
| Blynk App (Android/iOS) | 1 | For real-time mobile dashboard     |

---

## 🔌 Wiring Connections

| ESP32 Pin | Connected Module | Function       |
|-----------|------------------|----------------|
| 3.3V      | MAX30102, MPU6050 | Power (if using 3.3V modules) |
| 5V / VIN  | SIM800L (via 4.2V booster or Li-ion) | Power |
| GND       | All Modules       | Ground         |
| GPIO 21   | MAX30102 SDA      | I2C Data       |
| GPIO 22   | MAX30102 SCL      | I2C Clock      |
| GPIO 21   | MPU6050 SDA       | I2C Data       |
| GPIO 22   | MPU6050 SCL       | I2C Clock      |
| GPIO 17   | SIM800L TX        | UART Receive   |
| GPIO 16   | SIM800L RX (via 1kΩ) | UART Transmit  |

> ⚠️ Use a **separate power supply (like Li-ion battery)** for SIM800L. Do not power it directly from ESP32.

---

## 📱 Blynk Dashboard Setup

Create a Blynk Template & Device, and use these **virtual pins**:

| Data            | Virtual Pin |
|------------------|-------------|
| Heart Rate       | V1          |
| SpO₂             | V2          |
| Blood Pressure   | V3          |
| Alert Status     | V4          |

---

## 📲 Software Features

- **Blynk Cloud Integration** for monitoring via mobile app
- **Emergency Conditions**:
  - Heart Rate > 100 bpm
  - SpO₂ < 92%
  - BP > 140 mmHg
- When above thresholds are crossed:
  - Display "⚠️ EMERGENCY!" on Blynk dashboard
  - Send SMS alert to predefined number

---

## 🚀 How to Use

### 1. ✅ Hardware Setup
- Connect all sensors to ESP32 using I2C and UART (see wiring)
- Power the ESP32 via USB and SIM800L via Li-ion battery

### 2. ⚙️ Software Setup
- Open `main.ino` in Arduino IDE
- Install required libraries:
  - Blynk
  - WiFi
  - Adafruit_Sensor
  - Adafruit_MPU6050
  - MAX30105
- Replace:
  - `Your_SSID` and `Your_PASSWORD`
  - `Your_BLYNK_TEMPLATE_ID`, `BLYNK_TEMPLATE_NAME`, `BLYNK_AUTH_TOKEN`
  - Emergency mobile number in `sendSMSAlert()`
- Select Board: `ESP32 Dev Module`
- Select Port: COM port of your board
- Upload the code

### 3. 📱 Setup Blynk App
- Add a **New Device → From Template**
- Add **4 Value Display Widgets** connected to V1–V4
- Name appropriately (e.g., HR, SpO₂, BP, Alert)

---

## 🧪 Output Sample (Serial Monitor)
---
note: the code was uploaded as raw format check and download and It is for educational purpose only!!!
