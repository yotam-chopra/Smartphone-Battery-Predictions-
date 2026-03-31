# 📱 Smartphone Battery Modeling (MCM 2026)

> A physics-based, interpretable model for predicting smartphone battery behavior under real-world usage, aging, and environmental conditions.

---

## 🚀 Overview

Smartphone batteries often behave unpredictably — devices may drain quickly under heavy use or shut down even when a nonzero battery percentage is displayed.  

This project develops a **continuous-time, physics-based model** that explains and predicts these behaviors by linking:

- User activity (CPU, screen, network, GPS)
- Battery physics (charge, voltage, resistance)
- Environmental factors (temperature)
- Battery aging (state of health)

Unlike purely data-driven approaches, this model is **interpretable, extensible, and grounded in physical principles**.

---

## 🧠 Key Ideas

### 1. State of Charge (SOC) Dynamics
- Battery charge evolves via a **differential equation**
- Driven by current draw and conservation of charge
- SOC alone does **not** determine when a phone dies

### 2. Voltage-Limited Shutdown ⚡
- Devices shut down when **voltage drops below a threshold**, not when charge is zero
- Explains:
  - Phones dying at 10–20%
  - Sudden shutdown during heavy usage
  - Worse performance in cold weather

### 3. Power Decomposition
Total power consumption is modeled as:
- Screen brightness
- CPU load
- Network activity
- GPS usage
- Background processes

This enables **scenario-based simulation** (e.g., gaming vs reading).

### 4. Aging + Temperature Effects
- Battery health (SOH) reduces capacity and increases resistance
- Cold temperatures:
  - Decrease effective capacity  
  - Increase internal resistance  
- Result: earlier shutdown due to **voltage sag**

### 5. State Estimation (EKF + HMM)
- **Extended Kalman Filter (EKF)** improves SOC estimation using voltage
- **Hidden Markov Model (HMM)** captures changing usage patterns

---

## 📊 Results & Insights

### 🔋 Realistic Behavior Captured
- Time-to-empty increases with SOC
- Large variation depending on usage intensity
- Voltage-limited shutdown reproduced

### ❄️ Temperature Effects
- Cold environments significantly reduce battery life
- High-load tasks amplify voltage collapse

### ⚡ Dominant Drivers of Battery Drain
1. Temperature  
2. Sustained power demand (CPU + network)  
3. Voltage limitations (internal resistance + load)  

---

## 🎮 Usage Scenarios Simulated

- Idle (screen off)
- Reading (low brightness)
- Video streaming
- Navigation (GPS + weak signal)
- Gaming (high CPU)

Each scenario produces different **power profiles and battery lifetimes**.

---

## 💡 Key Takeaways

### For Users
- Avoid high-CPU tasks (gaming/navigation) at low battery
- Reduce brightness during long sessions
- Use Wi-Fi instead of weak cellular
- Keep phone warm in cold environments
- Don’t rely solely on battery percentage

### For Systems (OS Design)
- Voltage-aware battery indicators
- Temperature-adaptive performance scaling
- Dynamic workload throttling near shutdown
- Smarter usage-based power modes

---

## 🧪 Validation

- Tested on real smartphone sensing datasets
- Captures:
  - Correct SOC trends
  - Realistic usage differences
  - Time-to-empty behavior

---

## 🛠️ Tech & Methods

- Differential equations (continuous-time modeling)
- Electrical modeling (Thevenin equivalent circuit)
- Extended Kalman Filter (EKF)
- Hidden Markov Models (HMM)
- Python-based simulation

---

## 📈 Why This Project Matters

- Battery behavior is **not just about charge — it’s about voltage**
- Provides a **physically interpretable alternative** to black-box models
- Explains real-world phenomena like:
  - Sudden shutdowns
  - Cold-weather battery drain
  - Performance degradation with aging

---

## 📄 Paper

Full report included in this repository (MCM 2026 submission).
