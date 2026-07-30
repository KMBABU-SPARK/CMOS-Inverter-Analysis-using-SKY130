# 📖 Chapter 1: CMOS Inverter Design and Testbench Development

> This chapter focuses on the complete design of a CMOS inverter using the SKY130 Open PDK. It covers the inverter architecture, working principle, testbench development, simulation setup, and design specifications. This chapter serves as the foundation for all subsequent analyses, including DC analysis, transient analysis, propagation delay, rise/fall time, and power analysis.

---

# 📑 Table of Contents

- [1.1 Introduction](#11-introduction)
- [1.2 Objectives](#12-objectives)
- [1.3 CMOS Inverter Theory](#13-cmos-inverter-theory)
- [1.4 CMOS Inverter Architecture](#14-cmos-inverter-architecture)
- [1.5 Circuit Schematic](#15-circuit-schematic)
- [1.6 Testbench Development](#16-testbench-development)
- [1.7 Design Specifications](#17-design-specifications)
- [1.8 Input Stimulus](#18-input-stimulus)
- [1.9 Simulation Setup](#19-simulation-setup)
- [1.10 Working Principle](#110-working-principle)
- [1.11 Truth Table](#111-truth-table)
- [1.12 Design Considerations](#112-design-considerations)
- [1.13 Files Used](#113-files-used)
- [1.14 Skills Demonstrated](#114-skills-demonstrated)
- [1.15 Key Takeaways](#115-key-takeaways)
- [1.16 Common Mistakes](#116-common-mistakes)
- [1.17 Interview Questions](#117-interview-questions)

---

# 1.1 Introduction

The CMOS (Complementary Metal-Oxide-Semiconductor) inverter is the most fundamental building block of modern digital integrated circuits. Nearly every digital system—including logic gates, multiplexers, flip-flops, memories, microprocessors, and application-specific integrated circuits (ASICs)—is ultimately constructed using CMOS inverters.

A CMOS inverter consists of two complementary MOS transistors:

- PMOS (Pull-Up Network)
- NMOS (Pull-Down Network)

The complementary switching action of these transistors enables:

- Full logic swing
- High noise immunity
- Low static power consumption
- High switching speed
- Excellent scalability

In this chapter, the CMOS inverter is designed using the **SKY130 Open PDK**, and a complete simulation-ready testbench is developed using **Xschem** and **ngspice**.

---

# 1.2 Objectives

The objectives of this chapter are to:

- Design a CMOS inverter using SKY130 transistors.
- Develop a simulation-ready testbench.
- Configure the power supply and input stimulus.
- Apply a realistic capacitive load.
- Prepare the design for characterization.
- Establish the foundation for all subsequent analyses.

---

# 1.3 CMOS Inverter Theory

A CMOS inverter is composed of a PMOS transistor connected between the output and the power supply (VDD) and an NMOS transistor connected between the output and ground (GND).

Both transistor gates are connected together to form the input, while their drains are connected together to produce the output.

The inverter operates by ensuring that only one transistor conducts during steady-state operation.

- When the input is LOW, the PMOS conducts and the NMOS remains OFF.
- When the input is HIGH, the NMOS conducts and the PMOS remains OFF.

This complementary operation minimizes static power consumption while maintaining full voltage swing at the output.

---

# 1.4 CMOS Inverter Architecture

The CMOS inverter consists of the following components.

| Component | Description |
|-----------|-------------|
| PMOS | Pull-Up Network |
| NMOS | Pull-Down Network |
| VDD | Power Supply |
| GND | Ground |
| VIN | Input Node |
| VOUT | Output Node |
| CL | Output Load Capacitor |

---

# 1.5 Circuit Schematic

## CMOS Inverter Schematic

> **Insert the CMOS inverter schematic here.**

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/01_design/images/Screenshot%202026-07-31%20005538.png" width="850">
</p>

**Figure 1.** CMOS inverter designed using SKY130 PMOS and NMOS devices in Xschem.

---

# 1.6 Testbench Development

To verify the inverter, a simulation testbench is created.

The testbench consists of:

- CMOS Inverter
- DC Power Supply (1.8 V)
- Pulse Voltage Source
- Capacitive Load
- Ground Reference

## Testbench

> **Insert the complete testbench image here.**

<p align="center">
<img src="https://github.com/KMBABU-SPARK/CMOS-Inverter-Analysis-using-SKY130/blob/main/01_design/images/Screenshot%202026-07-31%010035.png" width="900">
</p>

**Figure 2.** Simulation testbench used for all analyses.

---

# 1.7 Design Specifications

| Parameter | Value |
|-----------|------:|
| Technology | SKY130 Open PDK |
| Process Corner | TT (Typical-Typical) |
| Supply Voltage | 1.8 V |
| PMOS Device | sky130_fd_pr__pfet_01v8 |
| NMOS Device | sky130_fd_pr__nfet_01v8 |
| Load Capacitance | 0.25 pF |
| Simulator | ngspice |
| Schematic Tool | Xschem |

---

# 1.8 Input Stimulus

A pulse voltage source is used to repeatedly switch the inverter between logic LOW and logic HIGH.

| Parameter | Value |
|-----------|------:|
| Low Voltage | 0 V |
| High Voltage | 1.8 V |
| Rise Time | 100 ps |
| Fall Time | 100 ps |
| Pulse Width | 10 ns |
| Time Period | 20 ns |

---

# 1.9 Simulation Setup

The following SPICE commands are used to prepare the circuit for simulation.

```spice
.lib sky130.lib.spice tt

.tran 20p 40n

.save all
```

### Description of Commands

| Command | Purpose |
|----------|----------|
| `.lib` | Loads the SKY130 transistor models |
| `.tran` | Performs transient simulation |
| `.save` | Saves node voltages and currents |

---

# 1.10 Working Principle

## Case 1: Input = Logic LOW (0 V)

- PMOS turns ON.
- NMOS remains OFF.
- Output is connected to VDD.
- Output becomes Logic HIGH (1.8 V).

---

## Case 2: Input = Logic HIGH (1.8 V)

- PMOS turns OFF.
- NMOS turns ON.
- Output is connected to Ground.
- Output becomes Logic LOW (0 V).

---

# 1.11 Truth Table

| Input (VIN) | PMOS | NMOS | Output (VOUT) |
|-------------|------|------|---------------|
| 0 V | ON | OFF | 1.8 V |
| 1.8 V | OFF | ON | 0 V |

---

# 1.12 Design Considerations

The following considerations were taken into account during the design process:

- Use of the SKY130 Open PDK for realistic device modeling.
- Supply voltage selected as **1.8 V**, which is the nominal operating voltage for the SKY130 1.8 V devices.
- Addition of a **0.25 pF load capacitor** to represent practical output loading.
- Selection of the **TT (Typical-Typical)** process corner for nominal performance evaluation.
- Use of a pulse voltage source to emulate digital switching conditions.
- Proper body terminal connections for both PMOS and NMOS devices.

---

# 1.13 Files Used

| File | Description |
|------|-------------|
| `inverter.sch` | Xschem schematic |
| `inverter.spice` | Generated SPICE netlist |
| `sky130.lib.spice` | SKY130 device models |
| `README.md` | Project documentation |

---

# 1.14 Skills Demonstrated

- CMOS Circuit Design
- Digital Circuit Fundamentals
- Xschem Schematic Capture
- SKY130 Open PDK
- ngspice Simulation
- SPICE Netlisting
- Testbench Development
- VLSI Design Documentation

---

# 1.15 Key Takeaways

- Successfully designed a CMOS inverter using SKY130 PMOS and NMOS devices.
- Developed a complete simulation-ready testbench.
- Configured the circuit with a 1.8 V supply and a pulse input source.
- Applied a realistic capacitive load for performance evaluation.
- Established a reusable foundation for DC, transient, timing, and power analyses.

---

# 1.16 Common Mistakes

- Incorrect PMOS source/drain connections.
- Connecting the PMOS source to GND instead of VDD.
- Omitting body terminal connections.
- Forgetting to include the SKY130 model library.
- Using incorrect pulse source parameters.
- Neglecting the output load capacitor.
- Incorrect grounding of the circuit.

---

# 1.17 Interview Questions

### Q1. Why is the CMOS inverter considered the fundamental building block of digital circuits?

**Answer:** Because all complex digital circuits, such as logic gates, multiplexers, flip-flops, memories, and processors, are ultimately constructed using CMOS inverters.

---

### Q2. Why does a CMOS inverter consume very little static power?

**Answer:** During steady-state operation, either the PMOS or the NMOS transistor is OFF, preventing a direct current path between VDD and GND.

---

### Q3. Why is a load capacitor added to the output?

**Answer:** The load capacitor emulates the parasitic capacitance and fan-out loading encountered in practical integrated circuits, enabling realistic timing and power analysis.

---

### Q4. Why is the TT process corner used?

**Answer:** The TT (Typical-Typical) process corner represents nominal manufacturing conditions and is commonly used as the baseline for circuit characterization.

---

### Q5. Why is a pulse source used instead of a DC source?

**Answer:** A pulse source allows the inverter to switch repeatedly between logic LOW and HIGH, enabling transient, delay, rise/fall time, and power analyses.
