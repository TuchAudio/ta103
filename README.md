# TuchAudio 103
Discrete, simple op-amp phono preamp

## Purpose
The most simple discrete op-amp, with **just 4 transistors** per channel -- a _3-transistor_ design was tried, but performed poorly.

## Design quirks

An op-amp this simple doesn't have too much of _open-loop gain_, thus the approximate formulae usually used are **no longer valid**. For this reason, _bass performance_ is just acceptable (but within _DIN 45.500_ specs).

DIN and RCA jacks are provided for signal input. Since the _native_ input impedance is around **110 kΩ**, space for suitable load (`Rx` and `Cx`) is provided for perfect adaptation; but for added flexibility, it is possible to use the free input for a suitable RC combo in parallel, to match the appropriate cartridge load.

Originally intended to be connected thru the [501 Input Selector board](), both output pins and power input are at compatible locations within each board. An aditional RCA **output** jack can be installed in order to use the circuit as a _stand-alone preamp_.

The use of an _asymmetric_ power supply (and its associated feedback _DC-blocking capacitor_) means that **it takes a few seconds** for the preamp to operate after powerup (or a noticeable supply voltage change).

### Stability

As any other amplifier with _asymmetrical power supply_, the PSRR is very poor, thus a **well filtered, stable** power supply is essential. Increasing (within reason) `R115/R215` may help a bit.

### Suggested mods

#### Standalone mode

Despite being designed around a 12 Volt power supply, this can be run from a single **9 Volt battery**, with minor changes and similar performance.

- `R115/R215`: use **220 Ω** instead of 330.
- `R103/R110/R203/R210`: use **8.2 kΩ** instead of 12K.

#### IEC1976/Neumann ammendments

The stated values are designed around these _ammendments_ to the **RIAA curve**; but since they're currently _deprecated_, you may get **improved bass response** by turning back to RIAA correction:

- `C104/C204`: do not mount (Neumann ammendment)
- `C106/C206`: use **470 nF** or more instead of 100 nF (which made a _-3 dB point at 20 Hz_ **over 108 kΩ** of the _501 board_ input)

## Specs

_Measured thru a **501 input board** (tape rec. output), 12 V supply_

- **Power supply:** 9-12 V, asymmetrical, max. 6 mA
- **Input connectors:** 2x RCA plus DIN (in parallel)
- **Gain at 1 kHz:** 47x (+33.45 dB)
- **Input sensitivity:** 3.8 mV (for 180 mV output)
- **Input impedance:** 110 kΩ; adjusted by `Rx/Cx`, either internal or external.
- **Output level and impedance:** 180 mV / 3.3 KΩ
- **Overload margin:** at least +15 dB
- **Signal-to-noise ratio:** TBD
- **Frequency response:** 40 Hz - 20 kHz _(+0.25/-3 dB deviation from RIAA)_
- **Distortion:**

| Harmonic | nominal output | +15 dB overload |
| -------- | -------------- | --------------- |
| 2nd      | negligible     | 0.5 %           |
| 3rd      | 0.1 %          | 0.9 %           |
| 4th      | 0.11 %         | 0.3 %           |

