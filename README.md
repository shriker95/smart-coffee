# Smart Coffee – Philips EP5400

ESPHome integration for the Philips EP5400 series coffee machine via D1 Mini (ESP8266).

## Hardware

- **Board:** Wemos D1 Mini (ESP8266)
- **PCB:** from [TillFleisch/ESPHome-Philips-Smart-Coffee](https://github.com/TillFleisch/ESPHome-Philips-Smart-Coffee)
- **UART wiring:**
  - Mainboard: RX=GPIO3, TX=GPIO1 (UART0)
  - Display: RX=GPIO13, TX=GPIO15 (Software UART)

## How it works

The D1 Mini sits between the display and the mainboard, transparently bridging both UART buses.
It parses incoming status packets (`0xB0`) from the mainboard and injects drink commands
(`0x93` / `0x90` / `0x91`) with a live-synced counter and recalculated CRC32.

## Features

- Status sensors: water, drip tray, grounds container, beans, brew state, system state
- Buttons: Kaffee 150ml, Cappuccino Max, Cappuccino Min, power off
- Secrets template: `secrets.yaml.example`

## Status

> **Note:** Currently only the status sensors appear to work reliably. The drink buttons (counter sync + CRC32) are implemented but not yet fully tested.

## Setup

1. Copy `secrets.yaml.example` → `secrets.yaml` and fill in credentials
2. Flash `philips_5400_d1mini.yaml` via ESPHome

## References

- [DivanX10/ESP-Philips-5400-Coffee-Machine](https://github.com/DivanX10/ESP-Philips-5400-Coffee-Machine) — protocol documentation and ESP32 component
- [TillFleisch/ESPHome-Philips-Smart-Coffee](https://github.com/TillFleisch/ESPHome-Philips-Smart-Coffee) — PCB design
