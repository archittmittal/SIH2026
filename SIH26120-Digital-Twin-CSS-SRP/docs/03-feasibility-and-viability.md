# Feasibility and Viability

## Technical Feasibility
The proposed architecture relies on proven technologies. Oil India Limited (OIL) has explicitly stated the availability of operational data, which is the primary prerequisite. 
- **Data Availability:** Production history, CSS cycle records, VFD/SRP logs, dynamometer cards, and rod failure logs are available.
- **ML Architectures:** Convolutional Neural Networks (for card classification), TFT (for forecasting), and Neural ODEs are mature, production-ready frameworks supported by PyTorch.
- **Physics Integration:** The foundational analytical models (Marx-Langenheim, Boberg-Lantz, Wave Equation) are standard petroleum engineering equations, making the physics-informed constraints highly reliable.

## Computational Requirements
- **Training (Cloud):** 1-2 NVIDIA A100 or V100 GPUs for training the Neural ODE and RL agents.
- **Inference (Edge):** NVIDIA Jetson Nano / Orin Nano, or any modern CPU for inference (FastAPI backend). The Neural ODE architecture guarantees that inference takes only milliseconds.
- **Storage:** Moderate. Time-series data can be highly compressed.

## SIH Prototype Timeline (36-Hour Plan)
To prove feasibility during the 36-hour hackathon, we will execute the following schedule:

| Time (Hours) | Phase | Tasks |
|--------------|-------|-------|
| 0 - 6 | Data Preprocessing | Clean dataset, generate mock telemetry data if necessary, setup database schemas, initialize Git repo. |
| 6 - 18 | Model Training & Core | Train Neural ODE on mock/sample reservoir data. Train CNN for dynamometer classification. Implement Wave Equation solver. |
| 18 - 30 | Integration & Dashboard | Develop FastAPI backend. Connect sub-twins for message passing. Build React+Three.js dashboard. Integrate Grafana. |
| 30 - 36 | Testing & Polish | End-to-end simulation runs. Optimize RL agent rewards. Finalize presentation, prepare demo scenarios (e.g., simulated rod failure). |

## Scalability
While designed for the Baghewala Field, the architecture is easily scalable to other heavy oil assets in India.
- **ONGC Fields:** Can be rapidly adapted for Mehsana and Balol heavy oil fields in Gujarat by retraining the Neural ODE with localized geological properties and fluid PVT data.
- **Dockerized Microservices:** The software stack can scale horizontally in the cloud to monitor hundreds of wells simultaneously.

## Cost-Benefit Analysis
- **Increased Production:** Early detection of pump unsetting and optimal CSS cycles can prevent production deferment.
- **Reduced Lifting Costs:** Energy optimization of the SRP (avoiding fluid pound, reducing SPM when fillage is low) directly reduces electricity costs.
- **Decreased Workovers:** Rod string failures require expensive pulling units and result in days of lost production. Predicting failures 24 hours in advance allows for cheap preventative maintenance.

## Industry Benchmarks
Digital Twin implementations in the O&G sector have proven highly viable:
- **Equinor:** Reduced operational costs by up to 20% on the Johan Sverdrup field using integrated digital twins.
- **Shell & BP:** Widely utilize physics-informed machine learning for ESP and SRP surveillance, extending mean time between failures (MTBF) significantly.

## Risk Assessment
1. **Data Quality Risk:** Missing or noisy SCADA data.
   *Mitigation:* Implement Kalman Filters and robust imputation techniques in the edge preprocessing pipeline.
2. **Model Drift:** Over time, reservoir characteristics change.
   *Mitigation:* The Digital Twin will feature an automated retraining pipeline triggered by statistical drift detection.
3. **Adoption Resistance:** Field operators may distrust AI recommendations.
   *Mitigation:* Use highly interpretable models (like TFT) and display the underlying physics logic alongside AI predictions on the dashboard.
