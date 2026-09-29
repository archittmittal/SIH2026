# Proposed Solution: TwinFlow-AI

## Solution Name
**TwinFlow-AI:** A Graph-Based Coupled Physics-ML Digital Twin for Heavy Oil Optimization.

## Architecture Overview
The Digital Twin architecture consists of four distinct layers, ensuring robust data ingestion, physical modeling, predictive analytics, and end-user visibility.

1. **Physical Layer:** Wellsite sensors, SCADA/DCS systems, VFDs on the SRP, temperature/pressure gauges, and steam generators.
2. **Data Layer:** Edge gateways for local data buffering, OPC-UA/MQTT protocols for telemetry, and a central Time-Series Database (InfluxDB/TimescaleDB) integrating historian and real-time logs.
3. **Model Layer (The Core):** A set of interconnected sub-twins simulating the reservoir, wellbore, and surface equipment simultaneously.
4. **Application Layer:** 3D Visualization dashboards, alert systems, and an interactive optimization interface for production engineers.

## Key Innovation: Graph-Based Coupled Physics-ML Digital Twin
Traditionally, numerical reservoir simulators (like CMG STARS or ECLIPSE) are decoupled from wellbore and surface network simulators. They are too computationally intensive for real-time applications.

Our innovation is modeling the reservoir, wellbore, and SRP as **interconnected sub-twins on a graph**, facilitating bidirectional information flow at every time step. 
- The **SRP Sub-Twin** outputs pressure and flow boundaries to the **Wellbore Sub-Twin**.
- The **Wellbore Sub-Twin** feeds downhole pressure back to the **Reservoir Sub-Twin**.
- The **Reservoir Sub-Twin** updates phase saturations and heat profiles, returning fluid mobility data upwards.

## Novelty: Neural ODE Reservoir Simulator
Instead of using computationally expensive finite-difference simulators for real-time control, we utilize a **Neural Ordinary Differential Equation (Neural ODE)** based reservoir simulator. 
- It uses analytical physics models (Marx-Langenheim for steam zone expansion and Boberg-Lantz for production response) as a baseline.
- The Neural ODE learns the *residual physics*—the complex, non-linear dynamics (like asphaltene precipitation or fingering) that analytical models fail to capture.
- **Advantage:** Maintains physical fidelity while executing **1000x faster** than full numerical simulators, enabling real-time optimization and multiple scenario evaluations in seconds.

## SRP Digital Twin & Dynamometer Analysis
The SRP operation is monitored through surface and downhole dynamometer cards. 
- We employ a **1D-CNN + LSTM hybrid model** to classify these cards in real-time.
- The model extracts spatial features from the pump card shape (1D-CNN) and analyzes temporal variations across consecutive strokes (LSTM).
- **Outcomes:** Instant diagnosis of rod floating, pump unsetting, gas interference, fluid pound, and mechanical friction—critical for highly viscous crude.

## Joint CSS + SRP Optimization via Reinforcement Learning
Optimizing CSS parameters (steam quality, injection rate, soak time) and SRP settings (stroke length, SPM) is a multi-objective problem. 
- We deploy an advanced Reinforcement Learning (RL) agent, utilizing **Soft Actor-Critic (SAC) or Proximal Policy Optimization (PPO)**.
- **Reward Function:** Maximizes cumulative oil production while heavily penalizing high Steam-Oil Ratios (SOR) and conditions leading to rod failures.
- The agent continuously interacts with the Neural ODE environment to discover optimal operational policies dynamically.

## Real-Time Anomaly Detection
To prevent costly workovers, a **Temporal Fusion Transformer (TFT)** predicts rod failures 24-48 hours in advance. It integrates static well parameters, historical failure logs, and real-time SCADA telemetry to output a highly interpretable risk probability score over a future time horizon.

## Dashboard & Application Interface
- **3D Well Visualization:** Interactive visualization of the wellbore using Three.js, mapping heat distribution and pump kinematics.
- **Real-Time KPIs:** Live monitoring of expected vs. actual production, pump efficiency, and energy consumption per barrel.
- **Automated Alerts:** SMS/Email integration for critical events like impending rod floating or optimal time to terminate the soak phase.
