# Task 3: Propulsion System

## 1. Given Components

- Drone type: Quadcopter
- Frame size: 10 inch
- Maximum drone weight: 2.5 kg
- Motors: 4 × Holybro S500 V2 2216-920KV
- Propellers: 1045 (10 × 4.5 inch)
- Required endurance: More than 12 minutes

## 2. Selected Battery

I selected a **4S 5000 mAh 20C LiPo battery with an XT60 connector**.

Battery specifications:

- Nominal voltage = 4 × 3.7 = **14.8 V**
- Fully charged voltage = 4 × 4.2 = **16.8 V**
- Capacity = **5000 mAh = 5 Ah**

Holybro recommends a 4S 3000–5000 mAh battery with a rating of 20C or higher for the S500 V2 kit. I selected the 5000 mAh option because flight time is important for the search-and-rescue mission.

## 3. Battery Discharge Calculation

Maximum battery current:

Maximum current = Capacity × C-rating

Maximum current = 5 Ah × 20C

**Maximum battery current = 100 A**

The four ESCs have a combined maximum rating of:

4 × 20 A = **80 A**

The battery’s theoretical 100 A rating is greater than the combined ESC rating. The actual continuous current should still remain within the 60 A continuous rating of the power-distribution board.

## 4. Selected ESC

I selected:

**4 × Holybro BLHeli-S 20 A ESCs**

Reasons:

- They are used in the official Holybro S500 V2 kit.
- They are compatible with the given 2216-920KV motors.
- They support the selected 4S battery.
- One ESC is connected to each motor.
- Their 20 A rating is suitable for this combination.

The built-in power-distribution board is rated for:

- Continuous current: **60 A**
- Burst current: **100 A**

## 5. Endurance Calculation

To protect the LiPo battery, I assumed that only 80% of its capacity would be used.

Usable capacity:

Usable capacity = 5 Ah × 0.8

**Usable capacity = 4 Ah**

Required flight time:

12 minutes = 12 ÷ 60

**Required flight time = 0.2 hours**

Maximum average current for 12 minutes:

Average current = Usable capacity ÷ Flight time

Average current = 4 Ah ÷ 0.2 h

**Maximum average current = 20 A**

Therefore, the complete drone must draw less than 20 A on average to remain airborne for more than 12 minutes.

Holybro reports approximately 18 minutes of hover time with a 5000 mAh battery and no additional payload.

The average current suggested by this result is:

Average current = 4 Ah ÷ (18 ÷ 60)

Average current = 4 ÷ 0.3

**Average current ≈ 13.33 A**

The search-and-rescue electronics add weight and consume power. For a simple practical estimate, I assumed a 30% reduction in the stated hover time:

Estimated flight time = 18 × 0.70

**Estimated flight time ≈ 12.6 minutes**

This is only an estimate, not a guaranteed flight time. The completed drone must undergo a hover test. Its measured average current must remain below 20 A to meet the 12-minute requirement.

## 6. Power Calculation

Maximum average power for the 12-minute target:

Power = Voltage × Current

Power = 14.8 V × 20 A

**Maximum average power = 296 W**

Continuous power capacity of the distribution board at nominal voltage:

Power = 14.8 V × 60 A

**Continuous power capacity = 888 W**

At the fully charged voltage:

Power = 16.8 V × 60 A

**Continuous power capacity = 1008 W**

These are the electrical limits of the distribution board, not the drone’s normal power consumption.

## 7. Estimated Weight

| Component | Estimated weight |
|---|---:|
| S500 V2 ARF kit | 782 g |
| 4S 5000 mAh battery | 500 g |
| Pixhawk 6C Mini | 42.4 g |
| Power module | 30 g |
| GPS module | 30 g |
| Raspberry Pi 5 with cooling | 70 g |
| OAK-D Lite | 61 g |
| ELRS receiver | 4.6 g |
| SiK air radio | 23.5 g |
| VTX | 12 g |
| FPV camera | 10 g |
| Regulators, wires and mounts | 150 g |
| **Estimated total** | **1715.5 g** |

Remaining weight:

Remaining weight = 2500 − 1715.5

**Remaining weight = 784.5 g**

The estimated drone weight is below the 2.5 kg limit. The final assembled drone must still be weighed because the actual battery, wiring and mounting weights may differ.

## 8. Final Selection

- Battery: **4S 5000 mAh 20C or higher LiPo**
- ESCs: **4 × Holybro BLHeli-S 20 A**
- Motors: **4 × Holybro 2216-920KV**
- Propellers: **1045 (10 × 4.5 inch)**
- Estimated weight: **Approximately 1.72 kg**
- Estimated endurance: **Approximately 12.6 minutes**
- Required test: **Measure actual hover current and flight time**

This combination was selected because it is recommended for the S500 V2 kit, is compatible with the given components and remains below the 2.5 kg weight limit based on the estimate.

## 9. Bonus: Alternative Motor

A possible alternative is:

**SunnySky X2216 V3 880KV motor with an APC 10 × 4.7 propeller**

I selected it as an alternative because it has published thrust and power test data and is designed for 10-inch propellers.

The estimated total drone weight is 1715.5 g. Therefore, the thrust needed from each motor during hover is:

Hover thrust per motor = Total weight ÷ Number of motors

Hover thrust per motor = 1715.5 ÷ 4

**Hover thrust per motor ≈ 429 g**

SunnySky’s test data for the 880KV motor with an APC 10 × 4.7 propeller at 11.1 V shows:

| Thrust | Current | Power | Efficiency |
|---:|---:|---:|---:|
| 400 g | 4.6 A | 51.06 W | 7.83 g/W |
| 500 g | 6.5 A | 72.15 W | 6.93 g/W |
| 1000 g | 16.9 A | 187.59 W | 5.33 g/W |
| 1400 g | 28.8 A | 319.68 W | 4.38 g/W |

The required hover thrust of approximately 429 g lies between the 400 g and 500 g test points. Therefore, the approximate hover power would be between 51 W and 72 W per motor.

Using a simple estimate of about 57 W per motor:

Total motor hover power = 57 × 4

**Estimated total motor hover power ≈ 228 W**

This is below the earlier 296 W average-power limit for achieving 12 minutes with the selected battery capacity.

### Important changes for this alternative

The published test was performed at **11.1 V**, so this alternative would require:

- A **3S LiPo battery**
- APC **10 × 4.7 propellers**
- ESCs capable of handling at least the motor’s maximum tested current

The current Holybro 20 A ESCs would not be suitable for the motor’s maximum tested current of 28.8 A. I would use approximately **30–40 A ESCs** for this alternative.

### Bonus conclusion

The SunnySky X2216 V3 880KV is a possible efficiency-focused alternative because it produces approximately 400 g thrust using 51.06 W in its published test.

However, it is not a direct tested comparison with the Holybro motor because an equivalent official thrust-and-power table for the given Holybro 2216-920KV motor was not available. A bench thrust test using the same battery and propeller would be required before confirming that it is definitely more efficient.

## Sources

- [Holybro S500 V2 kit](https://holybro.com/products/s500-v2-kit)
- [Given Holybro 2216-920KV motor](https://zbotic.in/product/holybro-s500-v2-motor-2216-920kv-ccw/)
- [Given 1045 propellers](https://robu.in/product/orange-hd-propellers-104510x4-5-abs-dji-black-1cw-1ccw-1pair-premium-quality/)
- [SunnySky X2216 V3 motor and thrust data](https://sunnyskyusa.com/products/sunnysky-x2216)
- [Pixhawk 6C Mini](https://holybro.com/products/pixhawk-6c-mini)
- [OAK-D Lite](https://shop.luxonis.com/products/oak-d-lite-1)
- [RadioMaster RP3 receiver](https://www.radiomasterrc.com/products/rp3-expresslrs-2-4ghz-receiver)
