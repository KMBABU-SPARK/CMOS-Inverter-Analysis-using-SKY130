# 4.1 Introduction

Propagation delay is one of the most important timing parameters of a CMOS inverter. It represents the finite time required for the output to respond to a change in the input signal. This delay occurs because the output load capacitor must be charged and discharged through the PMOS and NMOS transistors, respectively.

During switching, the transistors require a finite amount of time to change the output voltage, resulting in a delay between the input and output transitions. Measuring this delay is essential for evaluating the speed and performance of digital circuits.

---

# 4.2 Theory of Propagation Delay

When the input of the CMOS inverter changes state, the output does not switch instantaneously.

The delay is primarily caused by:

- Charging of the load capacitor through the PMOS transistor.
- Discharging of the load capacitor through the NMOS transistor.
- Internal transistor capacitances.
- Finite transistor switching speed.
- Output load capacitance.

Propagation delay is measured at the **50% voltage level** of both the input and output waveforms.

Since the supply voltage is **1.8 V**, the 50% reference voltage used for propagation delay measurement is:

**50% × 1.8 V = 0.9 V**

The average propagation delay is calculated as:

**Average Propagation Delay = (tPHL + tPLH) / 2**

The propagation delay consists of two components:

- **tPHL** – Output transition from HIGH to LOW.
- **tPLH** – Output transition from LOW to HIGH.

---

# 4.3 Why Propagation Delay Analysis?

Propagation delay analysis is performed to evaluate the switching speed of the CMOS inverter.

It helps to:

- Measure inverter switching speed.
- Determine circuit timing performance.
- Compare different inverter designs.
- Study the influence of load capacitance.
- Validate timing requirements for digital circuits.
- Estimate maximum operating frequency.

---

# 4.4 Simulation Setup

The same transient simulation setup used in the previous chapter is employed for propagation delay measurement.

A pulse voltage source drives the inverter input while the output is connected to a **0.25 pF** load capacitor.

The delay is measured by comparing the input and output waveforms at the **50% voltage level (0.9 V).**

### Simulation Parameters

| Parameter | Value |
|-----------|------:|
| Technology | SKY130 Open PDK |
| Supply Voltage | 1.8 V |
| Analysis Type | Transient |
| Simulation Time | 40 ns |
| Time Step | 20 ps |
| Load Capacitance | 0.25 pF |

### 📷 Propagation Delay Testbench

> Insert the transient simulation testbench used for delay measurement.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/04_delay_analysis/photos/tb.png" width="900">
</p>

---

# 4.5 Delay Measurement Methodology

Propagation delay is measured using the transient waveforms obtained from ngspice.

The measurement is performed as follows:

### High-to-Low Delay (tPHL)

- Input transitions from LOW to HIGH.
- Output transitions from HIGH to LOW.
- Measure the time difference between the input and output crossing **0.9 V**.

### Low-to-High Delay (tPLH)

- Input transitions from HIGH to LOW.
- Output transitions from LOW to HIGH.
- Measure the time difference between the input and output crossing **0.9 V**.

The average propagation delay is then calculated using
**Average Propagation Delay = (tPHL + tPLH) / 2**
### 📷 Delay Measurement Waveform

> Insert the waveform showing the 50% delay measurement points.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/04_delay_analysis/photos/op.png" width="900">
</p>

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/04_delay_analysis/photos/tphl.png" width="900">
</p>

---

# 4.6 Delay Measurement Commands

The following ngspice commands are used to measure the propagation delays automatically.

```spice
.control
run

meas tran tphl TRIG v(vin) VAL=0.9 RISE=1 \
+ TARG v(vout) VAL=0.9 FALL=1

meas tran tplh TRIG v(vin) VAL=0.9 FALL=1 \
+ TARG v(vout) VAL=0.9 RISE=1

let tpd=(tphl+tplh)/2

print tphl tplh tpd

.endc
```

The measured values are displayed in the ngspice console after simulation.

### 📷 ngspice Measurement Output

> Insert screenshot of the ngspice console displaying `tPHL`, `tPLH`, and `tpd`.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/04_delay_analysis/photos/scematic_data.png" width="900">
</p>

---

# 4.7 Delay Calculations

After obtaining the measured values from ngspice, the average propagation delay is calculated.

### Example Calculation

| Parameter | Value |
|-----------|------:|
| tPHL | 147.73 ps |
| tPLH | 192.90 ps |

Average propagation delay:
**Average Propagation Delay = (tPHL + tPLH) / 2**
| Parameter | Value |
|-----------|------:|
| tPD | 170.315 ps |


Replace the example values with the measured results obtained from simulation.

---

# 4.8 Results

The measured propagation delay values are summarized below.

| Parameter | Value |
|-----------|------:|
| Supply Voltage | 1.8 V |
| Load Capacitance | 0.25 pF |
| tPHL | 147.73 ps |
| tPLH | 192.90 ps |
| Average Delay | 170.315 ps |

---

# 4.9 Engineering Observations

The following observations were made during propagation delay analysis:

- The output does not switch instantaneously after the input transition.
- The propagation delay is caused by charging and discharging of the output load capacitor.
- The HIGH-to-LOW and LOW-to-HIGH delays may differ due to the different drive strengths of the NMOS and PMOS transistors.
- Delay increases as the output load capacitance increases.
- The measured propagation delay confirms the expected timing behavior of the CMOS inverter.

---

# 4.10 Result Summary

| Parameter | Value |
|-----------|------:|
| Technology | SKY130 Open PDK |
| Supply Voltage | 1.8 V |
| Analysis Type | Transient |
| Load Capacitance | 0.25 pF |
| tPHL | 147.73 ps |
| tPLH | 192.90 ps |
| Average Delay | 170.315 ps |

---

# ✅ Chapter Summary

Propagation delay analysis successfully quantified the switching speed of the CMOS inverter. The delay measurements obtained from transient simulation demonstrated the finite time required for the output to respond to changes in the input signal. The measured values of **tPHL**, **tPLH**, and the **average propagation delay** provide an accurate assessment of the inverter's timing performance and serve as key parameters for evaluating the speed of CMOS digital circuits.
