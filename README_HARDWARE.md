 Hardware for the Personal Alert Device 
Overview

This document outlines the hardware components, schematics, power setup, and connection instructions for the PAD, a wearable designed to detect falls and monitor elderly users' health metrics.

 Schematics 

- ![Wiring Diagram](images/Screenshot%202025-04-18%20132853.png)

- ![Power system](images/Screenshot%202025-04-18%20141745.png)


PCB Highlights:
- 2-layer custom PCB
- Mount points for Seeed Studio XIAO nRF52840 Sense
- Pads for sensors and battery connector
- Integrated power routing for wireless charging module

---

Hardware Components

| Component                        | Part Number/Model              | Vendor        | Used For                                 |
|----------------------------------|--------------------------------|---------------|------------------------------------------|
| Microcontroller                  | Seeed Studio XIAO nRF52840 Sense | Seeed Studio | BLE communication, onboard IMU and mic   |
| Heart Rate Sensor                | MAX30102                       | Aliexpress    | Pulse and SpO2 monitoring via I2C        |
| Temperature Sensor               | MLX90614                       | Aliexpress    | Body temperature monitoring via I2C      |
| Push Button                      | Generic                        | LCSC          | Manual emergency alert                   |
| Wireless Charging Receiver       | SW-WC-RX                       | Amazon        | 5V power input through copper coil       |
| Wireless Charging Transmitter    | SW-WC-TX                       | Amazon        | 5V USB-powered transmission               |
| Lithium Battery                  | 3.7V 1100mAh LiPo              | Amazon        | Main power supply                        |
| LEDs (Red, Yellow, Green)        | 0805 SMD + 330Ω resistors      | LCSC          | Battery and alert status indicators      |
| **Buzzer**                       | Passive Buzzer (SMD)           | LCSC          | Audible emergency alert                  |

 See full () for orderable parts.

---

Power Requirements

| Source             | Voltage | Current | Notes                               |
|-------------------|---------|---------|-------------------------------------|
| Lithium Battery   | 3.7V    | 300mA | Powers all onboard systems          |
| Wireless Charging | 5V      | 300mA  | Charges battery via receiver coil   |
| Microcontroller   | 3.3V    | 50mA   | Supplied from battery regulator     |

---

Assembly Photos



- ![PCB Top View](images/Screenshot%202025-03-27%20231332.png)
- ![Wiring Diagram](../images/wiring_diagram.png)

---

Wiring and Sensor Connections

MAX30102 heart rate sensor 
- SCL: D4 (GPIO pin on XIAO)
- SDA: D5
- VCC: 3.3V
- GND: GND

Push Button
- One terminal to D2
- Other terminal to GND

Wireless Charging Receiver
- 5V output: to the positive battery terminal
- GND to the battery ground

LEDs
- Red: Positive terminal to D10, and negative terminal to 330Ω → GND
- Yellow: Positive terminal to D3, and negative terminal to 330Ω → GND
- Green: Positive terminal to D1, and negative terminal to 330Ω → GND

Setup Instructions

1.Solder the positive terminal of the battery to the postive terminal of the receiver module and solder the negative terminal of the battery to the negative terminal of the receiver module
2. Solder the positive terminal of the battery to the BAT+ of the microconterller and the negative terminal of the battery to the BAT- of the microconterller
3. Solder all buzzer, LEDS, push-button switch, and microcontroller on the PCB
4. Connect the heart rate sensor and the thirmistor per wiring table
5. 3D-printed enclosure the enclourser for the device and the powering system

 Reference Documents

- [MAX30102 Datasheet (PDF)](https://datasheets.maximintegrated.com/en/ds/MAX30102.pdf)
- [Transmiter and reciver module page](https://www.amazon.com/dp/B08CVGYDJP?ref=ppx_pop_mob_ap_share)
- [Battery Page](https://www.amazon.com/dp/B0D7MC714N?ref=ppx_pop_mob_ap_share)

---


