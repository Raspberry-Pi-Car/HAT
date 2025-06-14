# HAT
A custom PCB for adding sensors and hardware interfacing

# V4

## Connected Devices / GPIO Pins
### I2C
| Device    | Usage | Documentation | 
| -------- | ------- |------- | 
| ICM-20948 | 9-DoF Interial Measurement Unit (Accelerometer, Gyroscope, and Magnetometer)   | [9-DoF IMU Datasheet](https://invensense.tdk.com/wp-content/uploads/2016/06/DS-000189-ICM-20948-v1.3.pdf)|
| PCA9685BS,118    | 16-Channel, 12-bit PWM Driver   | [PWM Driver Datasheet](https://www.nxp.com/docs/en/data-sheet/PCA9685.pdf) |


### SPI
| Device    | Usage | Documentation | 
| -------- | ------- |------- | 
| MCP-3008  | Analog to digital converter | [MCP 3008 Datasheet](https://cdn-shop.adafruit.com/datasheets/MCP3008.pdf) |


## Connected GPIO pins

| Device | GPIO / Pin |
| -------- | -------- |
| Ultrasonic Trigger | GPIO22 / Pin 15 |
| Ultrasonic Echo | GPIO23 / Pin 16 |
| Switch | GPIO26 / Pin 37 |


## Device and Connector Description

Most connectors are JST PH, 40-pin to Raspberry Pi is a female 2x20 header. Long pins are optional for possible future expansion but are not necessary, an extended standard female GPIO interface can be used. 

On the JST connectors, pin 1 is closest to the dot or with the soldered tabs facing up, is on the right side.

Information below may be repetitive, designed to focus on either the connector view or the device view. 

#### Battery
| Pin | Connection | Description |
| ------- | ------ | ------ |
| 1 | Battery (+) | Connected to main power switch (next to connector) |
| 2 | Battery (-) | Ground for PCB (GND) |

#### Motor A
| Pin | Connection | Description |
| ------- | ------ | ------ |
| 1 | Motor Controller AOUT1 | (A-) side |
| 2 | Motor Controller AOUT2 | (A+) side |

#### Motor B
| Pin | Connection | Description |
| ------- | ------ | ------ |
| 1 | Motor Controller BOUT2 | (B+) side |
| 2 | Motor Controller BOUT1 | (B-) side |

#### AD0/1 POT
| Pin | Connection | Description |
| ------- | ------ | ------ |
| 1 | +5V | Power |
| 2 | AD0 | Voltage divider (ground side) with POT0 |
| 3 | AD1 | Voltage divider (ground side) with POT1 |
| 4 | GND | Ground |

#### AD2/3
| Pin | Connection | Description |
| ------- | ------ | ------ |
| 1 | +5V | Power |
| 2 | AD2 | For motor encoder |
| 3 | AD3 | For motor encoder |
| 4 | GND | Ground |

#### AD4/5
| Pin | Connection | Description |
| ------- | ------ | ------ |
| 1 | +5V | Power |
| 2 | AD4 | For motor encoder |
| 3 | AD5 | For motor encoder |
| 4 | GND | Ground |

#### Ultrasonic
| Pin | Connection | Description |
| ------- | ------ | ------ |
| 1 | +5V | Power |
| 2 | GPIO22 / Pin 15 | Trigger pin for the ultrasonic Sensor |
| 3 | GPIO23 / Pin 16 | Echo pin for ultrasonic Sensor (though a 2/3 voltage divider)
| 4 | GND | Ground |

#### I2C
| Pin | Connection | Description |
| ------- | ------ | ------ |
| 1 | +5V | Power |
| 2 | GPIO2 SDA | SDA I2C line 1 |
| 3 | GPIO3 SCL | SCL I2C line 1 |
| 4 | GND | Ground |

### Motor Controller

The motor controller (DRV8411) can drive up to two brushed dc motors at up to 2A each. The inputs and controls are described below. The direction, forward and reverse, are relative to the motor do not necessarily mean the direction of motion of the vehicle.

| Connector | Connection |
| ------ | ------- | 
| JST MotorA | AOUT1 [Pin 2] and AOUT2 [Pin 1] |
| JST MotorB | BOUT1 [Pin 2] and BOUT2 [Pin 1] |

| PCA 9685 Channel | Motor Controller input | Motor Controller Out | Controller Behavior |
| ------ | ------ | ------ | 
| 12 |  AIN1  | AOUT1 | A reverse (A- to A+) |
| 13 |  AIN2  | AOUT2 | A forward (A+ to A-) |
| 14 |  BIN2  | BOUT2 | B reverse (B- to B+) |
| 15 |  BIN1  | BOUT1 | B forward (B+ to B-) |

The motor controller works by driving the motor in the direction that has the high signal. If multiple inputs are enables at the same time the motor controller will appear to take the difference of the two signals but will draw more power.

| IN1 | IN2 | Behavior |
| ----- | ------ | ------ |
| LOW | LOW | High Z / Coast |
| HIGH | LOW | OUT1 -> OUT2 (Forward) |
| LOW | HIGH | OUT2 -> OUT2 (Reverse) |
| HIGH | HIGH | Brake |

### AD Converter


| AD input | Usage |
| ------ | ------ |
| 0 | Voltage divider (ground side) with POT0 |
| 1 | Voltage divider (ground side) with POT1 |
| 2 | Pin 2 (left middle) on connector AD2/3  for motor encoder |
| 3 | Pin 3 (right middle) on connector AD2/3 for motor encoder |
| 4 | Pin 2 (left middle) on connector AD4/5  for motor encoder |
| 5 | Pin 3 (right middle) on connector AD4/5 for motor encoder |
| 6 | Not connected |
| 7 | Not connected |


### IMU
The ICM20498 is used as the Inertial Movement Unit on board. It has 9-way capability allowing for x, y, and z-axis capture of Acceleration, G-Force, and Magnetic Headings. This device communicates view the I2C bus and has no other external connections. 



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





