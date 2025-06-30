# Buck Converter-Based Single-Phase and Three-Phase Inverter Using Differential Load Connections

## Project Overview

This project focuses on the design and hardware implementation of **single-phase and three-phase DC-AC inverters** using **differential connection of buck converters**, as described in **Section 6.1.4 — Differential Connection of the Load** from *Fundamentals of Power Electronics* by **Robert W. Erickson**.

Initially, a **single-phase inverter** was realized using two buck converters connected in differential mode. This approach was extended to a **three-phase inverter** by configuring **three buck converters**, each generating a phase voltage with respect to a virtual neutral point formed by the average of the three outputs.

All circuits were modeled in MATLAB for validation and then implemented in hardware using **TL494-based PWM generation** and **custom-soldered buck converter boards**.

---

## Hardware Details

### PWM Generation Circuit using TL494

- Pulse width modulation implemented using **TL494IN**
- Frequency and duty cycle controlled using **3362P potentiometers**
- Gate driving handled by **TC4428A dual MOSFET driver**
- Outputs configured in **emitter follower mode** for clean drive signals
- PWM verified using oscilloscope before interfacing with power stage

### Power Converter Components

| Component             | Specification / Part No.    | Description                          |
|----------------------|------------------------------|--------------------------------------|
| Power MOSFET         | IRFZ44NPbF                   | 49A, 55V, TO-220, heatsink mounted   |
| Diode                | QH08TZ600                    | 600V, 8A Hyperfast recovery diode    |
| Inductor             | 1 mH toroidal, 2.4 A rated   | Buck converter output inductor       |
| Capacitors           | 470 µF (63 V), 100 µF (25 V) | Output and input filtering           |
| Load                 | 40 Ω, 3 A Rheostat           | Variable resistive load              |
| Current Sense Resistor | 0.01 Ω, 3 W                 | In-line current monitoring           |

### TL494 Driver Board Components

| Component Type       | Value / Part No.             | Quantity |
|----------------------|------------------------------|----------|
| Potentiometers       | 10kΩ (D-var), 50kΩ (F-var)   | 2        |
| Capacitors           | 1nF, 10nF, 100nF, 4.7µF       | Multiple |
| Resistors            | 150Ω, 4.7kΩ, 47kΩ             | Multiple |
| Connectors / Headers | Berg Strip, Green Terminals  | —        |

---

## Simulation & Testing

- **Single-phase inverter** simulated using two buck converters in MATLAB/Simulink
- Extended topology to **three-phase inverter using three buck converters**
- Verified phase voltages and neutral formation via simulation
- Hardware testing confirmed expected output waveforms using DSO
- Phase synchronization achieved via tuning PWM signals from TL494

---

## Hardware Integration

1. **TL494 Board Assembly**
   - Assembled PWM circuit with potentiometer control for frequency and duty cycle
   - Output verified via oscilloscope before interfacing

2. **MOSFET Driver and Power Stage**
   - Used TC4428A for level shifting and clean switching
   - Maintained **isolation between drive and power grounds**
   - Assembled buck converter hardware on general-purpose and custom PCBs

3. **Inverter Realization**
   - **Single-phase inverter**: Two buck converters driving a differential resistive load
   - **Three-phase inverter**: Three buck converters supplying phase voltages with respect to virtual neutral
   - Verified **balanced 120° phase-shifted AC outputs** on DSO

---

## Results

| Feature               | Achieved Outcome                              |
|-----------------------|-----------------------------------------------|
| Single-phase AC Output| Differential buck pair produced sinusoidal AC |
| Three-phase Inversion | 3 buck converters generated phase voltages    |
| Virtual Neutral       | Formed dynamically via phase averaging        |
| Hardware PWM Control  | Tuned TL494 for synchronized inverter driving |
| Waveform Verification | Successful on DSO with clear phase separation |

---

## Key Concepts & Learning Outcomes

- Implemented **DC-AC inversion** using buck converters with **differential load connection**
- Realized both **single-phase and three-phase inverters** without transformers or H-bridges
- Designed and built hardware using **TL494 PWM generator** and **TC4428A gate driver**
- Understood and applied **virtual neutral formation** for three-phase synthesis
- Practiced **safe measurement**, signal probing, and **gate-power isolation** in lab conditions

---

## Measurement & Safety Protocols

- **Ground isolation** ensured between TL494 and power stages
- Used **oscilloscope safely**: one signal at a time due to lack of differential probes
- For current measurement: placed **0.01 Ω resistors** in line and used lab current probes
- **Load connected prior to power-up** to prevent overcurrent on inductors
  
---

## Contributors

- Nishit Rupavatia
- Prashant Narang
- Guide: Professor Vijay AS

---

## 📎 References

- Robert Erickson, D. Maksimovic, *Fundamentals of Power Electronics*, 2nd Ed., Springer  
- TL494 PWM Controller Datasheet – [Texas Instruments](https://www.ti.com)  
- TC4428A MOSFET Driver Datasheet – [Microchip](https://www.microchip.com)  
- IRFZ44NPbF Datasheet – [Infineon Technologies](https://www.infineon.com)  
- QH08TZ600 Diode Datasheet – [Power Integrations](https://www.power.com)

---




