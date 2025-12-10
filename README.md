🎮 Tuni Boy — A Tunisian Open-Source Retro Gaming Console

Tuni Boy is a Tunisian-designed handheld gaming console created to help makers, students, and developers discover a mixed world of electronics, embedded programming, and retro gaming.
It combines a powerful ESP32-S3 microcontroller with a custom multi-layer PCB, a bright SPI TFT display, SD-card storage, physical buttons, audio amplifier, and a full battery-powered power system.

The goal of Tuni Boy is simple:
👉 Have fun, learn electronics, and build your own games.

![Tuni Boy](https://github.com/bejaouihamza/tuni_boy/blob/main/Capture%20d'%C3%A9cran%202025-12-10%20084328.png)

🧩 1. Schematic Overview — Main Parts & Subsystems

The schematic (from tuni.Boy.pdf) is built around five main sections:

1) The Brain — ESP32-S3 WROOM-1 Module

This is the main microcontroller, providing:

Dual-core LX7 CPU

Built-in WiFi + USB

SPI, I²C, UART

Enough GPIO for display, SD card, audio, and buttons

Low power consumption

It drives all peripherals of the console:

SPI TFT screen

an encoder

SD card

Buttons


![schematic](https://github.com/bejaouihamza/tuni_boy/blob/main/image.png)
(https://github.com/bejaouihamza/tuni_boy/blob/main/tuni.Boy.pdf)

2) Display System — SPI TFT LCD

Your screen uses SPI and connects to the ESP32-S3 as follows:

TFT Signal	ESP32-S3 GPIO
CS	GPIO10
DC	GPIO2
RESET	GPIO9
SCK	GPIO4
MOSI	GPIO6
MISO	GPIO5
LED/LITE	3.3V or PWM

The TFT uses a standard controller such as ST7789/ILI9341, ideal for retro games (8-bit palettes, sprites, tilemaps, etc.).

![pcb](https://github.com/bejaouihamza/tuni_boy/blob/main/Capture%20d'%C3%A9cran%202025-12-10%20084312.png?raw=true)


3) Storage System — Micro SD Card (SPI Mode)

The SD card allows:

storing games

storing sprites/images

audio files

save data

Connections:

SD Signal	ESP32-S3 GPIO
CS	GPIO3
SCK	GPIO4
MOSI	GPIO6
MISO	GPIO5
VCC/GND	3.3V/GND

It shares the SPI bus with the TFT screen (standard practice).

Audio amplifier

Power management signals


4) Audio System — PAM8302 Amplifier

The PAM8302 is a class-D amplifier powering a small speaker.

It takes audio from the ESP32-S3:

Possible sources:

PWM audio

I2S external DAC

Built-in ESP32-S3 digital audio output

Connections include:

IN+ / IN− = audio input

VDD = 5V or 3.3V

OUT+ / OUT− = speaker

Perfect for retro chiptunes, beeps, and game sound effects.
![](https://github.com/bejaouihamza/tuni_boy/blob/main/Capture%20d'%C3%A9cran%202025-12-10%20084341.png?raw=true)
