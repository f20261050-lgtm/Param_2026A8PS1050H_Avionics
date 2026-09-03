# Autonomous Architecture Decision Matrix

## Evaluation Weights

| Criterion | Weight |
|---|---:|
| Mission suitability | 30% |
| Weight | 25% |
| Power consumption | 20% |
| Compute capability | 15% |
| Cost | 10% |

Each build is scored from 1 to 5. A score of 5 is best and a score of 1
is worst.

For power, weight and cost, a higher score means lower power, lower weight
or lower cost.

## Scores

| Build | Mission suitability | Weight | Power | Compute | Cost |
|---|---:|---:|---:|---:|---:|
| 1. Stereo IMX219 + Jetson | 4 | 3 | 2 | 5 | 2 |
| 2. OAK-D Lite + Raspberry Pi | 4 | 4 | 4 | 4 | 3 |
| 3. D500 + wide camera + Raspberry Pi | 3 | 3 | 4 | 3 | 3 |
| 4. Stereo IMX219 + Raspberry Pi | 3 | 4 | 3 | 3 | 4 |
| 5. RealSense D435i + Jetson | 3 | 2 | 2 | 5 | 1 |

## Weighted Calculations

### Build 1

Final score = (4 × 0.30) + (3 × 0.25) + (2 × 0.20)
            + (5 × 0.15) + (2 × 0.10)

Final score = 3.30

### Build 2

Final score = (4 × 0.30) + (4 × 0.25) + (4 × 0.20)
            + (4 × 0.15) + (3 × 0.10)

Final score = 3.90

### Build 3

Final score = (3 × 0.30) + (3 × 0.25) + (4 × 0.20)
            + (3 × 0.15) + (3 × 0.10)

Final score = 3.20

### Build 4

Final score = (3 × 0.30) + (4 × 0.25) + (3 × 0.20)
            + (3 × 0.15) + (4 × 0.10)

Final score = 3.35

### Build 5

Final score = (3 × 0.30) + (2 × 0.25) + (2 × 0.20)
            + (5 × 0.15) + (1 × 0.10)

Final score = 2.65

## Ranking

| Rank | Build | Score |
|---:|---|---:|
| 1 | OAK-D Lite + Raspberry Pi 5 | 3.90 |
| 2 | Stereo IMX219 + Raspberry Pi 5 | 3.35 |
| 3 | Stereo IMX219 + Jetson Orin Nano | 3.30 |
| 4 | D500 + wide camera + Raspberry Pi 5 | 3.20 |
| 5 | RealSense D435i + Jetson Orin Nano | 2.65 |

## Preliminary Selection

Build 2, consisting of the OAK-D Lite and Raspberry Pi 5, receives the
highest score.

The OAK-D Lite performs its own depth and AI processing. This reduces the
processing load on the Raspberry Pi. The combination provides colour
images, depth information and object-detection capability without requiring
the higher power of a Jetson-based build.

Its main limitation is that depth information is most useful at relatively
short distances. The colour camera can still be used to detect a person
from farther away, while depth can assist with nearby obstacles.

These scores are preliminary. Exact component weights, prices and combined
power consumption will be added before making the final selection.
