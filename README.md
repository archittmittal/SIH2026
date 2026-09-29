<div align="center">

# 🇮🇳 Smart India Hackathon 2026

### Ideation Phase — Problem Statement Documentation

[![SIH 2026](https://img.shields.io/badge/SIH-2026-orange?style=for-the-badge&logo=hackthebox&logoColor=white)](https://www.sih.gov.in/)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue?style=for-the-badge)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen?style=for-the-badge)](https://github.com/archittmittal/SIH2026/pulls)

<br/>

*Comprehensive documentation, novel architectures, and feasibility analyses for selected SIH 2026 problem statements.*

---

</div>

## 📋 Problem Statements

This repository contains end-to-end ideation documentation for the following SIH 2026 problem statements:

<table>
  <tr>
    <th width="50%">🌧️ SIH26086 — VarshaMitra</th>
    <th width="50%">🛢️ SIH26120 — TwinFlow-AI</th>
  </tr>
  <tr>
    <td>
      <b>Hyperlocal Monsoon Onset & Break Prediction System</b><br/>
      <sub>Ministry of Earth Sciences (MoES)</sub>
    </td>
    <td>
      <b>Digital Twin for CSS & SRP Optimization</b><br/>
      <sub>Oil India Limited (OIL)</sub>
    </td>
  </tr>
  <tr>
    <td>
      <code>Agriculture, FoodTech & Rural Development</code>
    </td>
    <td>
      <code>Smart Automation</code>
    </td>
  </tr>
  <tr>
    <td>
      Block/Village-scale 7-to-30-day probabilistic monsoon forecasting using Physics-Informed Graph Neural Networks, with vernacular agronomic advisories for 120M+ farming households.
    </td>
    <td>
      AI-enabled Well-to-Surface Digital Twin integrating reservoir, wellbore, and SRP systems for real-time optimization of heavy oil production at Baghewala Field.
    </td>
  </tr>
  <tr>
    <td align="center">
      <a href="./SIH26086-Hyperlocal-Monsoon-Prediction/"><b>📂 View Documentation →</b></a>
    </td>
    <td align="center">
      <a href="./SIH26120-Digital-Twin-CSS-SRP/"><b>📂 View Documentation →</b></a>
    </td>
  </tr>
</table>

---

## 🏗️ Solution Highlights

### 🌧️ VarshaMitra — *Friend of the Rain*

> Bridging global climate signals to hyperlocal farmer advisory — one block at a time.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         DATA INGESTION LAYER                           │
│  IMD AWS/ARG ─ ERA5 ─ GPM IMERG ─ GFS/ECMWF ─ ENSO/IOD/MJO Indices  │
└────────────────────────────────┬────────────────────────────────────────┘
                                 ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                     ML PREDICTION PIPELINE                             │
│  SRCNN Downscaling (25km → 5km) ──► PI-STGNN (Graph Attention)       │
│  ──► Hidden Semi-Markov Model (Onset/Break Detection)                 │
│  ──► Isotonic Calibration ──► Probabilistic Risk Maps                 │
└────────────────────────────────┬────────────────────────────────────────┘
                                 ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                    ADVISORY & DELIVERY ENGINE                          │
│  Crop Phenology Expert System ──► IndicTrans2 (12+ Languages)         │
│  ──► PWA ─ WhatsApp API ─ SMS ─ IVRS                                 │
└─────────────────────────────────────────────────────────────────────────┘
```

**Core Innovation:** Physics-Informed Spatio-Temporal Graph Neural Network (PI-STGNN) that embeds monsoon thermodynamic constraints directly into the loss function — predictions that are not just statistically accurate, but *physically consistent*.

---

### 🛢️ TwinFlow-AI — *The Coupled Digital Twin*

> One wellbore. Three sub-twins. Zero silos.

```
┌───────────────────────────────────────────────────────────────────────┐
│                     PHYSICAL LAYER (Field)                            │
│  SCADA/DCS ─ VFD Sensors ─ Downhole Gauges ─ Dynamometer Cards      │
└───────────────────────────────┬───────────────────────────────────────┘
                                ▼
┌───────────────────────────────────────────────────────────────────────┐
│              DIGITAL TWIN ENGINE (Coupled Sub-Twins)                  │
│                                                                       │
│  ┌─────────────┐    ┌──────────────┐    ┌─────────────┐              │
│  │  Reservoir   │◄──►│   Wellbore    │◄──►│     SRP     │              │
│  │  Sub-Twin    │    │   Sub-Twin    │    │   Sub-Twin  │              │
│  │ (Neural ODE) │    │ (Drift-Flux)  │    │ (Wave Eqn)  │              │
│  └─────────────┘    └──────────────┘    └─────────────┘              │
│           ▲                                      │                    │
│           └──── RL Agent (PPO/SAC) ──────────────┘                    │
│                 Joint CSS + SRP Optimization                          │
└───────────────────────────────┬───────────────────────────────────────┘
                                ▼
┌───────────────────────────────────────────────────────────────────────┐
│                    APPLICATION LAYER                                   │
│  3D Well Visualization ─ Real-time KPIs ─ Failure Alerts ─ Reports   │
└───────────────────────────────────────────────────────────────────────┘
```

**Core Innovation:** Neural ODE-based reservoir simulator that learns residual physics — **1000× faster** than numerical simulation — coupled with a Reinforcement Learning agent for joint CSS+SRP optimization.

---

## 📂 Repository Structure

```
SIH2026/
├── README.md                                  ← You are here
├── LICENSE
│
├── SIH26086-Hyperlocal-Monsoon-Prediction/
│   ├── README.md                              ← Solution overview
│   └── docs/
│       ├── 01-proposed-solution.md            ← VarshaMitra architecture
│       ├── 02-technical-approach.md           ← ML pipeline & tech stack
│       ├── 03-feasibility-and-viability.md    ← Costs, risks & 36-hr plan
│       ├── 04-impact-and-benefits.md          ← Farmer impact & SDG alignment
│       └── 05-research-and-references.md      ← 20+ academic references
│
└── SIH26120-Digital-Twin-CSS-SRP/
    ├── README.md                              ← Solution overview
    └── docs/
        ├── 01-proposed-solution.md            ← TwinFlow-AI architecture
        ├── 02-technical-approach.md           ← Digital twin engine & ML stack
        ├── 03-feasibility-and-viability.md    ← Industry benchmarks & viability
        ├── 04-impact-and-benefits.md          ← Production & cost impact
        └── 05-research-and-references.md      ← SPE papers & case studies
```

---

## 🛠️ Tech Stack Overview

<table>
  <tr>
    <th>Layer</th>
    <th>🌧️ VarshaMitra</th>
    <th>🛢️ TwinFlow-AI</th>
  </tr>
  <tr>
    <td><b>ML / AI</b></td>
    <td>PyTorch, PyTorch Geometric, scikit-learn</td>
    <td>PyTorch, torchdiffeq (Neural ODE), Stable-Baselines3</td>
  </tr>
  <tr>
    <td><b>Backend</b></td>
    <td>FastAPI, Celery, Redis</td>
    <td>FastAPI, Apache Kafka, Redis</td>
  </tr>
  <tr>
    <td><b>Database</b></td>
    <td>PostgreSQL + PostGIS + TimescaleDB</td>
    <td>InfluxDB / TimescaleDB</td>
  </tr>
  <tr>
    <td><b>Frontend</b></td>
    <td>React (PWA), Leaflet.js</td>
    <td>React / Next.js, Three.js, Grafana</td>
  </tr>
  <tr>
    <td><b>Delivery</b></td>
    <td>WhatsApp Business API, MSG91, IVRS</td>
    <td>Dashboard, Automated Alerts</td>
  </tr>
  <tr>
    <td><b>Infra</b></td>
    <td>Docker, Kubernetes, AWS/GCP</td>
    <td>Docker, NVIDIA Jetson (Edge), AWS/GCP</td>
  </tr>
</table>

---

## 📊 Impact at a Glance

<table>
  <tr>
    <th></th>
    <th>🌧️ VarshaMitra</th>
    <th>🛢️ TwinFlow-AI</th>
  </tr>
  <tr>
    <td><b>Primary Beneficiaries</b></td>
    <td>120M+ farming households</td>
    <td>Oil India Limited (Baghewala Field)</td>
  </tr>
  <tr>
    <td><b>Key Metric</b></td>
    <td>Reduce crop failure from false onset by up to 40%</td>
    <td>10–15% production increase, 15–20% SOR reduction</td>
  </tr>
  <tr>
    <td><b>Economic Impact</b></td>
    <td>₹5,000–15,000 savings per hectare per season</td>
    <td>₹1–2 Cr savings per well over lifecycle</td>
  </tr>
  <tr>
    <td><b>SDG Alignment</b></td>
    <td>SDG 1, 2, 13, 15</td>
    <td>SDG 7, 9, 12, 13</td>
  </tr>
</table>

---

## 🚀 Getting Started

Each problem statement folder contains its own detailed documentation. Start here:

| Problem Statement | Quick Link |
|:---|:---|
| 🌧️ Hyperlocal Monsoon Prediction | [**SIH26086 Documentation →**](./SIH26086-Hyperlocal-Monsoon-Prediction/README.md) |
| 🛢️ Digital Twin CSS/SRP | [**SIH26120 Documentation →**](./SIH26120-Digital-Twin-CSS-SRP/README.md) |

---

## 🤝 Contributing

Contributions, suggestions, and feedback are welcome! Feel free to:

1. **Fork** this repository
2. **Create** a feature branch (`git checkout -b feature/your-idea`)
3. **Commit** your changes (`git commit -m 'Add: your feature'`)
4. **Push** to the branch (`git push origin feature/your-idea`)
5. Open a **Pull Request**

---

## 📜 License

This project is licensed under the **Apache License 2.0** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built with 🧠 and ❤️ for Smart India Hackathon 2026**

*[@archittmittal](https://github.com/archittmittal)*

</div>
