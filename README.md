# 📘 PrecisionDAC — High-Performance Data-to-Analog Conversion Platform
### *ATxmega128A1U • DAC81408EVM • Industrial RS-232 Interface • Multi-Rail Power System*

---

## 🚀 Project Overview
**PrecisionDAC** is an industry-grade **Data-to-Analog Conversion (DAC) platform** built using:

- **ATxmega128A1U (100-pin)** microcontroller  
- **DAC81408EVM** (16-bit, 8-channel precision DAC)  
- **MAX3232** UART Transceiver (RS-232 ↔ TTL)  
- **DB-25 industrial connector interface**  
- **Isolated ±12V and 5V DC-DC converters**

Designed for **test equipment, control systems, industrial automation, and analog signal generation**, this project showcases embedded systems development, SPI driver design, mixed-signal understanding, and hardware–firmware integration.

---

## 🎯 Key Features
- 16-bit precision Data-to-Analog conversion  
- SPI driver for DAC81408  
- UART (RS-232 <→ TTL) communication via MAX3232  
- DB-25 industrial interface mapping  
- Multi-rail power system: 24V → ±12V → 5V  
- Modular firmware structure  
- Scalable design for multi-channel instrumentation  

---

## 🧩 Hardware Architecture

| Module | Part Number | Purpose |
|--------|-------------|---------|
| MCU | ATxmega128A1U | SPI control, UART communication, data processing |
| DAC Module | DAC81408EVM | 16-bit, 8-channel analog output |
| UART Transceiver | MAX3232 | RS-232 to TTL |
| Industrial Connector | DB-25 | Analog output interface |
| DC-DC Converters | ±12V & 5V modules | Power supply subsystem |

---

## 📡 Block Diagram
      +-----------------------------+
      |     ATxmega128A1U MCU       |
      |   (SPI + UART + GPIO)       |
      +---------------+-------------+
                      |
                      | SPI
                      v
            +------------------+
            |  DAC81408EVM     |
            | 16-bit, 8-ch DAC |
            +--+--+--+--+--+---+
               |  |  |  |  
               v  v  v  v  
          DB-25 Industrial Output

      UART (USART)
            |
            v
    +-------------------+
    |   MAX3232 IC      |
    | RS232 <-> TTL     |
    +---------+---------+
              |
            RS-232
              |
            PC/Host

 Power System:
 24V → ±12V → 5V → DAC + MCU


---

## 📁 Repository Structure
PrecisionDAC/  
│
├── firmware/  
│ ├── src/  
│ ├── include/  
│ └── Makefile  
│
├── hardware/  
│ ├── schematics/  
│ └── pcb/  
│
├── docs/  
│ ├── images/  
│ └── pinouts/  
│
├── LICENSE  
└── README.md  

---

## 🔧 Firmware Highlights
- SPI driver for DAC81408  
- UART handler for RS-232 communication  
- DAC channel initialization  
- Structured command interface  
- Lookup-table based waveform support  
- Watchdog and safety checks  

---

## 🧪 Test & Validation Tools
This project includes optional utilities:

- **serial_test.py** — Send digital values via UART  
- **calibration_helper.py** — Adjust offset/gain  
- **output_plotter.py** — Visualize DAC outputs  

---

## 📦 Build & Flash Instructions
### 1. Install AVR toolchain
- AVR-GCC  
- Atmel Studio  

### 2. Build
```bash
make
avrdude -c atmelice -p x128a1u -U flash:w:main.hex
