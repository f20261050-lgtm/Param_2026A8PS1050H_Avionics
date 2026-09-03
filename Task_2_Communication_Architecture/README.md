# Task 2: Communication Architecture

The drone requires three communication systems:

1. An RC transmitter and receiver
2. A telemetry radio
3. A video transmitter or VTX

They are separate because they carry different information.

## 1. RC Transmitter and Receiver

### Selected Model

- RadioMaster Pocket ELRS 2.4 GHz transmitter
- RadioMaster RP3 ELRS receiver

### Purpose

The RC link carries commands from the pilot to the drone. These include:

- Throttle
- Roll, pitch and yaw
- Flight-mode selection
- Arm and disarm
- Emergency manual control

### Protocol

The transmitter and receiver communicate wirelessly using ExpressLRS.

The receiver communicates with the Pixhawk using CRSF. CRSF is a digital
serial protocol and requires both TX and RX connections.

### Connection to Pixhawk

The receiver will use the Pixhawk TELEM2 UART:

- Receiver TX to Pixhawk TELEM2 RX
- Receiver RX to Pixhawk TELEM2 TX
- Receiver ground to Pixhawk ground
- Receiver power to a suitable regulated supply

CRSF must not be connected as ordinary PWM or PPM.

### Range

The exact range depends on transmission power, antennas, interference and
line of sight. ExpressLRS is designed for long-range RC operation, but a
ground range test must be performed before flight.

## 2. Telemetry Radio

### Selected Model

Holybro SiK Telemetry Radio V3, 100 mW.

The exact frequency version must comply with Indian WPC rules. The radio
should not be operated at an unapproved frequency or transmission power.

### Purpose

Telemetry transfers flight information between the drone and a ground
computer running Mission Planner or QGroundControl.

It carries:

- GPS position
- Altitude
- Battery voltage and current
- Flight mode
- Warnings
- Mission commands
- Autonomous-flight status

### Protocol

The flight information uses MAVLink.

The telemetry radio communicates electrically with the Pixhawk through a
UART serial connection.

### Connection to Pixhawk

The air telemetry radio will connect to TELEM1:

| Pixhawk TELEM1 pin | Connection |
|---|---|
| Pin 1: 5 V | Radio 5 V input |
| Pin 2: Pixhawk TX | Radio RX |
| Pin 3: Pixhawk RX | Radio TX |
| Pin 6: Ground | Radio ground |

CTS and RTS are not required for the basic connection.

### Range

Holybro gives a line-of-sight range of approximately 300–500 m for the
100 mW version with 2 dBi antennas. Better ground antennas may increase the
range, but the link must follow local frequency and power regulations.

## 3. Video Transmitter

### Selected Model

- RUSHFPV Tank Solo 5.8 GHz analogue VTX
- Compatible analogue FPV camera
- Compatible 5.8 GHz analogue ground receiver

### Purpose

The VTX sends live video from the drone to the operator.

The video helps the operator:

- Observe the search area
- Confirm a detected target
- Monitor the drone's surroundings
- Assist with manual control if necessary

### Analogue or Digital

I selected an analogue VTX because it is relatively simple, light and has
low delay.

Because the VTX is analogue, it must use an analogue FPV camera and an
analogue 5.8 GHz receiver. A digital-only camera cannot be connected directly
to this VTX.

### Specifications

- Input voltage: 7–36 V
- Selectable transmission power
- Weight: Approximately 12 g without cables
- Frequency: 5.8 GHz
- Channels: 48

### Connection

- Analogue camera video output to VTX video input
- Camera ground to VTX ground
- VTX antenna to VTX antenna connector
- VTX and camera powered from a suitable regulator

The VTX does not need to send its video through the Pixhawk.

The antenna must always be attached before powering the VTX.

### Range

Video range depends heavily on transmission power, antennas, interference
and line of sight. Therefore, an exact guaranteed range cannot be given.
A range test should be completed at low altitude before the search mission.

## Power Architecture

The battery should not be connected directly to every low-voltage device.

The proposed power arrangement is:

- Battery to power module
- Power module to Pixhawk POWER1
- Regulated 5 V supply to Raspberry Pi and OAK-D Lite
- Pixhawk TELEM1 supply to the low-power telemetry radio
- Regulated supply to the RC receiver
- Suitable regulated supply to the VTX and FPV camera

All connected devices should share a common ground.

The Raspberry Pi should not be powered from a low-current Pixhawk peripheral
pin because it requires more current than the flight controller port is
designed to provide.

## PWM, PPM and Digital Protocols

PWM normally uses one signal wire for each RC channel.

PPM combines several RC channels into a single signal.

CRSF is a digital serial protocol. It uses a UART and supports two-way
communication.

The selected ELRS receiver uses CRSF, so it will be connected to TELEM2 TX
and RX rather than an individual PWM motor output.

## Communication Summary

| System | Wireless link | Pixhawk connection | Information carried |
|---|---|---|---|
| RC | ExpressLRS 2.4 GHz | TELEM2 UART using CRSF | Pilot controls |
| Telemetry | SiK radio | TELEM1 UART using MAVLink | Position, battery and mission data |
| Video | Analogue 5.8 GHz | No direct Pixhawk connection required | Live camera video |

## Sources

- [Pixhawk 6C Mini port details](https://docs.holybro.com/autopilot/pixhawk-6c-mini/pixhawk-6c-mini-ports)
- [Holybro SiK Telemetry Radio V3](https://docs.holybro.com/radio/sik-telemetry-radio-v3)
- [ArduPilot RC-system documentation](https://ardupilot.org/copter/docs/common-rc-systems.html)
- [RUSHFPV Tank Solo specifications](https://rushfpv.net/products/tank-solo-vtx)
- [Indian 865–868 MHz short-range-device rules](https://www.dot.gov.in/static/uploads/2025/07/84f33f09e137fa81930f44bcd5f2d238.pdf)
