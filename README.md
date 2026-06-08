# C & AVR Assembly — University Coursework

[![C](https://img.shields.io/badge/C-bare--metal-00599C.svg?logo=c&logoColor=white)](https://en.cppreference.com/w/c)
[![AVR Assembly](https://img.shields.io/badge/AVR-Assembly-A41E22.svg?logo=arduino&logoColor=white)](https://www.microchip.com/wwwAppNotes/AppNotes.aspx?appnote=en591628)
[![ATmega328P](https://img.shields.io/badge/MCU-ATmega328P-555.svg)](https://www.microchip.com/en-us/product/ATmega328P)
[![Atmel Studio](https://img.shields.io/badge/Atmel%20Studio-IDE-1f6feb.svg)](https://www.microchip.com/en-us/tools-resources/archives/avr-sam-mcus)
[![Shell](https://img.shields.io/badge/Shell-toolchain-89E051.svg?logo=gnu-bash&logoColor=black)](https://www.gnu.org/software/bash/)

Embedded coursework from **Kristianstad University** and **Business Academy Aarhus** — bare-metal C, AVR assembly, and a (very early) hand-rolled compiler experiment. Everything targets the **ATmega328P**.

---

## What's in here

### Labs

| Folder | Focus |
|---|---|
| `Lab 1 Assembly` | First AVR assembly program |
| `Lab 2 Assembly` | Assembly tasks (Task5 etc.) |
| `Lab 2 timers buttons` | C — Timer interrupts + button debouncing |
| `Lab 3 PWM ADC UART LCD` | C — PWM, ADC, UART, LCD driver |
| `Lab 4 Project(LCD ADC UART BTN)` | Capstone — combine all peripherals into one project |

### Homework

`Homework Timers`, `Homework Toggling LEDs`

### Lectures (in-class demos)

`Lecture ADC and PWM`, `Lecture RGB lights` (WS2812 driver), `Lecture Servo`, `Lecture Timers`, `Lecture UART`

### Projects

`Project Servo 1`, `Project Servo 2`, `Project Servo 3 (Complete)` — servo control progression

### `c_programming_fundamentals/`

Pure C exercises: `lab1InC`, `lab2InC`, `lab3InC`, and an `Advent_of_code` solution.

### `custom_compiler_c/` 🛠 *(very early — just started)*

A from-scratch C-to-AVR-assembly compiler experiment. I started it to better understand how high-level code maps down to assembly — but it's nowhere near functional yet. Right now it's just the **skeleton**: hand-written `.asm` building blocks (`hello`, `printInt`, `printStrings`, `macros`, `test`), a `fileRead` input stub, and a `halalC.sh` driver script. No real frontend, no parser, no codegen — think of it as a learning sandbox that I plan to grow into something more.

---

## Stack

- **MCU** — ATmega328P @ 16 MHz
- **Languages** — C (with `avr-libc`) and AVR assembly
- **IDE** — Atmel Studio (each `GccApplication*` folder is its own project)
- **Toolchain** — `avr-gcc`, `avr-as`, `avr-objcopy`, `avrdude`

---

## Layout

```
c_assembly_uni/
├── Lab 1 Assembly/                   # first asm steps
├── Lab 2 Assembly/                   # asm tasks
├── Lab 2 timers buttons/             # C — timers + buttons
├── Lab 3 PWM ADC UART LCD/           # C — full peripheral stack
├── Lab 4 Project(LCD ADC UART BTN)/  # capstone
├── Homework Timers/
├── Homework Toggling LEDs/
├── Lecture ADC and PWM/
├── Lecture RGB lights/               # WS2812 driver
├── Lecture Servo/
├── Lecture Timers/
├── Lecture UART/
├── Project Servo 1..3 (Complete)/    # servo project progression
├── c_programming_fundamentals/       # plain C — labs + Advent of Code
└── custom_compiler_c/                # 🛠 very-early compiler experiment
    ├── halalC.sh                     # driver script
    ├── hello/ printInt/ printStrings/ macros/ test/   # asm building blocks
    └── fileRead/                     # input handling stub
```

---

## Build & flash (typical lab)

With **avr-gcc + avrdude**:

```bash
avr-gcc -mmcu=atmega328p -Os -DF_CPU=16000000UL main.c -o main.elf
avr-objcopy -O ihex main.elf main.hex
avrdude -p m328p -c arduino -P /dev/ttyUSB0 -b 115200 -U flash:w:main.hex
```

Or open the `GccApplication*` folder in **Atmel Studio** and hit Build / Program.

---

© Danielis Maizelis · Kristianstad University · Business Academy Aarhus
