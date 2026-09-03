# Build 1: Stereo Camera with Jetson Orin Nano

## Components

- Custom or Waveshare IMX219-83 stereo camera
- NVIDIA Jetson Orin Nano

## How It Works

The stereo camera contains two image sensors. The two cameras view the same
scene from slightly different positions. The Jetson compares the images to
estimate depth.

The Jetson can also run an object-detection model to identify a person or
boat. This makes the build suitable for autonomous search and rescue.

## Basic Specifications

### IMX219-83 Stereo Camera

- Sensor: Two Sony IMX219 camera sensors
- Camera arrangement: Stereo
- Resolution: To be confirmed from the exact product page
- Field of view: Approximately 83 degrees, subject to confirmation
- Connection: MIPI-CSI camera interface
- Main purpose: Capturing images and estimating depth
- Weight: To be confirmed
- Power consumption: To be confirmed
- Cost: To be confirmed

### NVIDIA Jetson Orin Nano

- Type: AI companion computer
- Memory: 8 GB for the developer-kit version considered
- AI performance: Up to 67 TOPS with the current software configuration
- Power: Configurable from 7 W to 25 W
- Camera connections: Two MIPI-CSI connectors on the developer kit
- Main purpose: Object detection, image processing and depth calculation
- Weight: To be confirmed for the complete flying setup
- Cost: To be confirmed

## Advantages

1. The Jetson has strong AI processing capability.
2. It should be capable of running real-time object detection.
3. The stereo camera can provide both normal images and depth information.
4. The system could detect a person and estimate the person's distance.
5. Processing can happen onboard without continuously sending images to the
   ground station.

## Disadvantages

1. The Jetson may consume up to 25 W, which can reduce flight endurance.
2. The developer kit and its cooling system add weight.
3. Stereo depth calculation requires additional processing.
4. Stereo depth may become less accurate for distant objects.
5. The system is likely to be more expensive than a Raspberry Pi-based build.
6. Bright sunlight, reflections and the low texture of the ocean surface may
   make stereo depth estimation more difficult.

## Initial Assessment

- Compute capability: Excellent
- Power consumption: Poor to acceptable
- Mission suitability: Good
- Weight: To be confirmed
- Cost: To be confirmed

No final score is assigned yet because the exact weight, power and cost must
be compared fairly with the other four builds.
