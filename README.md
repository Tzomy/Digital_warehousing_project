# Robotic Warehouse Design: MTSR vs AMR vs Rack-Climbing Robots (CSRS)

Sizing and comparison of three robotic tote-based storage and retrieval systems for a 20,000-tote warehouse.

> Project developed for the **Logistics – Advanced Project Work, a.y. 2025/26** course (University of Padua, Prof. Alessandro Persona), with teammates: Anna Gianolla, Bruktawit Mekonnen, Davide Salvagno, Giacomo Squizzato, Tommaso Pintonato.

---

## Table of Contents

1. [Overview](#overview)
2. [The Three Systems](#the-three-systems)
3. [Problem Specifications](#problem-specifications)
4. [Kinematic and Geometric Parameters](#kinematic-and-geometric-parameters)
5. [Methodology](#methodology)
6. [Results](#results)
7. [Comparison and Fields of Application](#comparison-and-fields-of-application)
8. [Repository Structure](#repository-structure)
9. [References](#references)
10. [Team](#team)

---

## Overview

The goal of this project is to **design a robotized warehouse** starting from a given set of specifications, and to compare three alternative automation technologies:

| # | System | Description |
|---|--------|-------------|
| 1 | **MTSR** | Multi-Tote Storage and Retrieval autonomous mobile robots |
| 2 | **MTSR + AMR** | MTSRs serving the racks, Autonomous Mobile Robots handling horizontal transport between an exchange floor and the picking stations |
| 3 | **CSRS** | Rack-Climbing Robotic Storage and Retrieval Systems |

For each technology we size the warehouse and the robot fleet required to sustain the target throughput, then compare the solutions in terms of fleet size, investment cost, and suitability for different operating scenarios.

---

## The Three Systems

### 1. Multi-Tote Storage and Retrieval (MTSR)
Autonomous mobile robots equipped with a vertical mast that can carry multiple totes at once (8 back trays). They travel along the aisles, climb the mast to reach the storage level, and deliver totes to the picking stations through a box carousel and conveyor. A single robot performs both horizontal and vertical movements.

### 2. MTSR + AMR
MTSRs operate inside the aisles only, while AMRs perform the horizontal transport between the rack area and the picking stations. The **lowest shelf floor is used as an exchange floor** where MTSRs and AMRs hand over the totes.

### 3. Rack-Climbing Robotic Storage and Retrieval Systems (CSRS)
Robots that move freely on the ground floor and **climb the racks** through vertical rails to reach any storage position. Horizontal moves are performed on the ground, vertical ones inside the aisles. In this configuration the lowest floor is absent.

---

## Problem Specifications

| Parameter | Value |
|-----------|-------|
| System capacity | **20,000 totes** (plastic boxes) |
| Number of aisles | **8** |
| Shelf floors | **16** in case 1 · in case 2 the lowest floor is the exchange floor · in case 3 the lowest floor is absent |
| Picking stations | **3** |
| Distance between shelves and picking stations | **12 m** |
| Throughput | **200 totes IN + 200 totes OUT per hour** |
| Cost per robot | MTSR: **€60,000** · AMR: **€7,000** · CSRS: **€20,000** |

---

## Kinematic and Geometric Parameters

### Robot parameters

| Parameter | MTSR | AMR | CSRS (climbing) |
|-----------|:----:|:---:|:---------------:|
| Horizontal speed Vx (m/s) | 1.5 | 4 | 4 |
| Vertical speed Vz (m/s) | 1 | – | 1 |
| Tote load/unload time (s) | 5 | 3 | 3 |
| Positioning time (s) | 5 | 3 | 3 |
| Acceleration (m/s²) | 0.3 | 1 | 1 |
| Number of back trays | 8 | – | – |

### Tote size

| L (mm) | B (mm) | H (mm) |
|:------:|:------:|:------:|
| 400 | 600 | 400 |

### General parameters

| Parameter | Value |
|-----------|-------|
| Maximum picking height | 8,000 mm |
| Height of lower shelf floor | 500 mm |
| Total number of floors | 16 |
| Aisle width | 1,200 mm |
| Shelf module length | 2,000 mm |
| Number of totes per module | 4 |
| Shelf depth | 600 mm |
| Type of stock | Single-deep |

---

## Methodology

For each system (1, 2, 3) the design follows these steps:

1. **Layout definition**: number of modules per aisle, warehouse length, width and height, derived from the 20,000-tote capacity, 8 aisles and floor configuration of the case.
2. **Cycle-time model**: travel times computed with the kinematic parameters above (acceleration phase, constant speed phase, load/unload and positioning times), for both single and dual command cycles where applicable.
3. **Fleet sizing**: number of robots required to serve 200 totes IN + 200 totes OUT per hour, taking into account the 3 picking stations and the 12 m shelf-to-station distance.
4. **Cost evaluation**: total investment on robots, based on the unit costs given in the specifications.
5. **Comparison**: the three solutions are compared on fleet size, cost and operational flexibility.

---

## Results

### Warehouse layout

| | System 1: MTSR | System 2: MTSR + AMR | System 3: CSRS |
|---|:---:|:---:|:---:|
| Storage floors | 16[cite: 2] | 15 (16 total; floor 1 = exchange)[cite: 2] | 15 (lowest floor absent)[cite: 2] |
| Modules per aisle | 40 (20 per rack side) | 42 (21 per rack side) | 42 (21 per rack side) |
| Length of shelves (m) | 46.8 | 48.9 | 44.1[cite: 1] |
| Width of shelves (m) | 19.2[cite: 1] | 19.2[cite: 1] | 19.2[cite: 1] |
| Total warehouse area (m²) | 4,474.56[cite: 2] | 4,607.88[cite: 2] | 4,304.72[cite: 2] |
| Warehouse height (m) | 8.0 | 8.0 | 8.0 |
| Cycle time $T(CC)$ (s) | 482.2[cite: 1] | 427.6 (MTSR) / 88.4 (AMR)[cite: 1] | 111.4[cite: 1] |

### Robot fleet and investment

| | System 1: MTSR | System 2: MTSR + AMR | System 3: CSRS |
|---|:---:|:---:|:---:|
| Number of MTSRs | 6 (+ 1 spare)[cite: 1, 2] | 4 (+ 1 spare)[cite: 1, 2] | – |
| Number of AMRs | – | 8 (+ 1 spare)[cite: 1, 2] | – |
| Number of CSRS robots | – | – | 12 (+ 3 charging)[cite: 1, 2] |
| **Total robot cost (€)** | **€360,000** (€420,000 incl. spare)[cite: 2] | **€296,000** (€363,000 incl. spares)[cite: 2] | **€240,000** (€300,000 incl. charging)[cite: 2] |
| Area cost (€350/m²) | €1,566,096[cite: 2] | €1,612,758[cite: 2] | €1,506,652[cite: 2] |
| Shelving structure cost (€) | €1,500,000[cite: 2] | €1,500,000[cite: 2] | €1,500,000[cite: 2] |
| Workstations cost (3 units) (€) | €300,000[cite: 2] | €300,000[cite: 2] | €300,000[cite: 2] |
| Additional equipment cost (€) | €5,000 (1 battery pack)[cite: 2] | – | €800,000 (vertical rails)[cite: 2] |
| **Total System Investment (€)** | **€3,791,096**[cite: 2] | **€3,775,758**[cite: 2] | **€4,106,952**[cite: 2] |

---

## Comparison and Fields of Application

The three technologies are compared in general terms with respect to:

| Criterion | MTSR | MTSR + AMR | CSRS |
|-----------|------|------------|------|
| **a) Peaks of demand** | Lower flexibility; high unit cost (€60k/robot) makes scaling fleet size for short-term peaks expensive[cite: 2]. | High flexibility on horizontal transport (inexpensive AMRs at €7k/robot), though aisle retrieval remains bounded by MTSR capacity[cite: 2]. | High flexibility; intermediate robot cost (€20k) and single-tote modularity allow extra climbing robots to be added easily[cite: 2]. |
| **b) Item classes A, B, C (picking frequency)** | Best paired with class-based storage (high-turnover A items near the front/lower levels) to minimize multi-stop tour lengths. | Very effective with class-based storage; placing A-items near the bottom exchange floor minimizes MTSR vertical travel. | Less sensitive to vertical/horizontal skew due to fast ground speed ($4\text{ m/s}$), though class-based zoning reduces rail congestion. |
| **c) Size of customer orders** | **Directly influenced by customer order size**; requires batching 6 to 8 totes per trip to amortize horizontal travel and achieve target throughput[cite: 1]. | Moderately influenced; MTSRs still batch within aisles while AMRs decouple single-tote delivery to picking stations. | Independent of order size; single-tote cycles handle both single-line and multi-line orders without batching delays. |
| **d) Throughput levels** | Suited for medium-to-high throughput when tray utilization (6–8 totes/trip) is consistently high[cite: 1]. | High throughput capability; decoupling vertical storage from horizontal transport reduces MTSR cycle time from $482.2\text{ s}$ to $427.6\text{ s}$[cite: 1]. | High, scalable throughput ($T(CC) = 111.4\text{ s}$ per tote), limited only by aisle/rail traffic density at very large fleet sizes[cite: 1]. |
| **e) Sequencing constraints on SKU arrival at picking stations** | Rigid; 8-tote batch retrieval makes strict SKU arrival sequencing complex and requires buffering/sorting at the carousel. | High sequencing capability; the lowest-floor exchange buffer allows AMRs to dispatch totes to stations in the exact required sequence. | Very high sequencing capability; individual robots retrieve and deliver single totes directly in the required order sequence. |

---

## Repository Structure

---

## Repository Structure

```
.
├── README.md
├── model/         # Cycle-time and fleet sizing models (scripts / spreadsheets)
└── results/       # Output tables and charts
```

> Adjust this section to match the actual content of the repository.

---

## References

| Title | Authors | Year | System |
|-------|---------|:----:|--------|
| Analysis and Design of Rack-Climbing Robotic Storage and Retrieval Systems | W. Chen, R. de Koster, Y. Gong | 2022 | CSRS |
| Order sequencing, tote scheduling, and robot routing optimization in multi-tote storage and retrieval autonomous mobile robot systems | H. Bai, P. Yang, Z. Qin, M. Qi, W. Xiong | 2025 | MTSR |
| Making better order fulfillment in multi-tote storage and retrieval autonomous mobile robot systems | Z. Qin, Y. Kang, P. Yang | 2024 | MTSR |
| Performance Analysis of Multi-Tote Storage and Retrieval Autonomous Mobile Robot Systems | Z. Qin, P. Yang, Y. Gong, R. B. M. de Koster | 2024 | MTSR |
| Modeling and Analysis of Multi-Line Orders in Multi-Tote Storage and Retrieval Autonomous Mobile Robot Systems | X. Shan, Y. Jin, P. Zheng Li, K. Kondo | 2024 | MTSR |
| Warehouses with heterogeneous robots collaboration: operational policies and performance analysis | Y. Kang, R. Wang, Z. Qin, P. Yang, Y. Yan | 2025 | MTSR + AMR |
| Enhancing Warehouse Efficiency with Multi-Tote Storage and Retrieval AMRs | M. Faccio, I. Granata, A. Persona | 2025 | MTSR |
| Hybrid MTSR–AMR warehouse system with class-based storage policies: modeling and performance evaluation | I. Granata, M. Faccio, A. Persona | 2025 | MTSR + AMR |

---

## Team
- Anna Gianolla
- Bruktawit Mekonnen
- Davide Salvagno
- Giacomo Squizzato
- Tommaso Pintonato
