# 💡 Smart Streetlight Predictive Maintenance Dashboard

An AI-powered IoT dashboard built for modern smart cities. This platform transitions municipal streetlight infrastructure from a *reactive* maintenance model to a *proactive* one, using Unsupervised Machine Learning and Generative AI.

## 🚀 The Problem
Currently, city streetlight maintenance is highly inefficient. Municipalities fix streetlights only after a citizen calls to complain or by paying crews to drive around at night looking for burnt-out bulbs. This leads to wasted energy, high maintenance costs, and reduced public safety in poorly lit areas.

## 🌟 Our Solution
We built an end-to-end simulation and monitoring dashboard that analyzes real-time electrical telemetry (voltage, current, and power) from streetlights to automatically:
1. **Detect Anomalies:** Flags broken or failing streetlights using Unsupervised Machine Learning.
2. **Diagnose Faults:** Categorizes the exact hardware issue (e.g., Burnt Bulb, Voltage Surge, Flickering).
3. **Dispatch Crews:** Uses Generative AI to automatically draft actionable maintenance work orders for electrical crews before citizens even notice a problem.

## 🛠️ Technical Stack
* **Frontend:** Streamlit, Folium (Interactive Geographic Mapping)
* **Data Simulation:** Pandas, NumPy (Synthetically injecting probabilistic hardware faults into UCI Household Power Data)
* **Machine Learning:** Scikit-Learn (`IsolationForest` for anomaly detection)
* **Generative AI:** Groq API, Meta Llama-3-8b-8192

## ⚙️ Pipeline Architecture
1. **The Simulator (`data_prep.py`):** Generates a 50-node IoT network and probabilistically injects specific hardware faults into the time-series sensor data.
2. **The Anomaly Hunter (`detector.py`):** Analyzes power variance and voltage spikes, mathematically isolating anomalous behavior using an auto-calibrated `IsolationForest`.
3. **The Diagnostician (`classifier.py`):** A logic engine that evaluates the `on_ratio` and coefficient of variation of power to accurately classify the specific fault type and calculate evaluation metrics against ground-truth labels.
4. **The Command Center (`app.py`):** The interactive UI that visualizes the metrics, generates dynamic map filters, and orchestrates the AI reporting workflow.

## 💻 How to Run Locally

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Set API Key
Export your Groq API key to enable the Generative AI maintenance work orders:
```bash
export GROQ_API_KEY="your_api_key_here"
```

### 3. Run the Dashboard
```bash
streamlit run app.py
```

## 🏆 Hackathon Submission
Submitted by **Team 07** for Division A.
