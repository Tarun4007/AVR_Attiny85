# HVSP-attiny85-fuse-config
# ATtiny85 HVSP: Unlock RESET Pin as GPIO 🧠⚡

This repository documents how to use **High Voltage Serial Programming (HVSP)** to configure the ATtiny85 microcontroller, specifically to:

✅ Disable the RESET pin  
✅ Use PB5 (pin 1) as a regular GPIO  
✅ Restore the RESET function when needed  
✅ Set custom fuse bits

---

## 🔧 What Is HVSP?

**HVSP (High Voltage Serial Programming)** is a method used to program ATtiny microcontrollers when the RESET pin is disabled or fuse settings prevent ISP.

- Requires 12V on RESET pin
- Useful to recover or repurpose chips

---

## ⚙️ Goals of This Repo

- Convert ATtiny85 pin 1 (RESET) to GPIO
- Explain required fuse settings
- Provide HVSP programmer setup using Arduino Uno
- Enable easy reconfiguration of ATtiny85 fuses

---

## 🔩 Fuse Settings

| Function | Value | Description |
|----------|-------|-------------|
| `HFUSE`  | 0x5F  | Disables RESET to enable PB5 as GPIO |
| `LFUSE`  | 0x62  | Default (internal 8 MHz RC oscillator) |
| `EFUSE`  | 0xFF  | Default |

Generate fuses using [AVR Fuse Calculator](https://www.engbedded.com/fusecalc/)

---

## 🛠 HVSP Setup (with Arduino Uno)

### 🧰 Requirements:
- Arduino Uno
- 12V power source (DC booster or external)
- ATtiny85 microcontroller
- Breadboard + jumper wires

### 🧑‍💻 Software:
- [ArduinoISP_HVSP by MCUdude](https://github.com/MCUdude/MiniCore/tree/master/extra/ArduinoISP_HVSP)
- Arduino IDE

### 📖 Steps:
1. Upload `ArduinoISP_HVSP` to Arduino Uno
2. Connect Arduino pins to ATtiny85 per schematic
3. Apply 12V to RESET via HVSP circuit
4. Burn fuses (as shown above)

> 🛑 **Warning**: You won’t be able to reprogram the ATtiny85 via ISP once RESET is disabled. You must use HVSP again to revert!

---
