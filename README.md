# Project Portfolio

Source code is kept private — this repo showcases the design, architecture, and key features of my projects.

---

## Nimbus

A weather app for Denmark, built with real-time data from MET Nordic APIs. Designed with an editorial, typography-driven aesthetic.

### Screenshots

<p align="center">
  <img src="assets/nimbus/IMG_3645.PNG" width="200" />
  <img src="assets/nimbus/IMG_3648.PNG" width="200" />
  <img src="assets/nimbus/IMG_3649.PNG" width="200" />
</p>
<p align="center">
  <img src="assets/nimbus/IMG_3647.PNG" width="200" />
  <img src="assets/nimbus/IMG_3646.PNG" width="200" />
</p>

### Features

- **Current conditions** — temperature, wind, humidity, cloud cover with real-time updates
- **Hourly & daily forecasts** — interactive charts for temperature, precipitation, wind, and humidity
- **Precipitation nowcast** — minute-by-minute rain predictions via MET Nordic
- **Sun & daylight explorer** — solar noon countdown, sun position (altitude/azimuth), sunrise/sunset with a sky-gradient visualization and time scrubber
- **Lunar phase explorer** — real-time moon illumination, phase name, moonrise/moonset timeline, constellation tracking with a fisheye date scrubber
- **Radar map** — rain and wind overlays via RainViewer and WX map tiles
- **Weather warnings** — advisory bulletins
- **Multi-location** — manage up to 4 saved locations
- **iOS widget** — glanceable weather on the home screen

### Architecture & Tech

- **Swift / SwiftUI** with MVVM-Coordinator pattern
- **Metal shaders** for real-time sky stage background rendering
- **MET Nordic API** for weather data
- **RainViewer API** for radar imagery
- **GCP Cloud Run** backend for tile proxy and data aggregation
- **Terraform** for infrastructure-as-code
- **WidgetKit** for home screen widget

### Status

In active development. Not yet on the App Store.

---

## MSc Thesis — Dynamic Fleet Allocation under Rolling-Horizon Last-Mile Delivery

**DTU (Technical University of Denmark), 2026**

A multi-day rolling-horizon framework for last-mile delivery that dynamically allocates computational budget and fleet resources under uncertainty. Orders arrive with multi-day service windows; the system decides daily which orders to attempt, then solves a constrained VRPTW routing problem within a limited compute budget.

### Problem

In last-mile delivery, orders have flexible delivery windows spanning multiple days. The challenge is to balance three competing objectives under limited computational time:
- Minimize routing cost (distance/duration)
- Minimize deadline failures and undelivered orders
- Minimize plan instability (PlanChurn) across rolling re-planning days

### Approach

- **Rolling-horizon simulation** — day-by-day re-planning with carryover of undelivered orders
- **Risk-gated allocation** — a risk gate that decides when to escalate compute budget based on system stress signals
- **ALNS solver** — Adaptive Large Neighborhood Search for daily VRPTW routing with time windows, vehicle capacity, and shift constraints
- **Learned allocator** — ML model (HGB / Ridge) trained offline to predict optimal compute-to-order allocation ratios
- **Bandit-augmented allocator** — online learning layer that adapts the allocation policy in real time
- **Sparse fail-safe bandit** — robust variant for out-of-distribution scenarios

### Experiments

| ID | Description |
|----|-------------|
| EXP00 | Business-as-usual baseline (no pressure) |
| EXP01 | Crunch baseline (single-wave pressure, no risk gate) |
| EXP02–04 | Static vs. dynamic compute allocation with risk gate |
| EXP05–08 | Sensitivity analysis: capacity ratio, multi-trip, fleet parallelism, risk threshold |
| EXP09 | Risk model ablation |
| EXP12 | Offline learned allocator |
| EXP13 | Online bandit-augmented allocator |
| EXP14 | Sparse fail-safe bandit |
| EXP15 | Out-of-distribution robustness evaluation |

### Tech Stack

- **Python** — simulation, solvers, ML pipeline
- **OR-Tools / ALNS** — vehicle routing optimization
- **scikit-learn** — HistGradientBoosting, Ridge regression for allocation models
- **DTU HPC (LSF)** — experiment execution on cluster
- **LaTeX** — thesis document

---

*More projects coming soon.*
