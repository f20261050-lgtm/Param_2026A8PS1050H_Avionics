# Build 5: RealSense D435i with Jetson Orin Nano

## Components

- Intel RealSense D435i depth camera
- NVIDIA Jetson Orin Nano

## How It Works

The RealSense D435i contains a colour camera and two stereo depth sensors.
It produces a colour image and estimates the distance of nearby objects.

It also contains an IMU that measures acceleration and rotation.

The camera connects to the Jetson through USB. The Jetson can run an
object-detection model on the colour image and use the depth information
for nearby obstacle awareness.

## Basic Specifications

### Intel RealSense D435i

- Maximum depth resolution: 1280 × 720
- Maximum colour resolution: 1920 × 1080
- Maximum depth frame rate: Up to 90 frames per second
- Depth field of view: More than 90 degrees diagonally
- Stated depth range: Approximately 0.2 m to more than 3 m, depending on
  lighting and operating conditions
- Additional sensor: Six-axis IMU
- Connection: USB
- Approximate weight: 75 g
- Main purpose: Colour imaging, depth estimation and movement measurement
- Power consumption: To be confirmed for the chosen operating mode
- Cost: To be confirmed

### NVIDIA Jetson Orin Nano

- Memory: 8 GB for the developer-kit version considered
- AI performance: Up to 67 TOPS
- Configurable power: Approximately 7 W to 25 W
- Main purpose: Object detection, autonomous processing and communication
- Cooling: A fan and heatsink are required
- Weight: To be confirmed for the complete setup
- Cost: To be confirmed

## Advantages

1. The Jetson provides strong AI processing capability.
2. The RealSense produces depth data without requiring the Jetson to
   calculate stereo depth entirely from raw camera images.
3. The camera provides both colour and depth information.
4. The built-in IMU provides additional movement information.
5. USB makes the camera relatively simple to connect to the Jetson.
6. The system should be capable of real-time object detection.

## Disadvantages

1. The RealSense depth range is mainly useful for nearby objects.
2. Strong sunlight can reduce the quality of depth measurements.
3. Reflections from the ocean may produce unreliable depth readings.
4. The Jetson can consume considerably more power than the simpler options.
5. The Jetson, camera and cooling system add weight.
6. This is likely to be one of the more expensive builds.
7. The RealSense is not waterproof and would require protection from sea
   spray.

## Initial Assessment

- Compute capability: Excellent
- Power consumption: Poor to acceptable
- Mission suitability: Good for AI detection but limited for long-range depth
- Weight: Acceptable, subject to confirming the complete setup
- Cost: Poor to acceptable

This build has strong processing capability, but its power, cost and
short practical depth range may be unnecessary for the mission.
