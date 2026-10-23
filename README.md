# Two-Stage CMOS Operational Amplifier Design

A full-custom, transistor-level design and simulation study of a **two-stage CMOS operational amplifier** implemented in **Cadence Virtuoso** using a **45 nm CMOS technology**. The project evaluates DC operating point, AC response, transient behavior, loop-gain stability, statistical variation, and physical layout verification.

## Overview

The amplifier uses a two-stage topology:

- **Stage 1:** NMOS differential input pair with a PMOS current-mirror active load.
- **Stage 2:** Common-source gain/output stage with a current-source load.
- **Bias network:** Current-mirror biasing driven by a 10 µA reference current.
- **Frequency compensation:** Miller compensation capacitor between the first-stage output and the final output.

The design was simulated in Cadence ADE-L / ADE Explorer. The report also documents layout, DRC/LVS checks, Monte Carlo analysis, PVT analysis, and post-layout RC extraction.

## Design Conditions

| Parameter | Value |
|---|---:|
| CMOS technology | 45 nm (`gpdk045`) |
| Positive supply (`VDD`) | 2 V |
| Ground (`VSS`) | 0 V |
| Reference bias current (`Ibias`) | 10 µA |
| Non-inverting input pulse levels | 0.7 V to 1.3 V |
| AC input amplitude | 100 mV |
| Estimated Miller compensation capacitor (`Cc`) | ≈ 0.198 pF |

## Reported Simulation Results

| Metric | Reported result |
|---|---:|
| Quiescent output voltage | 1.301 V |
| Open-loop DC gain | 50.05 dB (≈ 318 V/V) |
| Unity-gain bandwidth | ≈ 111.469 MHz from the AC plot |
| Slew rate | 50.55 V/µs |
| Settling time | 21.548 ns |
| DC offset | 1.49 mV |
| Static power dissipation | 175.819 µW |
| Total quiescent supply current (derived) | ≈ 87.91 µA |
| Phase margin | ≈ 58° (reported approximate value) |
| Gain margin | ≈ 23 dB (reported approximate value) |

> **Note:** Values above are transcribed from the accompanying design report. The report gives approximate stability values and discusses a phase-margin target above 60°. Recheck the final ADE/STB results and extracted post-layout measurements before treating these as sign-off values.

## Analyses Included

- **DC operating point and offset:** Output operating point and input-referred offset.
- **AC analysis:** Low-frequency open-loop gain and 0 dB crossover / bandwidth.
- **Transient analysis:** Pulse response, slew rate, and settling time.
- **Stability (STB / loop gain):** Gain margin and phase margin.
- **Monte Carlo analysis:** Variation of selected performance metrics across randomized runs.
- **PVT analysis:** Transient and AC behavior across process/voltage/temperature conditions.
- **Layout verification:** Layout review with reported DRC-clean result and LVS completion.
- **Post-layout analysis:** The report includes a post-layout RC extraction section; numerical post-PEX results are not provided in the supplied report text.

## Repository Contents

This README is based on the report `2_Stage_CMOS_OpAmp_Design_Report.pdf`. The supplied material contains the design report, schematic/test-bench screenshots, plots, and layout verification screenshots.

A typical repository structure could be:

```text
.
├── README.md
└── 2_Stage_CMOS_OpAmp_Design_Report.pdf
```

If you add Cadence project files, consider organizing them as:

```text
.
├── README.md
├── report/
│   └── 2_Stage_CMOS_OpAmp_Design_Report.pdf
├── cadence/
│   ├── schematic/
│   ├── testbenches/
│   ├── simulations/
│   └── layout/
└── results/
    ├── dc/
    ├── ac/
    ├── transient/
    ├── stb/
    ├── monte-carlo/
    └── pvt/
```

Only include folders and files that actually exist in your repository.

## Tools and Environment

- Cadence Virtuoso Schematic Editor
- Cadence Analog Design Environment (ADE-L / ADE Explorer)
- `gpdk045` 45 nm CMOS PDK, as referenced by the report

Access to the appropriate Cadence installation, PDK, libraries, and project database is required to reproduce the simulations. The PDF alone is a report and does not include a complete runnable Cadence project.

## Reproducing the Work

1. Open the design library and schematic in Cadence Virtuoso.
2. Confirm the `gpdk045` device models and library setup are available in your environment.
3. Configure the bias reference and supply conditions listed above.
4. Run the DC operating-point and offset test benches.
5. Run the open-loop AC analysis and record low-frequency gain and the 0 dB crossover.
6. Run the unity-gain-buffer transient test bench to measure slew rate and settling time.
7. Configure the loop-gain/STB test bench and extract gain margin and phase margin.
8. Run Monte Carlo and PVT sweeps using the intended model corners and variation settings.
9. Verify the physical layout with DRC and LVS, then run parasitic extraction and post-layout simulations.
10. Update this README with final, verified post-layout results if those files are available.

Exact menu paths and simulation settings may differ by Cadence version and project configuration.

## Repository Status / Limitations

- The supplied artifact is a PDF report; schematic source, symbol views, test-bench schematics, model files, and simulation state files were not supplied as separate files.
- The report states that no DRC errors were found and that LVS was completed.
- Numerical post-layout RC-extraction results are not included in the supplied report text.
- Confirm the reported phase margin, gain margin, bandwidth, and post-layout performance directly from the final simulation outputs.

## Reference

- [Two_Stage_OpAmp_Report_338.pdf](Two_Stage_OpAmp_Report_338.pdf) — Full technical design report, including circuit architecture, transistor dimensions, test benches, simulation plots, design calculations, results, layout review, and conclusion.
- (https://drive.google.com/drive/u/1/folders/1cI2x7nFT4_fxSRTWPWng71tYrSX30-lj) - videos of pvt and full design

## Author
T RAJESH

B.Tech, 
Electronics and Communication Engineering
Indian Institute of Information Technology, Sri City

