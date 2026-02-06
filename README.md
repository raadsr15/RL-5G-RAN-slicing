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

## 🔬 Methodology

### 1. Problem Formulation

The dynamic radio resource allocation problem for 5G RAN network slicing is formulated as a **Markov Decision Process (MDP)**. The objective is to optimally allocate a fixed number of radio resource blocks (RBs) among heterogeneous service slices—eMBB, URLLC, and mMTC—while satisfying slice-specific Service Level Agreements (SLAs) related to throughput and latency.

At each decision epoch, the agent observes the current network state and selects a continuous RB allocation vector. The action is normalized to ensure that the total allocated resources do not exceed the available RB budget.

---

### 2. Environment Design

A custom simulation environment is implemented using the **Gymnasium** framework to emulate end-to-end RAN slicing behavior. Each network slice is modeled with independent traffic arrival rates and queue dynamics, reflecting heterogeneous service requirements.

Queue evolution follows a discrete-time update rule based on incoming traffic and allocated service capacity. Latency is estimated from queue backlogs and service rates, with strict constraints applied to URLLC traffic. The environment deterministically transitions between states based on the agent’s actions and observed traffic conditions.

---

### 3. State and Action Space

The **state space** captures slice-level network information, including queue lengths and traffic arrival rates for each slice. This representation provides sufficient observability for the agent to learn congestion-aware and SLA-compliant allocation policies.

The **action space** is continuous and represents the proportion of total RBs allocated to each slice. Actions are clipped and normalized to enforce feasibility and physical consistency of resource allocation.

---

### 4. Reward Function Design

An SLA-aware reward function is designed to jointly optimize throughput and latency performance. Positive rewards are assigned proportionally to the successfully served traffic, while penalties are imposed for SLA violations such as insufficient throughput or excessive latency.

To reflect service criticality, higher penalty weights are assigned to URLLC SLA violations, followed by eMBB and mMTC, ensuring priority-aware learning behavior.

---

### 5. Learning Algorithm

The resource allocation policy is learned using **Proximal Policy Optimization (PPO)**, a policy-gradient reinforcement learning algorithm well-suited for continuous control problems. PPO provides stable policy updates by constraining the deviation between successive policies.

The agent is trained over multiple episodes, and performance is evaluated using system-level metrics including average throughput, SLA violation rate, queue stability, and resource allocation fairness across slices.

---

## 📊 Results

The trained agent demonstrates:
- Improved SLA compliance, especially for URLLC
- Stable queue dynamics under heterogeneous traffic
- Adaptive RB allocation strategies
- Superior performance compared to static slicing baselines

---
