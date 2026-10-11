# ⭐ Starbie — An ESP32-C3 Electronic Pet

Starbie is a DIY electronic pet project built around the **Seeed Studio XIAO ESP32-C3**. It combines embedded systems, sensors, an OLED display, and interactive buttons to create a small electronic companion.

This repository contains my PCB design work as part of **Hack Club Half Life — Week 1: Design Your PCB**.

## 🖼️ PCB 3D Render

![Starbie PCB 3D Render](starbie-pcb-render.png)

*3D visualization of the Starbie PCB design.*

## 🚀 Project Features

- ESP32-C3 microcontroller for embedded control
- OLED display interface using I²C
- MPU6050 motion sensor interface
- DHT11 temperature and humidity sensor
- Two push buttons for user interaction
- Custom PCB layout designed in KiCad

## 🧰 Hardware Components

| Component | Purpose |
|---|---|
| Seeed Studio XIAO ESP32-C3 | Main microcontroller |
| OLED display | Visual output |
| MPU6050 | Motion and orientation sensing |
| DHT11 | Temperature and humidity sensing |
| Push buttons × 2 | User input |
| 10 kΩ resistor | DHT11 data-line pull-up, as configured in the schematic |
| Custom PCB | Connects all components |

## 🔌 Pin Connections

| Component | Signal | XIAO ESP32-C3 connection |
|---|---|---|
| Push button SW1 | GPIO2 | D2 |
| Push button SW2 | GPIO3 | D3 |
| DHT11 | Data | D1 |
| OLED | SCL | D4 |
| OLED | SDA | D5 |
| MPU6050 | SCL | D4 |
| MPU6050 | SDA | D5 |
| OLED / MPU6050 | Power | 3.3V and GND |

*Verify these connections against the final schematic before assembling the hardware.*

## 🛠️ Tools and Technologies

- **KiCad** — Schematic capture and PCB layout
- **ESP32-C3** — Embedded development
- **I²C** — Communication with the OLED and MPU6050
- **PCB Design** — Footprints, routing, and design-rule checking

## 📂 Repository Contents

```text
Starbie/
├── README.md
├── starbie-pcb-render.png
├── myfirstkicad.kicad_pro
├── myfirstkicad.kicad_sch
└── myfirstkicad.kicad_pcb
```

*The KiCad filenames above are examples. Replace them with your actual project filenames, and upload the corresponding files if you want to share the full design.*

<img width="2400" height="1792" alt="Gemini_Generated_Image_9kou9b9kou9b9kou" src="https://github.com/user-attachments/assets/821d481a-8276-42b0-9438-df4338a1c080" />

## 📈 Current Progress

- [x] Initial schematic and component selection
- [x] PCB placement and routing work
- [x] PCB 3D visualization
- [ ] Resolve remaining KiCad design-rule-check (DRC) errors
- [ ] Verify the final schematic and PCB
- [ ] Manufacture and assemble the PCB
- [ ] Test the hardware and firmware

## 🎯 Project Goal

To learn practical PCB design, embedded electronics, sensor integration, and microcontroller-based development by building an interactive electronic pet.

## 🙌 Acknowledgements

Inspired by the Starbie starter project by SharKingStudios and developed as part of my Hack Club Half Life learning journey.

- [Starbie Project Repository](https://github.com/SharKingStudios/Starbie)
- [KiCad](https://www.kicad.org/)
- [Hack Club Half Life](https://halflife.hackclub.com/)

---

**Made with curiosity and a passion for electronics.** ⚡
