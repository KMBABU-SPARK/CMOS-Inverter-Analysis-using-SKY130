# ⚡ CMOS Inverter Design and Analysis using SKY130

> A complete engineering study of a CMOS inverter using the SKY130 Open PDK. This repository covers the entire design and characterization flow, including DC analysis, transient analysis, propagation delay, rise/fall time extraction, and power analysis using Xschem and ngspice.

---

# 📖 Overview

The CMOS inverter is the fundamental building block of modern digital integrated circuits. Understanding its behavior is essential for VLSI design, timing analysis, and power optimization.

This repository documents the complete workflow of designing and analyzing a CMOS inverter in the SKY130 technology node. Each section explains the theory, simulation setup, results, calculations, and engineering observations.

The project is organized as a reference guide so it can also serve as a revision notebook for future learning and interview preparation.

---

# 🎯 Objectives

The primary objectives of this project are:

- Design a CMOS inverter using SKY130 transistors
- Verify its voltage transfer characteristics
- Perform transient switching analysis
- Measure propagation delay
- Calculate rise and fall times
- Analyze dynamic power consumption
- Understand the impact of load capacitance on circuit performance

---

# 🛠 Software and Technology

| Tool | Purpose |
|------|----------|
| Xschem | Schematic Capture |
| ngspice | Circuit Simulation |
| SKY130 Open PDK | Technology Library |
| Ubuntu | Simulation Environment |

---
# 📚 Lessons

| No. | Chapter | Link |
|:---:|---------|------|
| 1️⃣ | CMOS Inverter Design | 🔗 [Go](https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/01_design/inverter_design.md) |
| 2️⃣ | DC Analysis (Voltage Transfer Characteristics) | 🔗 [Go](https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/02_DC_Analysis/dc_analysis.md) |
| 3️⃣ | Transient Analysis | 🔗 [Go](https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/03_Transient_analysis/Transient_analysis.md) |
| 4️⃣ | Propagation Delay Analysis | 🔗 [Go](https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/04_delay_analysis/delay_analysis.md) |
| 5️⃣ | Rise Time and Fall Time Analysis | 🔗 [Go](https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/05_rise_and_fall_time_analysis/rise_%26_fall_time_analysis.md) |
| 6️⃣ | Power Analysis | 🔗 [Go](https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/06_power_analysis/power_analysis.md) |


# 📚 Repository Contents

This repository is divided into multiple sections. Each section contains the theoretical background, simulation methodology, waveforms, calculations, observations, and conclusions.

---

## 1️⃣ CMOS Inverter Design

### Goal

Design the CMOS inverter using SKY130 PMOS and NMOS devices.

### Topics Covered

- CMOS inverter architecture
- PMOS and NMOS operation
- Device sizing
- Circuit schematic
- Testbench creation
- Input stimulus
- Load capacitance

### Deliverables

- Schematic
- SPICE Netlist
- Design Specifications
- Testbench

---

## 2️⃣ DC Analysis (Voltage Transfer Characteristics)

### Goal

Study the steady-state relationship between input and output voltages.

### Topics Covered

- DC Sweep
- Voltage Transfer Curve (VTC)
- Logic Levels
- Switching Threshold
- Noise Margins

### Deliverables

- DC Sweep Setup
- VTC Plot
- Switching Voltage
- Engineering Observations

---

## 3️⃣ Transient Analysis

### Goal

Verify the dynamic switching behavior of the CMOS inverter.

### Topics Covered

- Pulse Input
- Output Waveform
- Charging and Discharging
- Capacitive Effects

### Deliverables

- Input Waveform
- Output Waveform
- Simulation Parameters
- Observations

---

## 4️⃣ Propagation Delay Analysis

### Goal

Measure the delay introduced by the inverter during logic transitions.

### Topics Covered

- tPHL
- tPLH
- Average Propagation Delay
- Delay Measurement Methodology

### Deliverables

- Delay Measurement Commands
- Waveforms
- Calculations
- Results

---

## 5️⃣ Rise Time and Fall Time Analysis

### Goal

Measure the output transition speed.

### Topics Covered

- Rise Time (10%–90%)
- Fall Time (90%–10%)
- Effect of Load Capacitance
- Switching Characteristics

### Deliverables

- Rise Time Calculation
- Fall Time Calculation
- Waveforms
- Discussion

---

## 6️⃣ Power Analysis

### Goal

Measure the power consumed by the CMOS inverter.

### Topics Covered

- Static Power
- Dynamic Power
- Supply Current
- Current Integration
- Average Power Calculation

### Deliverables

- Supply Current Plot
- Power Calculation
- ngspice Measurements
- Discussion

---

# 🧠 Engineering Workflow

```text
Circuit Design
      │
      ▼
Create Testbench
      │
      ▼
DC Analysis
      │
      ▼
Transient Analysis
      │
      ▼
Propagation Delay
      │
      ▼
Rise/Fall Time
      │
      ▼
Power Analysis
      │
      ▼
Engineering Conclusions
```

---

# 📂 Standard Structure for Every Section

Each analysis chapter follows the same format to maintain consistency.

1. Objective
2. Theory
3. Circuit Setup
4. Simulation Parameters
5. SPICE Commands
6. Waveforms
7. Calculations
8. Results
9. Engineering Observations
10. Conclusion

---

# 📖 Key Learning Outcomes

After completing this repository, you will understand:

- CMOS inverter operation
- CMOS switching characteristics
- Voltage Transfer Curve (VTC)
- DC simulation
- Transient simulation
- Propagation delay
- Rise and fall time extraction
- Dynamic and static power
- SPICE measurements
- SKY130 PDK workflow
- Xschem design flow
- ngspice simulation techniques

---

# 🎯 Skills Demonstrated

- CMOS Circuit Design
- Analog Simulation
- Device-Level Analysis
- Timing Characterization
- Power Characterization
- Xschem
- ngspice
- SKY130 Open PDK
- SPICE Netlisting
- Engineering Documentation

---


# 📚 References

- SKY130 Open PDK Documentation
- ngspice User Manual
- CMOS VLSI Design – Weste & Harris
- Digital Integrated Circuits – Jan M. Rabaey
