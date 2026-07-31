# 3.1 Introduction

Transient analysis evaluates the time-dependent behavior of the CMOS inverter when subjected to a time-varying input signal. Unlike DC analysis, which examines the steady-state relationship between input and output voltages, transient analysis studies how the inverter responds during switching events.

A pulse voltage source is applied to the inverter input, causing the output to alternate between logic HIGH and logic LOW. The resulting waveforms provide valuable insight into the inverter's dynamic performance, including charging and discharging behavior, propagation characteristics, and the influence of capacitive loading.

---

# 3.2 Theory of Transient Analysis

Transient analysis simulates the circuit response as a function of time.

When the input signal changes state, the PMOS and NMOS transistors alternately charge and discharge the output load capacitor. This charging and discharging process determines the switching characteristics of the inverter.

The transient response is influenced by:

- Input pulse characteristics
- Transistor drive strength
- Load capacitance
- Supply voltage
- Device parasitic capacitances

The generated waveforms form the basis for propagation delay, rise time, fall time, and power analyses presented in later chapters.

---

# 3.3 Why Transient Analysis?

Transient analysis is performed to verify the dynamic operation of the CMOS inverter under realistic switching conditions.

It helps to:

- Verify correct logic inversion.
- Observe dynamic switching behavior.
- Analyze output charging and discharging.
- Study the effect of capacitive loading.
- Validate the circuit before timing analysis.
- Generate waveforms for delay and power calculations.

---

# 3.4 Simulation Setup

A pulse voltage source is applied to the inverter input while a 0.25 pF load capacitor is connected to the output node.

The transient simulation records both the input and output voltages over time.

### Simulation Parameters

| Parameter | Value |
|-----------|------:|
| Technology | SKY130 Open PDK |
| Supply Voltage | 1.8 V |
| Analysis Type | Transient |
| Simulation Time | 40 ns |
| Time Step | 20 ps |
| Load Capacitance | 0.25 pF |

### 📷 Transient Testbench

> Insert the transient simulation testbench.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/03_Transient_analysis/photos/testbench.png" width="900">
</p>

---

# 3.5 Input Pulse Configuration

A pulse voltage source is used to repeatedly switch the CMOS inverter between logic LOW and logic HIGH.

### Pulse Parameters

| Parameter | Value |
|-----------|------:|
| Low Voltage | 0 V |
| High Voltage | 1.8 V |
| Rise Time | 100 ps |
| Fall Time | 100 ps |
| Pulse Width | 10 ns |
| Time Period | 20 ns |

The selected pulse parameters provide sufficient switching intervals to observe the complete charging and discharging behavior of the output capacitor.

### 📷 Input Waveform

> Insert the input waveform obtained from ngspice.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/03_Transient_analysis/photos/input.png" width="900">
</p>

---

# 3.6 Output Waveform

The output waveform demonstrates the inverter's response to the applied input pulse.

When the input transitions from LOW to HIGH, the NMOS transistor conducts and discharges the output capacitor, causing the output voltage to decrease toward ground.

When the input transitions from HIGH to LOW, the PMOS transistor conducts and charges the output capacitor, restoring the output voltage to VDD.

### 📷 Output Waveform

> Insert the output waveform obtained from ngspice.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/03_Transient_analysis/photos/inout.png" width="900">
</p>

---

# 3.7 Charging and Discharging of the Load Capacitor

The output capacitor plays a significant role in determining the inverter's transient response.

### Charging Process

When the input is LOW:

- PMOS turns ON.
- NMOS turns OFF.
- The output capacitor charges through the PMOS transistor.
- Output voltage increases toward VDD.

### Discharging Process

When the input is HIGH:

- PMOS turns OFF.
- NMOS turns ON.
- The output capacitor discharges through the NMOS transistor.
- Output voltage decreases toward ground.

### 📷 Charging and Discharging Waveform

> Insert waveform highlighting charging and discharging intervals.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/03_Transient_analysis/photos/capacitor charging due to pmos.png" width="900">
</p>

---

# 3.8 Effect of Load Capacitance

The load capacitor influences the dynamic performance of the CMOS inverter.

Increasing the load capacitance:

- Increases propagation delay.
- Increases rise time.
- Increases fall time.
- Increases dynamic power consumption.

Reducing the load capacitance:

- Improves switching speed.
- Reduces delay.
- Lowers dynamic power consumption.

These effects are investigated in greater detail in the timing and power analysis chapters.

### 📷 Output Capacitor in Testbench

> Insert screenshot showing the output load capacitor.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/03_Transient_analysis/photos/cap1p.png" width="900">
</p>
---
<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/03_Transient_analysis/photos/cap.50.png" width="900">
</p>
---

# 3.9 Engineering Observations

The following observations were made during transient analysis:

- The output correctly follows the logical inversion of the input signal.
- A full voltage swing between **0 V** and **1.8 V** is achieved.
- The output transitions exhibit finite rise and fall times due to the output load capacitance.
- Charging occurs through the PMOS transistor, while discharging occurs through the NMOS transistor.
- The transient response confirms the correct dynamic operation of the CMOS inverter.

---

# 3.10 Result Summary

| Parameter | Value |
|-----------|------:|
| Supply Voltage | 1.8 V |
| Simulation Time | 40 ns |
| Time Step | 20 ps |
| Load Capacitance | 0.25 pF |
| Input Signal | Pulse |
| Output Swing | 0 V – 1.8 V |

---

# ✅ Chapter Summary

Transient analysis successfully verified the dynamic switching behavior of the CMOS inverter. The generated input and output waveforms demonstrated correct logical inversion, while the charging and discharging of the output load capacitor confirmed proper transistor operation. The transient response obtained in this chapter serves as the foundation for the propagation delay, rise time, fall time, and power analyses presented in the following chapters.
