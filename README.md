# RL-Based Network Slicing for 5G RAN

This repository presents a reinforcement learning–based framework for
dynamic radio resource allocation in 5G RAN network slicing environments.

The problem is formulated as a constrained Markov Decision Process (MDP),
where a PPO agent learns to allocate radio resource blocks (RBs) across
heterogeneous service slices while satisfying SLA constraints.

---

## 📌 Key Features

- Gymnasium-based custom network slicing environment
- Three 5G service slices:
  - eMBB (enhanced Mobile Broadband)
  - URLLC (Ultra-Reliable Low-Latency Communication)
  - mMTC (massive Machine-Type Communication)
- SLA-aware reward design incorporating:
  - Throughput guarantees
  - Latency constraints
- PPO-based continuous control policy
- Evaluation using:
  - Reward convergence
  - SLA violation rate
  - Queue stability
  - Throughput per slice
  - RB allocation behavior
- Baseline comparison with fixed heuristic slicing

---

## 🧠 Methodology

- **State Space**: Queue lengths and traffic arrival rates per slice  
- **Action Space**: Continuous RB allocation ratios  
- **Reward Function**:
  - Positive reward for SLA satisfaction and throughput
  - Slice-specific penalties for SLA violations
- **RL Algorithm**: Proximal Policy Optimization (PPO)

---

## 📊 Results

The trained agent demonstrates:
- Improved SLA compliance, especially for URLLC
- Stable queue dynamics under heterogeneous traffic
- Adaptive RB allocation strategies
- Superior performance compared to static slicing baselines

---
