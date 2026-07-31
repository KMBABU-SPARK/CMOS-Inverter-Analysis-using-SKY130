# 2.1 Introduction

DC analysis is performed to evaluate the steady-state behavior of the CMOS inverter by gradually varying the input voltage while observing the corresponding output voltage. Unlike transient analysis, which studies time-dependent switching behavior, DC analysis focuses on the static electrical characteristics of the circuit.

The relationship between the input voltage (VIN) and the output voltage (VOUT) is represented by the **Voltage Transfer Characteristic (VTC)**. The VTC curve provides valuable information about the inverter's switching behavior, logic levels, voltage gain, switching threshold, and noise immunity.

The DC characteristics obtained in this chapter serve as the basis for evaluating the robustness and reliability of the CMOS inverter.

---

# 2.2 Theory of DC Analysis

A DC sweep analysis determines the output voltage of the inverter for every input voltage between **0 V** and **VDD** under steady-state conditions.

During the sweep, the input voltage is increased incrementally while the simulator calculates the corresponding output voltage. The resulting Voltage Transfer Characteristic (VTC) illustrates the inverter's transition from Logic HIGH to Logic LOW.

The VTC curve is used to determine important static parameters such as:

- Logic HIGH output voltage (VOH)
- Logic LOW output voltage (VOL)
- Switching Threshold Voltage (VM)
- Noise Margins (NMH and NML)
- Transition Region
- Voltage Gain

---

# 2.3 Why DC Analysis?

DC analysis is one of the most important characterization techniques for digital circuits because it provides insight into the static behavior of the inverter before timing analysis is performed.

It helps to:

- Verify correct inverter functionality.
- Determine the switching threshold voltage.
- Evaluate logic HIGH and logic LOW voltage levels.
- Measure the transition characteristics.
- Estimate the noise immunity of the circuit.
- Validate the inverter design before transient analysis.

---

# 2.4 DC Sweep Setup

A DC voltage source is connected to the inverter input, and the input voltage is swept from **0 V** to **1.8 V**.

The output voltage is recorded for every input voltage, resulting in the Voltage Transfer Characteristic (VTC).

### DC Sweep Parameters

| Parameter | Value |
|-----------|------:|
| Technology | SKY130 Open PDK |
| Supply Voltage (VDD) | 1.8 V |
| Input Sweep | 0 V → 1.8 V |
| Sweep Step | 10 mV *(0.01 V)* |
| Analysis Type | DC Sweep |

### 📷 DC Sweep Testbench

> Insert the Xschem testbench configured for DC analysis.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/02_DC_Analysis/Photos/tb.png" width="900">
</p>

---

# 2.5 SPICE Simulation Commands

The following SPICE commands are used to perform the DC sweep.

```spice
.lib sky130.lib.spice tt

.dc Vin 0 1.8 0.01

.save all

.end
```

### Description of Commands

| Command | Purpose |
|----------|----------|
| `.lib` | Loads the SKY130 transistor models |
| `.dc` | Performs a DC sweep of the input voltage |
| `.save` | Saves all simulation variables |
| `.end` | Ends the SPICE netlist |

---

# 2.6 Voltage Transfer Characteristic (VTC)

The Voltage Transfer Characteristic (VTC) is obtained by plotting the output voltage (VOUT) against the input voltage (VIN).

The VTC demonstrates the inverter's ability to produce a full logic swing while rapidly transitioning between logic states.

A steep transition region indicates high voltage gain and good switching performance.

### 📷 Voltage Transfer Curve

> Insert your ngspice VTC plot here.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/02_DC_Analysis/Photos/ipop.png" width="900">
</p>

### Observation

- Output remains close to **VDD** for low input voltages.
- Output rapidly transitions near the switching threshold.
- Output approaches **0 V** for high input voltages.
- Full voltage swing is achieved.

---

# 2.7 Logic Levels

The logic levels define the valid HIGH and LOW voltage ranges of the CMOS inverter.

| Parameter | Description | Value |
|-----------|-------------|------:|
| VOH | Logic HIGH Output Voltage | *(Measured)* |
| VOL | Logic LOW Output Voltage | *(Measured)* |
| VIH | Minimum Input Voltage recognized as HIGH | *(Measured)* |
| VIL | Maximum Input Voltage recognized as LOW | *(Measured)* |

The logic levels are extracted directly from the Voltage Transfer Characteristic.

### 📷 Logic Levels on VTC

> Insert annotated VTC showing VOH, VOL, VIH, and VIL.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/02_DC_Analysis/Photos/Your paragraph text.png" width="900">
</p>

---

# 2.8 Switching Threshold Voltage

The switching threshold voltage (**VM**) is the input voltage at which the output voltage equals the input voltage.

At this operating point, both the PMOS and NMOS transistors conduct simultaneously, and the inverter exhibits its highest voltage gain.

An ideally symmetric CMOS inverter has a switching threshold close to **VDD / 2**.

### Switching Threshold

| Parameter | Symbol | Value |
|-----------|--------|------:|
| Switching Threshold | VM | *(Measured)* |

### 📷 Switching Threshold on VTC

> Insert VTC with the switching threshold marked.

<p align="center">
<img src="images/switching_threshold.png" width="900">
</p>

---

# 2.9 Noise Margins

Noise margins quantify the inverter's ability to tolerate unwanted electrical noise without changing its logic state.

They are calculated as:

```text
NMH = VOH − VIH

NML = VIL − VOL
```

Larger noise margins indicate better immunity to electrical disturbances and improved reliability.

### Noise Margin Summary

| Parameter | Formula | Value |
|-----------|----------|------:|
| High Noise Margin | VOH − VIH | *(Calculated)* |
| Low Noise Margin | VIL − VOL | *(Calculated)* |

### 📷 Noise Margins on VTC

> Insert annotated VTC highlighting NMH and NML.

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/02_DC_Analysis/Photos/noise_margin.png" width="900">
</p>

---

# 2.10 Engineering Observations

The following observations were made from the DC analysis:

- The inverter exhibits proper voltage inversion.
- A full logic swing from **0 V** to **1.8 V** is achieved.
- The transition region is steep, indicating high voltage gain.
- The switching threshold is close to the expected value.
- The noise margins indicate good noise immunity.
- The DC characteristics confirm the correct operation of the CMOS inverter.

---

# 2.11 Result Summary

| Parameter | Symbol | Value |
|-----------|--------|------:|
| Supply Voltage | VDD | 1.8 V |
| Logic HIGH Output | VOH | *(Measured)* |
| Logic LOW Output | VOL | *(Measured)* |
| Switching Threshold | VM | *(Measured)* |
| High Noise Margin | NMH | *(Calculated)* |
| Low Noise Margin | NML | *(Calculated)* |

---

# ✅ Chapter Summary

The CMOS inverter was successfully characterized using DC sweep analysis in ngspice. The generated Voltage Transfer Characteristic (VTC) verified the correct steady-state operation of the inverter and provided key parameters such as the logic levels, switching threshold voltage, and noise margins. These results demonstrate the inverter's excellent static performance and establish the foundation for the transient, timing, and power analyses presented in the subsequent chapters.
