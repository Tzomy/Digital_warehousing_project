# Robotic Warehouse Design: MTSR vs AMR vs Rack-Climbing Robots (CSRS)

Sizing and comparison of three robotic tote-based storage and retrieval systems for a 20,000-tote warehouse.

> Project developed for the **Logistics – Advanced Project Work, a.y. 2025/26** course (University of Padua, Prof. Alessandro Persona).

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

> **TODO:** add the exact formulas, assumptions (e.g. storage policy, command cycles, utilization targets) and any scripts/spreadsheets used.

---

## Results

### Warehouse layout

| | System 1: MTSR | System 2: MTSR + AMR | System 3: CSRS |
|---|:---:|:---:|:---:|
| Storage floors | TBD | TBD | TBD |
| Modules per aisle | TBD | TBD | TBD |
| Warehouse length (m) | TBD | TBD | TBD |
| Warehouse width (m) | TBD | TBD | TBD |
| Warehouse height (m) | TBD | TBD | TBD |

### Robot fleet and investment

| | System 1: MTSR | System 2: MTSR + AMR | System 3: CSRS |
|---|:---:|:---:|:---:|
| Number of MTSRs | TBD | TBD | – |
| Number of AMRs | – | TBD | – |
| Number of CSRS robots | – | – | TBD |
| **Total robot cost (€)** | TBD | TBD | TBD |

---

## Comparison and Fields of Application

The three technologies are compared in general terms with respect to:

| Criterion | MTSR | MTSR + AMR | CSRS |
|-----------|------|------------|------|
| **a) Peaks of demand** | TBD | TBD | TBD |
| **b) Item classes A, B, C (picking frequency)** | TBD | TBD | TBD |
| **c) Size of customer orders** | TBD | TBD | TBD |
| **d) Throughput levels** | TBD | TBD | TBD |
| **e) Sequencing constraints on SKU arrival at picking stations** | TBD | TBD | TBD |

---

## Repository Structure

```
.
├── README.md
├── docs/          # Project brief, report, presentation, video
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

| Name | Role |
|------|------|
| TBD | TBD |
