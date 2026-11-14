# 💧 Online TDS Measurement of RO Plant

**An IoT-based water quality monitoring system that measures Total Dissolved Solids (TDS) in Reverse Osmosis (RO) water with real-time monitoring, cloud-based data logging, visualization, and automatic alerts.**

![Project](https://img.shields.io/badge/Project-IoT%20Based-blue)
![Microcontroller](https://img.shields.io/badge/Controller-ESP32-green)
![Programming](https://img.shields.io/badge/Language-C%2FC%2B%2B-orange)
![Platform](https://img.shields.io/badge/Platform-Arduino%20IDE-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Features](#-features)
- [System Architecture](#-system-architecture)
- [Hardware Components](#-hardware-components)
- [Software Stack](#-software-stack)
- [Working Principle](#-working-principle)
- [Installation & Setup](#-installation--setup)
- [Usage](#-usage)
- [Calibration & Maintenance](#-calibration--maintenance)
- [Troubleshooting](#-troubleshooting)
- [Applications](#-applications)
- [Future Enhancements](#-future-enhancements)
- [License](#-license)

---

## 📖 Overview

The **Online TDS Measurement of RO Plant** is an IoT-based project designed to automate the monitoring of Total Dissolved Solids (TDS) in Reverse Osmosis water treatment plants.

Traditional TDS measurement methods require manual testing, making continuous monitoring and historical data analysis difficult.

To overcome these limitations, this project integrates a DFRobot Gravity TDS Sensor with an ESP32 microcontroller to measure and process TDS values.

The ESP32 transmits the measured data through Wi-Fi to the Blynk IoT platform for real-time visualization. It also supports automatic data logging in Google Sheets for historical analysis.

A buzzer alert is provided when the measured TDS value exceeds the predefined threshold of **1000 ppm**.

### 🎯 Project Objectives

- Enable real-time TDS monitoring.
- Automate water quality measurement.
- Store sensor readings hourly in Google Sheets.
- Provide remote monitoring through Blynk IoT.
- Generate alerts when TDS exceeds the configured threshold.
- Reduce manual intervention and improve monitoring efficiency.

---

## ❗ Problem Statement

Conventional RO plants often depend on manual TDS measurement, which introduces several limitations:

- Lack of continuous water quality monitoring.
- No real-time remote access to TDS readings.
- Limited historical data storage.
- Absence of automatic alert mechanisms.
- Increased manual effort and monitoring time.

This project addresses these challenges through an IoT-based monitoring system that provides real-time readings, automated data logging and threshold-based alerts.

---

## ✨ Features

- **Real-Time TDS Monitoring:** Measures dissolved solids in water using a TDS sensor.
- **IoT Connectivity:** Uses ESP32 built-in Wi-Fi for cloud communication.
- **Mobile Dashboard:** Displays TDS readings through the Blynk IoT application.
- **Automatic Data Logging:** Stores TDS readings in Google Sheets at the configured hourly interval.
- **Threshold-Based Alerts:** Activates a buzzer when TDS exceeds 1000 ppm.
- **Historical Data Analysis:** Maintains records of water quality measurements.
- **Remote Monitoring:** Enables users to monitor readings without being physically present at the RO plant.

---

## 🏗️ System Architecture

The system consists of a sensor unit, processing unit, alert mechanism and cloud monitoring platform.

### Architecture Diagram

```text
             WATER SAMPLE
                  |
                  ▼
              TDS SENSOR
                  |
             Analog Signal
                  |
                  ▼
                 ESP32
           (Data Processing)
                  |
                  ▼
             TDS Calculation
                  |
                  ▼
          Threshold Comparison
                  |
             ┌────┴────┐
             |         |
          >1000 ppm   Wi-Fi
             |         |
             ▼         ▼
           BUZZER    CLOUD
                       |
                 ┌─────┴─────┐
                 |           |
                 ▼           ▼
              BLYNK      GOOGLE SHEETS
                 |           |
                 ▼           ▼
           LIVE DASHBOARD  DATA LOGGING
```

### Data Flow

1. The TDS sensor measures the electrical properties of water.
2. The sensor generates an analog voltage signal.
3. ESP32 reads the signal through its ADC.
4. The microcontroller processes the readings and calculates TDS in ppm.
5. The measured value is compared against the configured threshold.
6. The buzzer is activated if TDS exceeds 1000 ppm.
7. ESP32 transmits readings through Wi-Fi.
8. Blynk displays real-time measurements.
9. Google Sheets stores readings for historical analysis.

---

## 🔧 Hardware Components

| Component | Description | Quantity |
|---|---|---:|
| ESP32 | DFRobot FireBeetle ESP32 development board | 1 |
| TDS Sensor | DFRobot Gravity TDS sensor | 1 |
| Buzzer | Electronic buzzer for alerts | 1 |
| Jumper Wires | Electrical connections | 5 |

### Component Description

**1. TDS Sensor**

Measures the electrical properties of water to estimate Total Dissolved Solids concentration.

**2. ESP32 Microcontroller**

Acts as the main controller. It processes sensor readings, performs TDS calculations and communicates with cloud platforms through Wi-Fi.

**3. Buzzer**

Provides an audible warning when the measured TDS value exceeds the configured threshold.

**4. Jumper Wires**

Establish electrical connections between the sensor, ESP32 and buzzer.

---

## 💻 Software Stack

| Technology | Purpose |
|---|---|
| Arduino IDE | ESP32 programming environment |
| Embedded C/C++ | Firmware development |
| ESP32 Wi-Fi | Wireless internet connectivity |
| Blynk IoT | Real-time monitoring dashboard |
| Google Sheets | Cloud-based data logging |

---

## ⚙️ Working Principle

The system works through the following process:

**1. Sensor Measurement**

The TDS probe is placed in the water sample to measure its electrical properties.

**2. Analog Signal Processing**

The TDS module generates an analog voltage signal corresponding to the measured water properties.

**3. ESP32 Processing**

The ESP32 reads the analog signal using its ADC and processes the sensor readings.

**4. TDS Calculation**

The firmware applies the configured conversion formula to estimate TDS concentration in ppm.

**5. Threshold Checking**

The calculated TDS value is compared against the predefined threshold of 1000 ppm.

- If TDS > 1000 ppm: Buzzer is activated.
- Otherwise: High-TDS buzzer alert remains inactive.

**6. Cloud Communication**

The ESP32 connects to Wi-Fi and transmits the measured readings to the cloud.

**7. Monitoring and Logging**

- Blynk IoT provides real-time visualization.
- Google Sheets stores readings for historical analysis.

---

## 🚀 Installation & Setup

### 1. Install Arduino IDE

Download Arduino IDE:

https://www.arduino.cc/en/software

### 2. Configure ESP32

- Install ESP32 board support in Arduino IDE.
- Select the appropriate ESP32 development board.
- Select the correct COM port.

### 3. Hardware Assembly

- Connect the TDS sensor to the ESP32.
- Connect the buzzer to the configured GPIO pin.
- Verify power supply and ground connections.
- Ensure the sensor output voltage is compatible with the ESP32 ADC.

### 4. Configure Wi-Fi

Update your Wi-Fi credentials in the Arduino source code.

```cpp
#define WIFI_SSID "YOUR_WIFI_NAME"
#define WIFI_PASSWORD "YOUR_WIFI_PASSWORD"
```

### 5. Configure Blynk IoT

- Create an account on Blynk.
- Create an IoT template and device.
- Configure the required datastreams.
- Add your device authentication credentials to the firmware.

Blynk Platform: https://blynk.io/

### 6. Configure Google Sheets

- Create a Google Spreadsheet.
- Configure the ESP32-to-Google-Sheets integration.
- Set up the required data logging mechanism.

### 7. Upload Firmware

- Open the Arduino source code.
- Verify sensor and buzzer GPIO configurations.
- Update Wi-Fi and cloud credentials.
- Compile and upload the program to ESP32.

### 8. Verify the System

- Check sensor readings using Serial Monitor.
- Verify the Blynk dashboard.
- Check Google Sheets data logging.
- Test the buzzer threshold condition.

---

## 📊 Usage

After successful installation:

1. Power on the ESP32.
2. Ensure Wi-Fi connectivity is established.
3. Place the TDS probe in the water sample.
4. Observe the TDS readings on the Blynk dashboard.
5. Check historical readings in Google Sheets.
6. Monitor the buzzer alert when TDS exceeds the configured threshold.

### Example Data

| Time | TDS Reading | Status |
|---|---:|---|
| 10:00 AM | 250 ppm | Below threshold |
| 11:00 AM | 350 ppm | Below threshold |
| 12:00 PM | 450 ppm | Below threshold |
| 01:00 PM | 850 ppm | Below threshold |
| 02:00 PM | 1050 ppm | Threshold exceeded |

*Illustrative readings only, not actual experimental results.*

---

## 🧪 Calibration & Maintenance

- Calibrate the TDS sensor periodically using appropriate standard solutions.
- Follow the sensor manufacturer's calibration instructions.
- Clean the probe periodically to prevent deposits and measurement drift.
- Verify sensor connections and power supply.
- Check Wi-Fi connectivity and cloud data transmission.
- Validate readings against a calibrated reference TDS meter.

---

## 🛠️ Troubleshooting

| Problem | Possible Solution |
|---|---|
| No TDS readings | Check sensor wiring and power supply. |
| Incorrect TDS values | Verify calibration and ADC configuration. |
| ESP32 Wi-Fi connection failure | Check Wi-Fi credentials and signal strength. |
| Blynk dashboard not updating | Verify authentication token and datastream configuration. |
| Google Sheets not receiving data | Check cloud integration and communication settings. |
| Buzzer not working | Verify GPIO configuration and buzzer connections. |

---

## 🌍 Applications

- RO water purification plants.
- Industrial water treatment systems.
- Commercial water purification facilities.
- Smart water quality monitoring.
- Water management systems.

---

## 🔮 Future Enhancements

- **Multi-Parameter Monitoring:** Integrate pH, temperature and turbidity sensors.
- **Machine Learning:** Introduce predictive analysis for identifying abnormal water quality trends.
- **Solar Power Integration:** Use renewable energy for sustainable operation.
- **Multi-Plant Monitoring:** Extend monitoring capabilities to multiple RO plants.
- **Advanced Dashboard:** Develop a dedicated web-based monitoring interface.
- **Smart Notifications:** Implement configurable email, mobile and cloud alerts.

---

## 📄 License

This project is developed as an academic mini project.

A suitable open-source license, such as MIT, can be added after selecting the license for this repository.

---

### 📚 References

- [ESP32 Documentation](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/)
- [DFRobot](https://www.dfrobot.com/)
- [Arduino IDE](https://www.arduino.cc/en/software)
- [Blynk IoT](https://blynk.io/)
- [Google Sheets](https://www.google.com/sheets/about/)

---


