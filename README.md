# RL-Based Network Slicing for 5G RAN

Fifth-generation (5G) and emerging sixth-generation (6G) wireless networks must support heterogeneous services with diverse and often conflicting performance requirements, including enhanced Mobile Broadband (eMBB), Ultra-Reliable Low-Latency Communication (URLLC), and massive Machine-Type Communication (mMTC). Network slicing enables these services to coexist on shared radio access infrastructure by providing logical isolation and service-specific guarantees. However, dynamically allocating limited radio resources across slices while satisfying stringent service-level agreements (SLAs) remains a challenging problem, particularly under time-varying traffic conditions.

Conventional rule-based and optimization-driven resource allocation techniques often rely on static assumptions or carefully tuned heuristics, which limits their adaptability and scalability in realistic network environments. Reinforcement learning (RL) offers a data-driven alternative by allowing agents to learn adaptive control policies through interaction with the network, optimizing long-term system performance rather than instantaneous objectives.

This repository presents an RL-based framework for dynamic radio resource block (RB) allocation in a 5G RAN network slicing scenario. The problem is formulated as a constrained Markov Decision Process (MDP), where the state represents slice-level queue backlogs and traffic arrival rates, and the action corresponds to continuous RB allocation ratios across service slices. A Proximal Policy Optimization (PPO) agent is trained using an SLA-aware reward function that balances throughput maximization with latency constraint enforcement, incorporating slice-specific penalties to reflect differing service criticalities.

The framework is implemented using Gymnasium and Stable-Baselines3 and evaluated using system-level metrics relevant to wireless networking, including average throughput, SLA violation rate, queue stability, and resource allocation behavior. This work serves as a research-oriented prototype for AI-assisted wireless communication and provides a foundation for future studies in network slicing, edge intelligence, and 5G/6G systems.

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
