# Build 3: D500 LiDAR, Wide-Angle Camera and Raspberry Pi 5

## Components

- Waveshare D500 360-degree LiDAR
- Arducam IMX219 wide-angle camera
- Raspberry Pi 5 with 8 GB RAM

## How It Works

The wide-angle camera captures images of the search area. The Raspberry Pi
can run an object-detection program on these images to search for a person
or boat.

The D500 LiDAR rotates and measures the distance of objects around the drone.
It can therefore assist with nearby obstacle detection.

The camera and LiDAR perform different jobs. The camera identifies what an
object is, while the LiDAR measures the distance to nearby objects in its
scanning plane.

## Basic Specifications

### D500 LiDAR

- Type: 360-degree 2D time-of-flight LiDAR
- Measuring range: 0.03 m to 12 m
- Scanning frequency: 6 Hz to 13 Hz
- Typical scanning frequency: 10 Hz
- Communication: UART at 230400 baud
- Supply voltage: 5 V
- Current: Approximately 290 mA
- Power consumption: Approximately 1.45 W
- Weight: Approximately 45 g
- Main purpose: Detecting nearby obstacles and measuring distance

### Arducam IMX219 Wide-Angle Camera

- Sensor: Sony IMX219
- Resolution: 8 megapixels
- Maximum still-image resolution: 3280 × 2464 pixels
- Interface: MIPI-CSI
- Focus: Manual focus for the wide-angle B0180 model
- Diagonal field of view: Approximately 175 degrees
- Main purpose: Capturing a wide view for person or boat detection
- Weight: To be confirmed for the exact selected version
- Power consumption: To be confirmed
- Cost: To be confirmed

### Raspberry Pi 5 8 GB

- Processor: 2.4 GHz quad-core Arm Cortex-A76
- Memory: 8 GB
- Input supply: Regulated 5 V
- Main purpose: Processing camera images and LiDAR measurements
- Cooling: A fan or active cooler may be required
- Weight and power: To be calculated with the cooler and other accessories

## Advantages

1. The wide-angle camera can observe a large search area.
2. The LiDAR provides 360-degree coverage for nearby obstacles.
3. The LiDAR uses only about 1.45 W.
4. The LiDAR weighs only about 45 g.
5. The LiDAR can give direct distance measurements.
6. The Raspberry Pi can receive LiDAR data through UART.

## Disadvantages

1. The D500 only measures objects up to approximately 12 m away.
2. It scans in a 2D plane rather than producing a complete 3D view.
3. Its scanning plane may miss objects above or below the sensor.
4. A person in the ocean may be too small or too far away for the LiDAR.
5. Water reflections and direct sunlight may affect practical operation.
6. The Raspberry Pi must perform the camera object detection itself.
7. A 175-degree camera can produce strong image distortion near the edges.

## Initial Assessment

- Compute capability: Acceptable to good
- Power consumption: Good
- Mission suitability: Acceptable
- Weight: Good, subject to confirming the complete setup
- Cost: To be confirmed

This architecture appears useful for nearby obstacle detection, but the
12 m LiDAR range limits its usefulness for finding a distant person over
the ocean.
