# AVR Smart Environment Control System

This project implements a smart temperature and light control system using the ATmega microcontroller. The system reads temperature using an LM35 sensor and ambient light using an LDR. Based on the measurements, it automatically adjusts heater and cooler output using PWM and displays system states through LED indicators. The project also features a full LCD menu interface, password protection, and adjustable threshold settings.

---

## 🌡️ Features
- LM35 sensor for temperature measurement
- LDR sensor for ambient light intensity detection
- Automatic heater & cooler control using PWM
- Five temperature state indicator LEDs
- Light state indicator LED (Dark/Light)
- Interactive LCD menu system
- Adjustable thresholds (LL, L, H, HH)
- User login page with password authentication
- Navigation buttons: Enter, Back, Left, Right

---

## 🧭 Menu Structure
| Menu Item | Function |
|---------|----------|
| Set LL | Set Very Cold threshold |
| Set L | Set Cold threshold |
| Set H | Set Warm threshold |
| Set HH | Set Very Warm threshold |
| User Page | Shows real-time Temp & LDR values |

---

## 🔧 Hardware Connections
| Component | Pin |
|----------|----|
| LM35 | ADC0 (PC0) |
| LDR | ADC1 (PC1) |
| Heater (PWM) | PB1 (OC1A) |
| Cooler (PWM) | PB2 (OC1B) |
| LEDs | PD0–PD6 |
| Buttons | PC0–PC3 |
| LCD | Controlled via lcd.h library |

---

## 🧱 PWM & Control Logic
| Temperature | Action |
|------------|--------|
| ≤ LL | Heater Max |
| ≤ L | Heater Low |
| Between L & H | Both Off |
| ≥ H | Cooler Low |
| ≥ HH | Cooler Max |

---

## 🔐 User Login
- Default Username: `111`
- Default Password: `12345`
- Password entry appears before accessing User Page

---

## 🛠️ Dependencies
- AVR-GCC
- avr-libc
- lcd.h library (HD44780 type)
- USBasp or AVR ISP Programmer

---

## ▶️ Upload & Compile
```bash
avr-gcc -mmcu=atmega32 -Os main.c -o program.elf
avr-objcopy -O ihex program.elf program.hex
avrdude -c usbasp -p m32 -U flash:w:program.hex
