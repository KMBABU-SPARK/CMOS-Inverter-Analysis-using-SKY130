# 6.1 Introduction

Power consumption is a critical performance parameter in CMOS digital circuits. Although CMOS technology is well known for its low static power consumption, power is dissipated during switching due to the charging and discharging of the output load capacitor.

Power analysis evaluates both the instantaneous and average power consumed by the CMOS inverter during operation. It provides insight into the energy efficiency of the circuit and helps optimize digital designs for low-power applications.

---

# 6.2 Theory of Power Consumption

The total power consumed by a CMOS inverter consists of two primary components:

- Static Power
- Dynamic Power

### Static Power

Static power is the power consumed when the inverter is in a stable logic state (either logic HIGH or logic LOW).

Ideally,

- One transistor is ON.
- The other transistor is OFF.
- No direct current flows from VDD to ground.

Therefore, the static power consumption of an ideal CMOS inverter is nearly zero.

In practical CMOS technologies, a very small leakage current exists, resulting in a small amount of static power dissipation.

---

### Dynamic Power

Dynamic power is consumed during switching events when the output load capacitor is repeatedly charged and discharged.

Dynamic power depends on:

- Supply voltage
- Switching frequency
- Load capacitance
- Switching activity

The dynamic power is given by

**Dynamic Power = Cₗ × VDD² × f**

where

- \(C_L\) = Load capacitance
- \(V_{DD}\) = Supply voltage
- \(f\) = Switching frequency

---

# 6.3 Why Power Analysis?

Power analysis is performed to evaluate the energy efficiency of the CMOS inverter.

It helps to:

- Measure static power consumption.
- Measure dynamic power consumption.
- Observe supply current during switching.
- Calculate average power consumption.
- Study the effect of capacitive loading.
- Evaluate the suitability of the inverter for low-power applications.

---

# 6.4 Simulation Setup

Power analysis is carried out using the same transient simulation setup employed in the previous chapters.

The supply current flowing from the voltage source is monitored throughout the simulation, and the instantaneous power is calculated using the supply voltage and current.

### Simulation Parameters

| Parameter | Value |
|-----------|------:|
| Technology | SKY130 Open PDK |
| Supply Voltage | 1.8 V |
| Analysis Type | Transient |
| Simulation Time | 40 ns |
| Time Step | 20 ps |
| Load Capacitance | 0.25 pF |

### 📷 Power Analysis Testbench

> Insert the transient simulation testbench used for power analysis.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/06_power_analysis/photos/tb.png" width="900">
</p>

---

# 6.5 Supply Current Analysis

The current drawn from the power supply is measured during transient simulation.

The supply current remains very small during steady-state operation and exhibits sharp current pulses whenever the inverter switches.

These current spikes correspond to:

- Charging of the output capacitor.
- Discharging of the output capacitor.
- Brief simultaneous conduction of PMOS and NMOS during switching.

### 📷 Supply Current Waveform

> Insert the supply current waveform obtained from ngspice.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/06_power_analysis/photos/output.png" width="900">
</p>

---

# 6.6 Current Integration

The total energy consumed during simulation is determined by integrating the supply current over the simulation interval.

The instantaneous power is given by

**Instantaneous Power = Supply Voltage × Supply Current**

**P(t) = VDD × IDD(t)**

The total energy consumed is

**Total Energy Consumed = ∫ Instantaneous Power × dt**

**E = ∫ P(t) dt**
where

- \(P(t)\) = Instantaneous power
- \(I_{DD}(t)\) = Supply current
- \(T\) = Simulation time

Current integration provides the basis for calculating the average power consumed by the inverter.

---

# 6.7 Average Power Calculation

The average power is calculated from the total energy consumed during the simulation period.

The average power is given by

**Average Power = Total Energy / Measurement Time**

**Pavg = E / T**

Alternatively,

**Average Power = Supply Voltage × Average Supply Current**

**Pavg = VDD × Iavg**

where

- \(I_{avg}\) = Average supply current

### Example Calculation

| Parameter | Value |
|-----------|------:|
| Supply Voltage | 1.8 V |
| Average Current | 23.44 µA |

Average Power

**Average Power = Supply Voltage × Average Supply Current**

**Pavg = VDD × Iavg**

**= 1.8 × 23.44 µA**

**= 42.20 µW**
---

# 6.8 ngspice Measurement Commands

The following commands can be used to measure the supply current and average power automatically.

# 1.average supply current
```spice
.control
run

meas tran charge integ vcc#branch from=20n to=40n
let iavg = abs(charge)/20e-9

print iavg

.endc
```
# 2.average power
```spice
.control
run

meas tran charge integ vcc#branch from=20n to=40n
let iavg = abs(charge)/20e-9
let pavg = 1.8*iavg

print pavg

.endc
```
# 3.Static power
```spice
.control
run

meas tran q_static integ vcc#branch from=22n to=28n

let istatic = abs(q_static)/6e-9
let pstatic = 1.8*istatic

print istatic
print pstatic

.endc
```
# 4.dynamic_power=avg_power-static_power

The measured values are displayed in the ngspice console after the simulation.

### 📷 ngspice Measurement Output

> Insert screenshot showing the measured average current and average power.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/06_power_analysis/photos/SIM.png" width="900">
</p>

---

# 6.9 Results

The measured power consumption is summarized below.

| Parameter | Value |
|-----------|------:|
| Supply Voltage | 1.8 V |
| Load Capacitance | 0.25 pF |
| Average Supply Current | 23.44 µA |
| Static Power | 0.022 nW |
| Dynamic Power | 42.20 µW |
| Average Power | 42.22 µW |

---

# 6.10 Engineering Observations

The following observations were made during power analysis:

- The supply current is nearly zero during steady-state operation.
- Current spikes occur only during output transitions.
- Dynamic power dominates the overall power consumption.
- Static power remains very small due to the low leakage characteristics of CMOS technology.
- Increasing the load capacitance increases the switching current and average power consumption.
- The measured results confirm the low-power characteristics of the CMOS inverter.

---

# 6.11 Result Summary

| Parameter | Value |
|-----------|------:|
| Technology | SKY130 Open PDK |
| Supply Voltage | 1.8 V |
| Analysis Type | Transient |
| Load Capacitance | 0.25 pF |
| Average Supply Current | 23.44 µA |
| Static Power | 0.022 nW |
| Dynamic Power | 42.20 µW |
| Average Power | 42.22 µW |

---

# ✅ Chapter Summary

Power analysis successfully evaluated the energy consumption characteristics of the CMOS inverter. The transient simulation demonstrated that the inverter draws negligible current during steady-state operation, while current spikes occur during switching due to charging and discharging of the output load capacitor. The measured supply current, static power, dynamic power, and average power confirm the high energy efficiency of CMOS technology and provide important metrics for assessing inverter performance in low-power digital circuit applications.
