# Mission Requirements

## Mission Overview

The proposed drone will perform an autonomous search-and-rescue mission
over the ocean. Its objective is to detect and locate Odysseus and transmit
useful information to the ground operator.

## Design Constraints

- Maximum all-up weight: 2.5 kg
- Frame and propeller class: 10 inch
- Flight controller: Pixhawk 6C Mini
- Required endurance: More than 12 minutes
- Operating environment: Outdoor flight over the ocean

## Autonomous-System Requirements

1. Navigate autonomously through a predefined search area.
2. Detect a person or small vessel against an ocean background.
3. Estimate the target's position or relative distance.
4. Provide forward obstacle awareness.
5. Process sensor data sufficiently quickly for real-time operation.
6. Communicate the detected target's location to the flight controller
   or ground operator.
7. Consume as little power as practical to preserve flight endurance.
8. Remain light enough to satisfy the complete drone's 2.5 kg limit.
9. Integrate with the Pixhawk 6C Mini.
10. Remain reasonably affordable without compromising mission performance.

## Evaluation Criteria

The five proposed autonomous architectures will be evaluated using the
following criteria:

| Criterion | Weight | Reason |
|---|---:|---|
| Mission suitability | 30% | Detection and navigation capability are essential for completing the rescue mission. |
| Weight | 25% | The complete aircraft cannot exceed 2.5 kg. |
| Power consumption | 20% | Sensor and computer power reduces available flight endurance. |
| Compute capability | 15% | Real-time detection and depth processing require sufficient computing performance. |
| Cost | 10% | Cost matters, but flight feasibility and mission performance are more important. |

## Scoring Method

Each architecture will receive a score from 1 to 5 for every criterion:

| Score | Meaning |
|---:|---|
| 1 | Very poor |
| 2 | Poor |
| 3 | Acceptable |
| 4 | Good |
| 5 | Excellent |

The final weighted score will be calculated as:

Final score = (Mission suitability × 0.30)
            + (Weight × 0.25)
            + (Power × 0.20)
            + (Compute × 0.15)
            + (Cost × 0.10)

The architecture with the strongest overall score will be selected, provided
that it can fit within the complete drone's weight and power budgets.
