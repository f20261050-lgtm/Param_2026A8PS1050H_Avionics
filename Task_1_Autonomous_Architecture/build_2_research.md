# Build 2: OAK-D Lite with Raspberry Pi 5

## Components

- Luxonis OAK-D Lite depth and AI camera
- Raspberry Pi 5 with 8 GB RAM

## How It Works

The OAK-D Lite has one colour camera and two monochrome cameras. The two
monochrome cameras are used to estimate depth.

The camera also has a built-in AI processor. This means it can perform some
depth processing and object detection before sending the result to the
Raspberry Pi.

The OAK-D Lite connects to the Raspberry Pi through USB. The Raspberry Pi
can then use the result for autonomous navigation and communicate with the
Pixhawk.

## Basic Specifications

### OAK-D Lite

- Main colour sensor: Sony IMX214
- Depth sensors: Two OV7251 monochrome cameras
- Connection: USB 2 or USB 3
- Ideal depth range: Approximately 0.8 m to 12 m
- Power for basic camera streaming: Approximately 2.5 W to 3 W
- Additional AI processing: Up to approximately 1 W
- Additional stereo-depth processing: Up to approximately 0.5 W
- Main purpose: Colour imaging, depth estimation and AI processing
- Weight: To be confirmed for the exact version
- Cost: To be confirmed

### Raspberry Pi 5 8 GB

- Processor: 2.4 GHz quad-core Arm Cortex-A76
- Memory: 8 GB
- Camera/display interfaces: Two MIPI interfaces
- USB ports: Two USB 3 and two USB 2 ports
- Required input: Regulated 5 V supply
- Recommended maximum power supply: 5 V at 5 A
- Main purpose: Autonomous software and communication with the Pixhawk
- Weight: To be confirmed with cooling equipment
- Cost: To be confirmed

## Advantages

1. The OAK-D Lite performs depth processing inside the camera.
2. Its built-in AI processor reduces the Raspberry Pi's workload.
3. It provides colour images, depth information and AI capability in one unit.
4. USB makes the camera relatively simple to connect to the Raspberry Pi.
5. The combination should consume less power than a Jetson operating at its
   highest power setting.
6. It is suitable for detecting nearby obstacles.

## Disadvantages

1. Its ideal depth range is only about 0.8 m to 12 m, so it cannot provide
   reliable depth measurements for a person far away.
2. Strong sunlight and reflections from water may reduce depth accuracy.
3. The Raspberry Pi 5 requires cooling during demanding operation.
4. It is less powerful than the Jetson for running large AI models.
5. The Raspberry Pi and OAK-D Lite require a stable regulated 5 V supply.
6. Exact weight and cost depend on the selected cooling and storage equipment.

## Initial Assessment

- Compute capability: Good
- Power consumption: Good
- Mission suitability: Good
- Weight: To be confirmed
- Cost: To be confirmed

No final score is assigned yet because the same information must first be
collected for all five builds.
