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

## MSc Thesis — Rolling-Horizon Last-Mile Delivery Optimization

**DTU (Technical University of Denmark), 2026**

Two parallel research tracks tackling the same multi-day last-mile delivery problem from different angles: one theoretical (learning-augmented compute allocation), one applied (rich VRPTW with exact methods).

### Problem

Orders arrive daily with flexible multi-day delivery windows. The system must decide each day which orders to attempt and how to route vehicles — under time-window, capacity, and depot constraints — while balancing three competing objectives:
- Minimize routing cost (distance / duration)
- Minimize deadline failures and undelivered orders
- Minimize plan instability (PlanChurn) across rolling re-planning days

### Track 1 — Learning-Augmented Compute Allocation (Theoretical)

Focuses on how to dynamically allocate computational budget across planning days using machine learning.

**Approach:**
- **Rolling-horizon simulation** — day-by-day re-planning with carryover of undelivered orders
- **Risk-gated allocation** — escalates compute budget based on system stress signals
- **ALNS solver** — Adaptive Large Neighborhood Search for daily VRPTW routing
- **Learned allocator** — offline ML model (HistGradientBoosting / Ridge) predicting optimal compute-to-order ratios
- **Bandit-augmented allocator** — online learning that adapts allocation policy in real time
- **Sparse fail-safe bandit** — robust variant for out-of-distribution scenarios

**Experiments:** 15+ experiments covering baselines, dynamic allocation with risk gate, sensitivity sweeps (capacity ratio, multi-trip, fleet parallelism, risk threshold), ablation studies, and OOD robustness evaluation.

**Tech:** Python, ALNS, scikit-learn, DTU HPC (LSF)

### Track 2 — Rich VRPTW with Exact Methods (Applied)

Focuses on solving the full-fidelity routing problem with heterogeneous fleet, multi-dimensional capacity, and depot resource constraints.

**Approach:**
- **Branch-and-Price framework** — column generation with restricted master problem for tight lower bounds
- **ALNS + Set Partitioning recombination** — route-pool based intensification
- **Julia/Gurobi backend** — exact solver for restricted master and pricing subproblems via Python-Julia bridge
- **Depot resource modeling** — bucketed dock capacity, loading/unloading throughput, staging constraints
- **Stability-aware re-planning** — churn penalties for day-assignment, vehicle, sequence, and depot-slot changes

**Experiments:** resistance suite testing solver performance under increasing pressure (baseline, boundary, shifted, hard scenarios) across multiple seeds.

**Tech:** Python, Julia, Gurobi, OR-Tools, OSRM road-network matrices, DTU HPC (LSF)

### Shared Infrastructure

- Real delivery data from Copenhagen area (Herlev benchmark)
- OSRM-based travel time/distance matrices
- LaTeX thesis document with DTU template
- HPC job management via LSF batch scheduling

---

*More projects coming soon.*
