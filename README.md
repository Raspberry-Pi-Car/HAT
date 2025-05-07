# HAT
A custom PCB for adding sensors and hardware interfacing

## I2C
| Device    | Usage | Documentation | 
| -------- | ------- |------- | 
| INA260  | Battery monitor. Voltage, current and power reader  | [INA260 datasheet](https://www.ti.com/lit/ds/symlink/ina260.pdfP)|
| ICM-20948 | 9-DoF Interial Measurement Unit (Accelerometer, Gyroscope, and Magnetometer)   | [9-DoF IMU Datasheet](https://invensense.tdk.com/wp-content/uploads/2016/06/DS-000189-ICM-20948-v1.3.pdf)|
| PCA9685BS,118    | 16-Channel, 12-bit PWM Driver   | [PWM Driver Datasheet](https://www.nxp.com/docs/en/data-sheet/PCA9685.pdf) |


## SPI
| Device    | Usage | Documentation | 
| -------- | ------- |------- | 
| MCP-3008  | Analog to digital converter | [MCP 3008 Datasheet](https://cdn-shop.adafruit.com/datasheets/MCP3008.pdf) |


## Connected GPIO pins

| Device | GPIO / Pin |
| -------- | -------- |
| Ultrasonic Trigger | GPIO21 / Pin 40 |
| Ultrasonic Echo | GPIO20 / Pin 38 |
| H-Drive nFault | GPIO26 / Pin 37 |
| Switch | GPIO19 / Pin 35 |




## 2x20 Pin Header (GPIO)

| PIN #    | Usage | 
| -------- | ------- | 
| 1 |   Raspberry Pi 3.3V | 
| 2 |   Raspberry Pi 5V | 
| 3 |   I2C Data Line 1 (See I2C Devices)   | 
| 4 |   Raspberry Pi 5V | 
| 5 |   GPOIO 03:I2C Clock Line 1 (See I2C Devices)  | 
| 6 |   Raspberry Pi GND  | 
| 7 |   GPIO 4: GPCLCK  | 
| 8 |   GPIO 14: UART TX (Transmit Data)  | 
| 9 |   Raspberry Pi GND  | 
| 10 |  GPIO 15: UART RX (Receive Data)  | 
| 11 |  GPIO 17:Alert pin for INA260. Programmable Pin for detecting under/over voltage/current   | 
| 12 |  GPIO 18: PWM0  | 
| 13 |  GPIO 27: Unused  | 
| 14 |  Raspberry Pi GND  | 
| 15 |  GPIO 22: Unused   | 
| 16 |  GPIO 23: Unused | 
| 17 |  Raspberry Pi 3.3V   | 
| 18 |  GPIO 24: Unused   | 
| 19 |  GPIO 10: Master Out Slave In (MOSI) for MCP3008 and added SPI devices   | 
| 20 |  Raspberry Pi GND   | 
| 21 |  GPOIO 09: Master Input Slave Output (MISO) for MCP3008 and added SPI devices   | 
| 22 |  GPIO 25: Unused   | 
| 23 |  GPIO 11: Serial Clock (SCLK) for MCP3008 and added SPI devices   | 
| 24 |  GPIO 08: Chip Enable 0 (SPI0 CE0) for MCP3008 and added SPI devices   | 
| 25 |  Raspberry Pi GND   | 
| 26 |  GPIO 07: Chip Enable 1 (SPI0 CE1)  | 
| 27 |  GPIO 00: I2C Data Line 0 (no I2C devices using currently)  | 
| 28 |  GPIO 01: I2C Clock Line 0 (no I2C devices using currently)   | 
| 29 |  GPOIO 05: Unused   | 
| 30 |  Raspberry Pi GND    | 
| 31 |  GPIO 06: Unused   | 
| 32 |  GPIO 12: PWM0   | 
| 33 |  GPIO 13: PWM1   | 
| 34 |  Raspberry Pi Ground   | 
| 35 |  GPIO 19: GPIO Switch    | 
| 36 |  GPIO16: Unused   | 
| 37 |  GPOIO 36: H Drive Fault detection  | 
| 38 |  GPIO 20: UltraSonic Sensor Trigger  | 
| 39 |  Raspberry Pi GND   | 
| 40 |  GPIO 21: UltraSonic Sensor Echo | 





