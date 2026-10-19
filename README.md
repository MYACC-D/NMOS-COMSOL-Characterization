# DC Characterization of an NMOS Transistor Using COMSOL Multiphysics 6.4 and Python

## Overview

This project investigates the DC characteristics of an N-channel Metal-Oxide-Semiconductor Field-Effect Transistor (NMOS) using **COMSOL Multiphysics 6.4** and **Python**.

The NMOS device was modeled in COMSOL following the official COMSOL Semiconductor Module example, [DC Characteristics of a MOS Transistor (MOSFET)](https://doc.comsol.com/6.4/doc/com.comsol.help.models.semicond.mosfet/mosfet.html).

The simulated electrical characteristics were exported as CSV files and analyzed in Python using Google Colab. The analysis focuses on visualizing the current-voltage characteristics, calculating transconductance, and estimating the threshold voltage.

## Objectives

- Simulate an NMOS transistor using COMSOL Multiphysics 6.4.
- Analyze the transfer and output characteristics of the device.
- Calculate transconductance (g<sub>m</sub>) from the transfer characteristics.
- Estimate the threshold voltage (V<sub>th</sub>) using Python.
- Develop a workflow connecting semiconductor device simulation with numerical data analysis.

## Tools and Technologies

- **COMSOL Multiphysics 6.4** — NMOS device modeling and DC simulation
- **Python** — Numerical analysis and parameter extraction
- **Google Colab** — Cloud-based Python execution
- **NumPy** — Numerical differentiation and curve fitting
- **Pandas** — CSV data processing
- **Matplotlib** — Data visualization

## Methodology

### 1. NMOS Device Simulation

The NMOS transistor was modeled using COMSOL's Semiconductor physics interface, following the geometry, material properties, doping profiles, and boundary conditions of the reference model.

Two DC analyses were considered:

- **Transfer characteristics:** Drain current (I<sub>D</sub>) versus gate-to-source voltage (V<sub>GS</sub>), with drain-to-source voltage fixed at (V<sub>DS</sub> = 0.01 V).
- **Output characteristics:** Drain current (I<sub>D</sub>) versus drain-to-source voltage (V<sub>DS</sub>) for gate voltages of 2 V, 3 V, and 4 V.

### 2. Simulation Data Export

The results were exported from COMSOL into two CSV files:

| File | Description |
|---|---|
| `nmos_transfer.csv` | Transfer characteristics: (I<sub>D</sub>) versus (V<sub>GS</sub>) |
| `nmos_output.csv` | Output characteristics: (I<sub>D</sub>) versus (V<sub>DS</sub>) for multiple gate voltages |

Python: Analyze the exported transfer data, calculate transconductance, and estimate threshold voltage.

### 3. Python-Based Data Analysis

The exported CSV files were processed in Google Colab using Pandas, NumPy, and Matplotlib.

The analysis includes:

- Importing and extracting the relevant simulation data.
- Plotting transfer and output characteristics.
- Numerically differentiating the transfer curve to calculate transconductance.
- Applying polynomial curve fitting to estimate the threshold voltage.

### 4. Transconductance Calculation

Transconductance measures how strongly the drain current responds to a change in gate-to-source voltage at a fixed drain-to-source voltage.

g<sub>m</sub> = ∂I<sub>D</sub> / ∂V<sub>GS</sub>

The derivative was approximated numerically using NumPy:

g<sub>m</sub> ≈ ΔI<sub>D</sub> / ΔV<sub>GS</sub>

The resulting transconductance values are expressed in microsiemens (µS).

### 5. Threshold Voltage Estimation

The threshold voltage was estimated from the transfer characteristics using a polynomial fitting approach over the selected gate-voltage range.

The extracted value depends on the fitting interval and the chosen extraction method. It is therefore treated as a numerical estimate rather than an exact device parameter.

## Results

The Python analysis produced the following preliminary parameter estimates:

| Parameter | Estimated result |
|---|---:|
| Transconductance, (g<sub>m</sub>) | Approximately 9.35 µS |
| Threshold voltage, (V<sub>th</sub>) | Approximately 1.55 V |

These values are specific to the data processing and extraction methods used in this project. The threshold voltage should be interpreted in the context of the selected polynomial fitting procedure.

The transfer and output curves are used to examine the device's turn-on behavior, current response to gate voltage, and drain-current saturation.

## How to Run

1. Open the Python notebook in Google Colab.
2. Upload `nmos_transfer.csv` and `nmos_output.csv`.
3. Run the notebook cells in sequence.
4. Review the transfer and output characteristic plots.
5. Examine the calculated transconductance and estimated threshold voltage.

The COMSOL model is required to reproduce the original simulation data. The Python analysis can be run separately using the exported CSV files.

## Conclusion

This project demonstrates a practical workflow for **NMOS transistor DC characterization**, combining semiconductor device simulation in COMSOL Multiphysics 6.4 with Python-based data analysis.

It provides experience in interpreting transistor I–V characteristics, numerically calculating transconductance, estimating threshold voltage, and processing simulation data.

## Skills Demonstrated

- Semiconductor device physics
- NMOS transistor DC characterization
- COMSOL Multiphysics simulation
- Python-based numerical analysis
- Data visualization and CSV processing
- Transistor parameter extraction
- Google Colab and GitHub project documentation

## Reference

COMSOL AB, *DC Characteristics of a MOS Transistor (MOSFET)*, COMSOL Multiphysics 6.4 Documentation.

https://doc.comsol.com/6.4/doc/com.comsol.help.models.semicond.mosfet/mosfet.html
