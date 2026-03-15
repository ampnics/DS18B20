# D18BS20 — DS18B20 Temperature Sensor Module



[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
![Hardware](https://img.shields.io/badge/Hardware-KiCad%209.0-blue)
![Version](https://img.shields.io/badge/Version-V0.0.1-red)
![Made in India](https://img.shields.io/badge/Engineered%20in-India-ff9933)

> An open-source, minimal DS18B20 1-Wire temperature sensor module with onboard pull-up resistor and decoupling capacitor — designed for the engineering community.

---

## 📺 Video & Course

| Resource | Link |
|---|---|
| 🎬 DS18B20 Temperature Sensor Design | [Watch on YouTube](https://youtu.be/5xwUL280BjY) |
| 📚 Hardware Module Design — Full Playlist | [Watch Playlist](https://youtube.com/playlist?list=PLxgq6Jtu7shSHcKxjR8DUTR9fcr9KYakO&si=6mWbozdvvU1mXMRr) |

---


## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Schematic](#-schematic)
- [Hardware Specifications](#-hardware-specifications)
- [Pin Description](#-pin-description)
- [Repository Structure](#-repository-structure)
- [Getting Started](#-getting-started)
- [Usage Example](#-usage-example)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🔍 Overview

The **D18BS20** is a minimal, open-source breakout module for the **DS18B20 1-Wire digital temperature sensor**. It includes an onboard **4.7KΩ pull-up resistor** on the data line and a **100nF decoupling capacitor** on the power supply — making it ready to plug directly into any microcontroller without additional external components.

Designed in **KiCad 9.0.1** as part of the *Hardware Module Design* series on YouTube.

---

## ✨ Features

- ✅ DS18B20 1-Wire digital temperature sensor
- ✅ Onboard 4.7KΩ pull-up resistor on DQ line
- ✅ Onboard 100nF decoupling capacitor on VDD
- ✅ 3-pin connector (SIG, GND, VDD) for easy interfacing
- ✅ Compatible with 3.3V and 5V systems
- ✅ Temperature range: -55°C to +125°C
- ✅ ±0.5°C accuracy (-10°C to +85°C)
- ✅ Compact, minimal design
- ✅ Fully open-source — KiCad files included

---

## 📐 Schematic

```
VDD ──┬──── R1 (4K7) ────┬──── J1 Pin 1 (SIG)
      │                  │
      C1 (100nF)         └──── DS18B20 DQ (Pin 2)
      │
     GND ──────────────────── DS18B20 GND (Pin 1)
                               DS18B20 VDD (Pin 3) ── VDD

J1 Connector (Conn_01x03):
  Pin 1 → SIG (DQ Data Line)
  Pin 2 → GND
  Pin 3 → VDD
```

---

## 🔧 Hardware Specifications

| Parameter | Details |
|---|---|
| Sensor | DS18B20 |
| Communication | 1-Wire protocol |
| Supply Voltage | 3.0V – 5.5V |
| Temperature Range | -55°C to +125°C |
| Accuracy | ±0.5°C (-10°C to +85°C) |
| Resolution | 9 to 12-bit (configurable) |
| Pull-up Resistor | 4.7KΩ on DQ line |
| Decoupling Cap | 100nF on VDD |
| Connector | 3-pin 2.54mm pitch header |
| PCB Tool | KiCad 9.0.1 |
| Board Revision | V0.0.1 |

---

## 📌 Pin Description

| Pin | Label | Description |
|---|---|---|
| 1 | SIG | 1-Wire data line (DQ) — connect to MCU GPIO |
| 2 | GND | Ground |
| 3 | VDD | Power supply 3.3V or 5V |

---

## 🚀 Getting Started

### Prerequisites
- [KiCad 9.0.1](https://www.kicad.org/) — to open schematic and PCB files

### Clone the Repository
```bash
git clone https://github.com/ampnics/D18BS20.git
cd D18BS20
```

### Open in KiCad
1. Open KiCad
2. Click **"Open Project"**
3. Select `D18BS20.kicad_pro`

---

## 💻 Usage Example

### Arduino / ESP32

```cpp
#include <OneWire.h>
#include <DallasTemperature.h>

#define SIG_PIN 4  // Connect SIG pin of module to GPIO4

OneWire oneWire(SIG_PIN);
DallasTemperature sensors(&oneWire);

void setup() {
  Serial.begin(115200);
  sensors.begin();
}

void loop() {
  sensors.requestTemperatures();
  float tempC = sensors.getTempCByIndex(0);
  Serial.print("Temperature: ");
  Serial.print(tempC);
  Serial.println(" °C");
  delay(1000);
}
```

### Required Libraries
```
OneWire           → by Paul Stoffregen
DallasTemperature → by Miles Burton
```
Install via **Arduino IDE → Library Manager**

---

## 🏭 Fabrication

Gerber files are available in the `fab/` folder.

| Parameter | Value |
|---|---|
| Layers | 2 |
| Board Thickness | 1.6mm |
| Copper Weight | 1oz |
| Min Trace Width | 0.2mm |
| Surface Finish | HASL / ENIG |

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "hw: your change"`
4. Push: `git push origin feature/your-feature`
5. Open a **Pull Request**

---

## 📄 License

This project is licensed under the **MIT License**.

You are free to use, modify, and distribute this design for personal and commercial purposes with attribution.

---

## 👨‍💻 Designed By

**Md Ammar Maniyar** — [Ampnics](https://github.com/ampnics)

*Engineered in India 🇮🇳*

---

## ⭐ Support the Project

- ⭐ **Star** this repository
- 📺 **Subscribe** to the [YouTube Channel](https://youtube.com/playlist?list=PLxgq6Jtu7shSHcKxjR8DUTR9fcr9KYakO&si=6mWbozdvvU1mXMRr)
- 🍴 **Fork** and contribute back
