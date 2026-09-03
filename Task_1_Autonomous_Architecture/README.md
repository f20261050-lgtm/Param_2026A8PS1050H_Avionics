# Task 1: Autonomous Architecture

## Mission

The drone has to search for a person over the ocean. It should detect the
person, estimate nearby obstacles and send useful information to the Pixhawk
or ground station.

The complete drone must weigh less than 2.5 kg, so the autonomous system
should be light and consume reasonably low power.

## Available Builds

1. IMX219-83 stereo camera with Jetson Orin Nano
2. OAK-D Lite with Raspberry Pi 5
3. D500 LiDAR and wide-angle IMX219 camera with Raspberry Pi 5
4. IMX219-83 stereo camera with Raspberry Pi 5
5. Intel RealSense D435i with Jetson Orin Nano

## Comparison

| Build | Compute | Power | Search-and-rescue suitability | Weight | Cost |
|---|---|---|---|---|---|
| Stereo IMX219 + Jetson | Excellent AI performance | High, as the Jetson operates between about 7 W and 25 W | Good object detection and stereo depth | 23 g camera plus Jetson and cooling | High |
| OAK-D Lite + Raspberry Pi | Good because the camera has its own AI processor | Medium; camera uses about 2.5–3 W while streaming, with extra power for AI and depth | Good balance of colour imaging, AI and nearby depth | About 61 g camera plus Raspberry Pi and cooler | Medium |
| D500 + wide camera + Raspberry Pi | Acceptable | Medium; LiDAR uses 1.45 W in addition to the Pi and camera | Camera can detect a person, but LiDAR range is only 12 m | Sensors weigh about 60 g plus Raspberry Pi and cooler | Medium |
| Stereo IMX219 + Raspberry Pi | Acceptable, but the Pi must calculate depth and run object detection | Medium | Suitable, but processing may be slow | 23 g camera plus Raspberry Pi and cooler | Low |
| RealSense D435i + Jetson | Excellent AI performance | High | Good nearby depth and detection, but depth may be affected by sunlight | 75 g camera plus Jetson and cooling | Very high |

The exact total power depends on processing load. The same operating
conditions should be used when physically testing the final components.

## Weightage

I used the following weightage:

| Parameter | Weightage |
|---|---:|
| Search-and-rescue suitability | 30% |
| Weight | 25% |
| Power consumption | 20% |
| Compute capability | 15% |
| Cost | 10% |

Mission suitability receives the highest weight because the system must
actually detect the rescue target. Weight and power are also important
because they affect the 2.5 kg limit and flight endurance.

Each build is rated from 1 to 5. A score of 5 is best.

For weight, power and cost, a higher score represents lower weight, lower
power or lower cost.

## Scores

| Build | Use case | Weight | Power | Compute | Cost | Final score |
|---|---:|---:|---:|---:|---:|---:|
| Stereo IMX219 + Jetson | 4 | 3 | 2 | 5 | 2 | 3.30 |
| OAK-D Lite + Raspberry Pi | 4 | 4 | 4 | 4 | 3 | 3.90 |
| D500 + wide camera + Raspberry Pi | 3 | 3 | 4 | 3 | 3 | 3.20 |
| Stereo IMX219 + Raspberry Pi | 3 | 4 | 3 | 3 | 4 | 3.35 |
| RealSense D435i + Jetson | 3 | 2 | 2 | 5 | 1 | 2.65 |

The score is calculated using:

Final score = (Use case × 0.30) + (Weight × 0.25)
            + (Power × 0.20) + (Compute × 0.15)
            + (Cost × 0.10)

For example, Build 2 is calculated as:

Final score = (4 × 0.30) + (4 × 0.25) + (4 × 0.20)
            + (4 × 0.15) + (3 × 0.10)

Final score = 3.90

## Selected Build

I selected Build 2: OAK-D Lite with Raspberry Pi 5.

The OAK-D Lite has a colour camera, two depth cameras and a built-in AI
processor. It can perform some object detection and depth processing itself,
which reduces the Raspberry Pi's workload.

The Raspberry Pi can manage the autonomous program and communicate results
to the Pixhawk. This build is not the most powerful option, but it gives a
good balance of compute capability, power, weight and cost.

One limitation is that the OAK-D Lite's ideal depth range is approximately
0.8 m to 12 m. Therefore, depth will mainly be useful for nearby obstacles.
The colour camera can still be used to detect a person from farther away.

## Bonus: Camera Orientation

I would mount the OAK-D Lite at the front of the drone and tilt it slightly
downward by approximately 20 degrees.

This allows the camera to observe the area in front of and below the drone.
The mount should be rigid enough to keep the depth cameras aligned, while
using small vibration-damping material.

The propellers and landing gear should not appear in the camera's view.
The camera should also receive some protection from sea spray without
blocking its lenses.

## Bonus: Alternative Build

My alternative choice is Build 4: IMX219-83 stereo camera with Raspberry
Pi 5.

It is lighter and cheaper than the selected build. However, the Raspberry
Pi has to perform both stereo-depth calculation and object detection.
Therefore, it may process images more slowly than Build 2.

I would select Build 4 if low cost and low camera weight were more important
than processing performance.

## Sources

- [NVIDIA Jetson Orin Nano documentation](https://docs.nvidia.com/jetson/orin-nano-devkit/user-guide/index.html)
- [Luxonis OAK-D Lite documentation](https://docs.luxonis.com/hardware/products/OAK-D%20Lite)
- [Waveshare D500 LiDAR](https://www.waveshare.com/d500-lidar-kit.htm)
- [Waveshare IMX219-83 stereo camera](https://www.waveshare.com/imx219-83-stereo-camera.htm)
- [Arducam IMX219 wide-angle camera](https://www.arducam.com/blog/product/b0180-arducam-imx219-wide-angle-camera-module-drop-replacement-raspberry-pi-v2-nvidia-jetson-camera/)
- [Raspberry Pi 5 product brief](https://pip-assets.raspberrypi.com/categories/892-raspberry-pi-5/documents/RP-008348-DS-4-raspberry-pi-5-product-brief.pdf)
- [Intel RealSense D400 series datasheet](https://www.intelrealsense.com/wp-content/uploads/2022/04/Intel-RealSense-D400-Series-Datasheet-April-2022.pdf)
