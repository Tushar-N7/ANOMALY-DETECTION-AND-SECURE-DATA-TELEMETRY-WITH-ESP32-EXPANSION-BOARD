# **ESP32 Expansion & Stability Evaluation Board**

## **📌 Overview**

The **ESP32 Expansion & Stability Evaluation Board** is a custom-designed daughterboard developed to analyze, improve, and validate the stability of the ESP32 microcontroller under different electrical, load, and environmental conditions.

This board focuses on ensuring **stable ADC readings**, **clean power delivery**, **controlled operating modes**, and **cloud-connected telemetry** for ML-based monitoring.

The entire system simulates sensor readings, offers 7 operating modes, monitors ESP32 voltage behavior, evaluates decoupling performance, and streams data to a cloud ML model and dashboard.



## **📂 Repository Structure**

```
ESP32-Expansion-Board/
│
├── firmware/
│   ├── esp32_main.ino
│   ├── modes.h
│   ├── dummy_sensors.h
│   ├── config.h
│   └── README.md
│
├── hardware/
│   ├── schematics.pdf
│   ├── pcb_layout.png
│   ├── bill_of_materials.csv
│   └── board_description.md
│
├── cloud/
│   ├── data_format.md
│   ├── ml_model_notes.md
│   └── dashboard_api.md
│
├── documentation/
│   ├── abstract.md
│   ├── background_study.md
│   ├── problem_statement.md
│   ├── scope.md
│   ├── gaps.md
│   └── conclusion.md
│
└── README.md
```


## **🎯 Key Features**

### **1️⃣ Microcontroller Stability Focus**

* Power-line noise rejection
* Bulk + decoupling capacitor analysis
* Brownout, reset, regulator behavior testing
* 4.7V–5V VIN tolerance experiments

### **2️⃣ 7 Operating Modes**

| Mode No | Mode Name        | Function                        |
| ------- | ---------------- | ------------------------------- |
| 0       | Normal Mode      | Regular WiFi + sensors + 160MHz |
| 1       | Full Performance | CPU 240MHz, max sampling        |
| 2       | Low Power        | WiFi OFF, 80MHz                 |
| 3       | Maintenance      | System info, diagnostics        |
| 4       | Test Mode        | High-speed dummy sensors        |
| 5       | Safe Mode        | Minimal operations, safety      |
| 6       | Calibration Mode | ADC stability tests             |


## **📡 Cloud Integration**

* Sensor + mode data sent to cloud
* ML model predicts ESP32 stability
* Dashboard visualizes voltage, resets, and noise patterns


## **⚙️ Hardware Components**

* ESP32 WROOM module
* 5V → 3.3V LDO regulator
* 0.1µF + 10µF decoupling capacitors
* 1000µF bulk capacitor for VIN smoothing
* LEDs, switches, buttons
* Test points for ADC noise analysis
* Female headers for daughterboard mounting


## **📄 Project Documentation**

This repo includes full literature-style documentation:

* **Abstract**
* **Background of Study** (5+ paragraphs)
* **Identified Gaps / Grey Areas**
* **Problem Statement** (7 long paragraphs)
* **Scope of Work**
* **Conclusion**


## **🧪 Experiments Performed**

* ESP32 VIN voltage sweep from 4.7–5.0V
* ADC noise comparison with/without capacitors
* Reset frequency analysis
* Mode-wise power consumption test
* Telemetry reliability test


## **📊 Example Telemetry Packet**

```
{
  "mode": 4,
  "voltage": 4.92,
  "adc_value": 1734,
  "cpu_freq": 240,
  "uptime": 30291,
  "temperature": 34.7
}
```


## **🛠️ Dummy Sensor Simulation**

The firmware generates:

* Random temperature
* Random vibration
* Random current values
* ADC stability indicators

Useful for cloud model testing.


## **🔧 How to Use**

### **1. Flash Firmware**

Open firmware folder → upload `esp32_main.ino` using Arduino IDE or PlatformIO.

### **2. Power the Board**

Use:

* 5V USB
* External 5V through VIN
* Optionally test 4.7–5.0V ranges

### **3. View Serial Output**

Provides:

* ADC values
* Mode info
* Stability logs

### **4. Enable Cloud Upload**

Configure your WiFi and API keys in `config.h`.


## **📘 Applications**

* ESP32 stability testing
* Research projects
* Industrial sensor node testing
* Power supply noise analysis
* Cloud ML telemetry


## **🧠 Future Improvements**

* Real sensor integration
* Custom LDO comparison
* Thermal stability analysis
* ESP32 brownout ML prediction
* PCB v2 with differential ADC path


## **📜 License**

MIT License — free to use and modify.
