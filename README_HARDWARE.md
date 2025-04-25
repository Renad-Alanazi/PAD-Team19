# Hardware for the Personal Alert Device (PAD)
Overview

This document outlines the hardware components, schematics, power setup, and connection instructions for the PAD, a wearable designed to detect falls and monitor elderly users' health metrics.

 Schematics & PCB

- **Schematic PDF**: [`PAD_Schematic.pdf`](../hardware/PAD_Schematic.pdf)
- **PCB Layout PDF**: [`PAD_PCB.pdf`](../hardware/PAD_PCB.pdf)
- **EasyEDA Files**: Included in `/hardware/` folder

PCB Highlights:
- 2-layer custom PCB
- Mount points for Seeed Studio XIAO nRF52840 Sense
- Pads for sensors and battery connector
- Integrated power routing for wireless charging module

---

Hardware Components

| Component                        | Part Number/Model        | Vendor           | Notes                               |
|----------------------------------|--------------------------|------------------|-------------------------------------|
| Microcontroller                  | Seeed Studio XIAO nRF52840 Sense | Seeed Studio     | BLE, IMU, Microphone onboard        |
| Heart Rate Sensor               | MAX30102                 | LCSC / Adafruit  | Pulse and SpO2 sensor via I2C       |
| Temperature Sensor              | MLX90614 (IR)            | LCSC / SparkFun  | Body temperature via I2C            |
| Push Button                     | Generic                  | Amazon/LCSC      | For manual emergency alerts         |
| Wireless Charging Receiver      | SW-WC-RX                 | Amazon           | 5V wireless receiver, copper coil   |
| Wireless Charging Transmitter   | SW-WC-TX                 | Amazon           | Connected to 5V USB power           |
| Lithium Battery                 | 3.7V 1100mAh LiPo        | MakerHawk/Amazon | With built-in protection board      |
| LEDs (Red, Yellow, Green)       | 0805 SMD + 330Ω resistors| LCSC             | Battery status indication           |

> 💡 See full [Bill of Materials (BOM)](../hardware/BOM_PAD.xlsx) for orderable parts.

---

Power Requirements

| Source             | Voltage | Current | Notes                               |
|-------------------|---------|---------|-------------------------------------|
| Lithium Battery   | 3.7V    | 1100mAh | Powers all onboard systems          |
| Wireless Charging | 5V      | ~500mA  | Charges battery via receiver coil   |
| Microcontroller   | 3.3V    | ~40mA   | Supplied from battery regulator     |

---

Assembly Photos

- ![PCB Top View](../images/pcb_top.jpg)
- ![PCB in Enclosure](../images/assembled_inside.jpg)
- ![Wiring Diagram](../images/wiring_diagram.png)

---

Wiring and Sensor Connections

### I2C Devices (MAX30102, MLX90614)
- **SCL**: D4 (GPIO pin on XIAO)
- **SDA**: D5
- **VCC**: 3.3V
- **GND**: GND

Push Button
- One terminal to **D2**
- Other terminal to **GND**

Wireless Charging Receiver
- **+5V output** to battery charger input
- **GND** to system GND

LEDs
- Red: D3 → 330Ω → GND
- Yellow: D2 (shared via switch logic)
- Green: D1 → 330Ω → GND

Setup Instructions

1. **Solder all SMD components and microcontroller**
2. **Connect sensors and LEDs as per wiring table**
3. **Place device in 3D-printed enclosure**
4. **Attach battery and test wireless charging**
5. **Power on and verify LED indicator behavior**
6. **Upload firmware via USB and verify BLE connection**



 Reference Documents

- [MAX30102 Datasheet (PDF)](https://datasheets.maximintegrated.com/en/ds/MAX30102.pdf)
- [MLX90614 Datasheet](https://www.melexis.com/-/media/files/documents/datasheets/mlx90614-datasheet-melexis.pdf)
- [XIAO nRF52840 Datasheet](https://files.seeedstudio.com/wiki/XIAO-BLE-Sense/resources/XIAO_BLE_nRF52840_Sense_v1.0.pdf)
- [Battery Product Page](https://www.amazon.com/dp/B08S6ZP5ZR)

---

## ✅ Final Notes

This document, along with the schematics and photos, provides all the necessary details to rebuild and maintain the PAD hardware. Make sure to review solder joints and component orientation before powering the device.

