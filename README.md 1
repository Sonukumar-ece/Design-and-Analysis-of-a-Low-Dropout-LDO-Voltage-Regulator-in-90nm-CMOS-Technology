# Design and Analysis of a Low-Dropout (LDO) Voltage Regulator in 90nm CMOS

> **B.Tech Major Project** — Department of Electronics and Communication Engineering  
> National Institute of Technology Arunachal Pradesh *(Established by Ministry of Education, Govt. of India)*

**Team Members:**
- Kuldeep Choudhary (EC22B033)
- Sonu Kumar (EC22B026)
- Shubham Shekhawat (EC22B024)

**Supervisor:** Dr. Preetisudha Meher (HOD), Assistant Professor, ECE Department

---

## Table of Contents

- [Project Overview](#project-overview)
- [System Architecture](#system-architecture)
- [Error Amplifier Design](#error-amplifier-design)
- [Pass Element & Feedback Network](#pass-element--feedback-network)
- [Loop Compensation](#loop-compensation)
- [Simulation Results](#simulation-results)
- [Key Performance Summary](#key-performance-summary)
- [Conclusion & Future Scope](#conclusion--future-scope)
- [References](#references)

---

## Project Overview

This project presents the design, analysis, and simulation of a fully integrated **Low-Dropout (LDO) Linear Voltage Regulator** implemented in a standard **90nm CMOS process technology**.

### Objectives

- Design a robust, fully integrated LDO regulator using 90nm CMOS process technology.
- Utilize a **high-gain two-stage error amplifier** architecture to achieve precise output voltage regulation.
- Implement **RC Miller compensation** to guarantee loop stability across a wide load current range (0 mA to 30 mA).
- Achieve excellent **transient load regulation** with minimal voltage under/overshoot during rapid load steps.

---

## System Architecture

The LDO consists of four core elements:

| Block | Description |
|---|---|
| Reference Voltage (V_REF) | Stable 900 mV input reference |
| Error Amplifier (EA) | Two-stage op-amp for high-gain sensing |
| PMOS Pass Transistor (PM3) | Large-area power transistor for current delivery |
| Resistive Feedback Network | R1, R2 divider for output voltage scaling |

**Design Parameters:**

| Parameter | Value |
|---|---|
| Input Voltage (V_IN) | 1.2 V |
| Reference Voltage (V_REF) | 900 mV |
| Output Load Capacitor (C_L) | 1 µF |

**Closed-Loop Operation:** The error amplifier continuously senses the scaled output voltage via the feedback network and compares it against V_REF to dynamically adjust the gate drive of the pass transistor, correcting for load or line fluctuations.

---

## Error Amplifier Design

### Topology: Two-Stage CMOS Op-Amp

| Stage | Description |
|---|---|
| First Stage | NMOS differential input pair (NM0, NM1) with PMOS active current mirror load (PM1, PM2) — provides high differential gain |
| Second Stage | PMOS common-source amplifier (PM0) with NMOS active current source load (NM3) — maximizes output swing |
| Biasing Network | Constant current source I1 = 10 µA through master-slave NMOS current mirror (NM4, NM2) |

### Transistor Sizing

| Transistor / Component | Type | Width (W) | Length (L) | Multiplier (m) |
|---|---|---|---|---|
| NM0, NM1 (Input Pair) | NMOS | 2.5 µm | 500 nm | 1 |
| PM1, PM2 (1st Stage Load) | PMOS | 2.0 µm | 500 nm | 1 |
| PM0 (2nd Stage Driver) | PMOS | 4.0 µm | 500 nm | 13 |
| NM3 (2nd Stage Load) | NMOS | 2.0 µm | 500 nm | 23 |
| NM4, NM2 (Bias Mirrors) | NMOS | 3.5 µm | 500 nm | 1 |

---

## Pass Element & Feedback Network

### PMOS Pass Transistor (PM3)

Sized with a large aspect ratio to minimize dropout voltage (V_DO = V_IN − V_OUT) and source maximum load currents.

| Parameter | Value |
|---|---|
| Width (W) | 3.0 µm |
| Length (L) | 100 nm |
| Multiplier (m) | 100 |
| Effective Total Gate Width | 300 µm |

### Feedback Network

| Component | Value |
|---|---|
| R1 | 55 kΩ |
| R2 | 450 kΩ |

**Target Output Voltage:**

```
V_OUT = V_REF × (1 + R1 / R2)
      = 0.9 V × (1 + 55 kΩ / 450 kΩ)
      = 1.01 V
```

---

## Loop Compensation

### RC Miller Compensation Strategy

| Component | Value |
|---|---|
| Compensation Capacitor (C0) | 1.2 pF |
| Nulling Resistor (R0) | 1.82 kΩ |

**Pole Splitting:** The RC network is connected across the error amplifier's second stage, splitting the dominant internal pole and pushing non-dominant poles beyond the Unity Gain Frequency (UGF).

**Zero Control:** The nulling resistor R0 eliminates the Right-Half-Plane (RHP) zero introduced by the compensation capacitor, preventing phase margin degradation.

---

## Simulation Results

### AC Stability — Loop Gain vs. Load Condition

| Load Condition | DC Loop Gain | Unity Gain Frequency (UGF) | Phase Margin (PM) |
|---|---|---|---|
| No Load (0 mA) | −12.67 µdB (below 0 dB) | — | Stable, low g_m |
| Typical Load (15 mA) | High | 666.81 kHz | **81.23°** |
| Full Load (30 mA) | High | ~1.05 MHz | **81.86°** |

> The Miller compensation successfully maintains phase margin > 81° across all active operating regions.

### Line Regulation

Output voltage was characterized versus input voltage at both 0 mA and 30 mA load conditions, confirming stable regulation across the line variation range.

### Transient Load Regulation

**Test Condition:** Fast current step from 0 mA → 30 mA at t = 1.0 µs, recovering at t = 3.0 µs.

| Metric | Value |
|---|---|
| Nominal DC Output Voltage | 1.0119 V |
| Maximum Undershoot | 989.51 mV (ΔV = 22.39 mV / 2.2%) |
| Overshoot | ~0.1 mV (negligible) |
| Recovery Voltage | 1.0128 V |
| Settling Behavior | Critically damped — zero ringing |

### PSRR

Power Supply Rejection Ratio (PSRR) was characterized across frequency to evaluate the regulator's ability to suppress supply noise at the output.

---

## Key Performance Summary

| Parameter | Simulated Value |
|---|---|
| Input Voltage (V_IN) | 1.2 V |
| Regulated Output Voltage (V_OUT) | 1.012 V |
| Max Design Load Current (I_LOAD) | 30 mA |
| Phase Margin (15 mA → 30 mA) | 81.2° → 81.8° |
| Transient Undershoot (ΔV_OUT) | 22.39 mV (2.2%) |
| Settling / Response Behavior | Critically Damped (No Ringing) |
| CMOS Process Node | 90 nm |

---

## Conclusion & Future Scope

### Conclusions

A fully functional, highly stable LDO voltage regulator was successfully designed and verified in 90nm CMOS technology. The hybrid two-stage error amplifier plus RC Miller compensation architecture achieves:

- Excellent phase margin (> 81°) across all active load conditions.
- Minimal transient undershoot (2.2%) with critically damped recovery.
- Robust closed-loop regulation from 0 mA to 30 mA load currents.

### Future Enhancements

- Introduce a small permanent on-chip dummy/bleed resistor (~50 µA) to stabilize loop gain at 0 mA load conditions.
- Conduct comprehensive PSRR simulations across wider frequency bands.
- Layout design and post-layout parasitic extraction (PEX) verification to validate performance with physical parasitics.

---

## References

1. M. Tiikkainen, *LDO Voltage Regulator for On-Chip Power Management*, Master's Thesis, Department of Electrical Engineering, University of Oulu, 2014, pp. 1–86.
2. P. Crepaldi, T. Pementa, and R. L. Moreno, "A CMOS Low Dropout Voltage Regulator," in *Proc. IEEE Conference*, 2010.
3. Y. Patil, "Design and Analysis of Low Voltage Dropout Regulator (LDO)," *IJSTE – International Journal of Science, Technology and Engineering*, vol. 1, 2015.
4. P. Liu, S. Huang, Q. Duan, Q. Zhu, and Z. Meng, "A Low-Quiescent Current Off-Chip Capacitor-Less LDO Regulator with UGCC Compensation," in *Proc. IEEE*, 2019.

---

*National Institute of Technology Arunachal Pradesh — B.Tech ECE Major Project*
