# Build 4: Stereo IMX219 Camera with Raspberry Pi 5

## Components

- Custom or Waveshare IMX219-83 stereo camera
- Raspberry Pi 5 with 8 GB RAM

## How It Works

The stereo camera uses two IMX219 sensors to capture the same scene from
slightly different positions.

The Raspberry Pi compares the two images to estimate depth. It must also run
the object-detection program to search for a person or boat.

Unlike the OAK-D Lite, this camera does not have a separate built-in AI
processor. Therefore, most of the image and depth processing must be
performed by the Raspberry Pi.

## Basic Specifications

### IMX219-83 Stereo Camera

- Sensor arrangement: Two Sony IMX219 sensors
- Type: Stereo camera
- Approximate field of view: 83 degrees, subject to product confirmation
- Interface: MIPI-CSI
- Main purpose: Image capture and stereo depth estimation
- Resolution: To be confirmed from the exact product page
- Weight: To be confirmed
- Power consumption: To be confirmed
- Cost: To be confirmed

### Raspberry Pi 5 8 GB

- Processor: 2.4 GHz quad-core Arm Cortex-A76
- Memory: 8 GB LPDDR4X
- Camera/display connections: Two MIPI interfaces
- Input supply: Regulated 5 V
- Recommended supply capacity: Up to 5 V at 5 A
- Main purpose: Object detection, stereo processing and communication
- Cooling: An active cooler or fan may be needed
- Weight: To be confirmed with cooling and storage
- Cost: To be confirmed

## Advantages

1. It should be cheaper than the Jetson-based stereo build.
2. It may use less power than the Jetson at its highest operating mode.
3. The stereo camera provides normal images as well as depth information.
4. The Raspberry Pi 5 has two MIPI camera/display connections.
5. Raspberry Pi has a large community and many beginner-friendly resources.

## Disadvantages

1. The Raspberry Pi must perform both object detection and stereo-depth
   calculation.
2. Real-time processing may be slower than on the Jetson.
3. Heavy processing can increase power use and heat.
4. Active cooling adds weight and consumes some power.
5. The exact stereo-camera software and Raspberry Pi 5 compatibility must
   be confirmed.
6. Depth accuracy reduces as the target moves farther from the cameras.
7. Reflections and low visual detail over the ocean may make stereo matching
   more difficult.

## Initial Assessment

- Compute capability: Acceptable
- Power consumption: Good to acceptable
- Mission suitability: Acceptable to good
- Weight: To be confirmed
- Cost: Good, subject to confirmation

This build is a lower-cost alternative to Build 1. Its main limitation is
that the Raspberry Pi may struggle when object detection and stereo-depth
processing are performed at the same time.
