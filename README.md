# ATmega328P Arduino Nano Clone — Custom MCU PCB Design

> A fully custom Arduino Nano-compatible microcontroller board designed from scratch in KiCad. Implements the ATmega328P with USB-to-serial programming, onboard 5V/3.3V regulation, and a compact 2-layer layout — production-ready and Gerber-verified.

---

## Overview

This project is a **ground-up recreation of the Arduino Nano form factor** using the ATmega328P microcontroller. Rather than using a pre-made module, the entire hardware stack was designed from scratch: oscillator circuit, decoupling strategy, USB-to-serial bridge for bootloader programming, voltage regulation, and pin breakout — all laid out in a compact 2-layer PCB.

This project demonstrates the ability to design real microcontroller hardware — the kind of work needed for custom embedded products where off-the-shelf dev boards aren't suitable.

---

## Specifications

| Parameter          | Value                              |
|--------------------|------------------------------------|
| MCU                | ATmega328P-AU (TQFP-32)            |
| Clock              | 16 MHz external crystal            |
| USB Interface      | CH340G USB-to-Serial bridge        |
| Supply Voltage     | 5V via USB                         |
| Onboard Regulation | AMS1117-3.3 (3.3V LDO)            |
| I/O Voltage        | 5V logic                           |
| GPIO Pins          | 22 (14 digital, 8 analog)          |
| Programming        | USB (bootloader) / ICSP header     |
| PCB Layers         | 2                                  |
| Board Status       | Design complete, DRC passed        |
| Tool               | KiCad                              |

---

## Design Highlights

### Full ATmega328P Bring-Up Circuit
Includes all essential support circuitry: 16 MHz crystal with load capacitors, AVCC filtering with a ferrite bead and bulk capacitor, 100nF decoupling caps on all VCC/GND pins, and a proper reset circuit with pull-up resistor and filter capacitor.

### USB-to-Serial Programming
The CH340G bridge handles USB communication and auto-reset for bootloader programming, matching the Arduino Nano behaviour exactly. DTR line connected through a 100nF capacitor to the MCU reset pin for reliable auto-reset during upload.

### Onboard 3.3V Regulation
AMS1117-3.3 LDO provides a clean 3.3V rail for sensors and peripherals that require it, with input and output decoupling capacitors for stability.

### Compact 2-Layer Layout
All components fit within a Nano-compatible footprint on a 2-layer board. Power and ground planes on bottom layer, signals routed cleanly on top. SMD components used throughout for compact placement.

### DRC Passed
Full design rule check with zero errors. Trace widths verified for current capacity, clearances verified for standard PCB fab tolerances.

---

## Repository Structure

```
project2-atmega328p-nano/
├── schematic/
│   └── atmega328p_nano.kicad_sch
├── pcb/
│   └── atmega328p_nano.kicad_pcb
├── gerbers/
│   ├── atmega328p_nano.GTL
│   ├── atmega328p_nano.GBL
│   ├── atmega328p_nano.GTO
│   ├── atmega328p_nano.GTS
│   ├── atmega328p_nano.GBS
│   └── atmega328p_nano.DRL
├── bom/
│   └── bom.csv
└── README.md
```

---

## Bill of Materials (Key Components)

| Ref      | Component           | Part Number       | Package    |
|----------|---------------------|-------------------|------------|
| U1       | Microcontroller     | ATmega328P-AU     | TQFP-32    |
| U2       | USB-Serial Bridge   | CH340G            | SOP-16     |
| U3       | 3.3V LDO Regulator  | AMS1117-3.3       | SOT-223    |
| Y1       | Crystal Oscillator  | 16 MHz            | HC-49S     |
| C1, C2   | Crystal Load Caps   | 22pF              | 0402       |
| C3–C10   | Decoupling Caps     | 100nF             | 0402       |
| R1       | Reset Pull-up       | 10kΩ              | 0402       |
| J1       | USB Connector       | Mini-USB Female   | SMD        |
| J2, J3   | Pin Headers         | 2.54mm, 15-pin    | Through-hole |
| J4       | ICSP Header         | 2×3, 2.54mm       | Through-hole |

---

## Schematic Sections

1. **Power input & regulation** — USB 5V in → AMS1117-3.3 → 3.3V rail
2. **USB-to-Serial** — CH340G with crystal, decoupling, and DTR auto-reset
3. **ATmega328P core** — MCU with crystal, decoupling, AVCC filter, reset
4. **I/O breakout** — all GPIO, analog, and power pins exposed on 2.54mm headers
5. **ICSP header** — for bootloader burning and direct ISP programming

---

## Skills Demonstrated

- ATmega328P hardware bring-up and support circuit design
- USB-to-serial bridge integration (CH340G)
- LDO regulator selection and decoupling strategy
- SMD component placement and 2-layer PCB routing
- ICSP and bootloader programming interface design
- KiCad DRC and Gerber export

---

## Project Status

| Stage            | Status       |
|------------------|--------------|
| Schematic        | ✅ Complete  |
| PCB Layout       | ✅ Complete  |
| DRC              | ✅ Passed    |
| Gerbers Exported | ✅ Ready     |
| Fabricated       | ⬜ Not yet   |
| Tested           | ⬜ Not yet   |

---

## About the Designer

Self-taught PCB designer specializing in KiCad — IoT, embedded systems, and industrial control boards.
Available for freelance PCB design work: schematic capture, layout, DRC review, and Gerber preparation.

🔗 GitHub: [Abhi90808]
📧 [kvabhishek908@gmail.com]
