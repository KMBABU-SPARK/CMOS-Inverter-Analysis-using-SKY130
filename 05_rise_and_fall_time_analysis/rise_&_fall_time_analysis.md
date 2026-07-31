# 5.1 Introduction

Rise time and fall time are important transient parameters used to evaluate the switching speed of a CMOS inverter. They describe how quickly the output voltage transitions between logic levels during switching events.

The rise time measures the time required for the output voltage to increase from a LOW level to a HIGH level, while the fall time measures the time required for the output voltage to decrease from a HIGH level to a LOW level.

These parameters directly influence the operating speed, signal integrity, and overall performance of digital circuits.

---

# 5.2 Theory of Rise Time and Fall Time

The output transition of a CMOS inverter is governed by the charging and discharging of the output load capacitor.

### Rise Time (tr)

Rise time is defined as the time required for the output voltage to increase from **10%** to **90%** of the supply voltage.

During this transition:

- PMOS transistor turns ON.
- NMOS transistor turns OFF.
- The output load capacitor charges toward VDD.

For a supply voltage of **1.8 V**:

- 10% of VDD = **0.18 V**
- 90% of VDD = **1.62 V**

Rise time is measured as

\[
t_r=t_{90\%}-t_{10\%}
\]

---

### Fall Time (tf)

Fall time is defined as the time required for the output voltage to decrease from **90%** to **10%** of the supply voltage.

During this transition:

- NMOS transistor turns ON.
- PMOS transistor turns OFF.
- The output load capacitor discharges to ground.

For a supply voltage of **1.8 V**:

- 90% of VDD = **1.62 V**
- 10% of VDD = **0.18 V**

Fall time is measured as

\[
t_f=t_{10\%}-t_{90\%}
\]

---

# 5.3 Why Rise Time and Fall Time Analysis?

Rise time and fall time analysis is performed to evaluate the output transition speed of the CMOS inverter.

It helps to:

- Measure output switching speed.
- Evaluate signal integrity.
- Analyze charging and discharging performance.
- Study the effect of load capacitance.
- Compare inverter performance under different loading conditions.
- Validate timing performance for high-speed digital circuits.

---

# 5.4 Simulation Setup

The transient simulation setup used in previous analyses is employed for rise and fall time measurements.

A pulse voltage source drives the inverter input, while a **0.25 pF** load capacitor is connected to the output node.

The output waveform is analyzed to determine the transition time between the **10%** and **90%** voltage levels.

### Simulation Parameters

| Parameter | Value |
|-----------|------:|
| Technology | SKY130 Open PDK |
| Supply Voltage | 1.8 V |
| Analysis Type | Transient |
| Simulation Time | 40 ns |
| Time Step | 20 ps |
| Load Capacitance | 0.25 pF |

### 📷 Rise/Fall Time Testbench

> Insert the transient simulation testbench.

<p align="center">
<img src="images/rise_fall_testbench.png" width="900">
</p>

---

# 5.5 Rise Time Measurement

Rise time is measured from the output waveform during the LOW-to-HIGH transition.

Measurement steps:

- Locate the point where the output reaches **0.18 V (10%)**.
- Locate the point where the output reaches **1.62 V (90%)**.
- Calculate the time difference.

### Rise Time Formula

\[
t_r=t_{90\%}-t_{10\%}
\]

### 📷 Rise Time Waveform

> Insert waveform highlighting the 10% and 90% rise points.

<p align="center">
<img src="images/rise_time_waveform.png" width="900">
</p>

---

# 5.6 Fall Time Measurement

Fall time is measured from the output waveform during the HIGH-to-LOW transition.

Measurement steps:

- Locate the point where the output reaches **1.62 V (90%)**.
- Locate the point where the output reaches **0.18 V (10%)**.
- Calculate the time difference.

### Fall Time Formula

\[
t_f=t_{10\%}-t_{90\%}
\]

### 📷 Fall Time Waveform

> Insert waveform highlighting the 90% and 10% fall points.

<p align="center">
<img src="images/fall_time_waveform.png" width="900">
</p>

---

# 5.7 Effect of Load Capacitance

The output load capacitance significantly affects the transition speed of the CMOS inverter.

### Increasing Load Capacitance

- Increases rise time.
- Increases fall time.
- Slows charging and discharging.
- Reduces switching speed.
- Increases dynamic power consumption.

### Reducing Load Capacitance

- Decreases rise time.
- Decreases fall time.
- Improves switching speed.
- Reduces dynamic power consumption.

### 📷 Comparison of Output Waveforms

> Insert waveforms comparing different load capacitances.

<p align="center">
<img src="images/load_capacitance_comparison.png" width="900">
</p>

---

# 5.8 Switching Characteristics

The switching characteristics of the CMOS inverter are evaluated using the measured rise and fall times.

A fast inverter exhibits:

- Small rise time.
- Small fall time.
- Sharp output transitions.
- High switching speed.
- Improved timing performance.

Differences between rise and fall times arise due to the unequal drive strengths of the PMOS and NMOS transistors.

---

# 5.9 Calculations

The measured rise and fall times are obtained directly from the transient waveforms.

### Example Calculation

| Parameter | Value |
|-----------|------:|
| Rise Time | XX ps |
| Fall Time | XX ps |

Replace the example values with the measured results obtained from ngspice.

---

# 5.10 Results

| Parameter | Value |
|-----------|------:|
| Supply Voltage | 1.8 V |
| Load Capacitance | 0.25 pF |
| Rise Time | XX ps |
| Fall Time | XX ps |

---

# 5.11 Engineering Observations

The following observations were made during rise and fall time analysis:

- The output transitions smoothly between logic levels due to the charging and discharging of the load capacitor.
- Rise time corresponds to charging through the PMOS transistor.
- Fall time corresponds to discharging through the NMOS transistor.
- Larger load capacitance increases both rise and fall times.
- The measured transition times confirm the expected switching characteristics of the CMOS inverter.

---

# 5.12 Result Summary

| Parameter | Value |
|-----------|------:|
| Technology | SKY130 Open PDK |
| Supply Voltage | 1.8 V |
| Analysis Type | Transient |
| Load Capacitance | 0.25 pF |
| Rise Time | XX ps |
| Fall Time | XX ps |

---

# ✅ Chapter Summary

Rise time and fall time analysis successfully evaluated the output transition speed of the CMOS inverter. The transient waveforms demonstrated the charging and discharging behavior of the output load capacitor, allowing accurate measurement of the output transition times. The measured rise and fall times provide valuable insight into the switching performance of the inverter and form an essential basis for evaluating the timing characteristics of CMOS digital circuits.
