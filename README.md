# Battery-ready

Tiny LiPo/Li-ion charger & 5 V boost module built around the **IP5306**. Solder it directly to a 3.7 V cell and you get USB-C charging and a switchable 5 V output for small projects, in an ~11 x 13 mm footprint.

## Features

- USB-C charging (6-pin connector) of a single-cell 3.7 V LiPo / Li-ion battery
- 5 V boost output (max ~1.5A recommended), switchable with an onboard button
- Charge status LED
- Ultra-compact: **~11 mm x ~13 mm** including the USB-C connector
- Designed to be soldered straight onto the battery for a compact build

## Hardware

| Part | Function |
|---|---|
| IP5306 | Battery charger + synchronous step-up (5 V) converter |
| USB-C 6-pin | 5 V charging input |
| Tactile button | 5 V output enable / disable |
| Status LED | Charging indicator |

## Pinout

The board has 3 solder pads:

| Pad | Description |
|---|---|
| `5V` | 5 V output (only when enabled) |
| `B+` | Battery positive |
| `G` | Battery negative. Shared with the 5 V output |

## Usage

### Output control (button)

| Action | Result |
|---|---|
| Single press | 5 V output **enabled** |
| Double press | 5 V output **disabled** |

### Charging

1. Connect a USB-C source to the connector.
2. LED **blinking** = battery is charging.
3. LED **off** (stops blinking) = battery is fully charged.

The 5 V output can be used while charging (IP5306 charge-and-discharge behaviour).

## Important notes

- **Auto shutdown on light load:** if the load on the 5 V line is below ~100 mA, the output switches off after ~30 s. Very low-power loads (sensors, MCUs in sleep) will therefore be cut off. Press the button again to re-enable, or add a dummy/bleed load if the device must stay powered.
- **Voltage on `5V` pad while disabled:** measuring the pad with a multimeter while the output is disabled shows roughly **2.3 V**. This is not a real supply: it is a high-impedance leakage/residual voltage from the boost stage, picked up by the meter's input, and it collapses as soon as any load is connected. The output is considered off.