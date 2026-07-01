# 🚀 Domain-Randomised Deep Reinforcement Learning for Spacecraft Fault Recovery

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)]()
[![Stable-Baselines3](https://img.shields.io/badge/Stable--Baselines3-PPO-orange.svg)]()
[![Gymnasium](https://img.shields.io/badge/Gymnasium-RL-green.svg)]()
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)]()

Implementation accompanying the research paper:

> **Domain-Randomised Deep Reinforcement Learning for Spacecraft Fault Recovery: A Trade-Off Between Training Efficiency and Recovery Performance**

---

## 📖 Overview

This project investigates whether **domain randomisation** can provide a computationally efficient alternative to training multiple specialist reinforcement learning controllers for autonomous spacecraft fault recovery.

A custom **6-DOF spacecraft attitude recovery environment** was developed in Gymnasium, incorporating realistic actuator degradation and environmental uncertainty. Three Proximal Policy Optimisation (PPO) training strategies are evaluated:

- Nominal PPO
- Specialist PPO Ensemble
- Domain-Randomised PPO

The work analyses the trade-off between:

- Recovery performance
- Policy generalisation
- Training efficiency

---

## 🛰 Features

✔ Six-degree-of-freedom spacecraft attitude dynamics

✔ Continuous thruster degradation (0–100%)

✔ Complete thruster failures

✔ Gaussian sensor noise

✔ External disturbance torques

✔ ±10% spacecraft inertia uncertainty

✔ Domain Randomisation

✔ PPO-based control

✔ Quantitative evaluation framework

---

## 🏗 Repository Structure

```text
.
├── spacecraft_env.py          # Custom Gymnasium spacecraft environment
├── train_nominal.py           # Nominal PPO controller
├── train_specialist.py        # Specialist PPO controllers
├── train_domain_randomised.py # Domain-Randomised PPO
├── evaluate.py                # Performance evaluation
├── models/
├── results/
├── figures/
└── README.md
```

---

## ⚙ Environment

### State Space

```
s = [θx, θy, θz, ωx, ωy, ωz]
```

where

- θ = spacecraft orientation
- ω = angular velocity

---

### Action Space

Continuous thruster commands

```
a ∈ ℝ⁶
```

---

### Fault Models

The simulator includes:

| Fault | Description |
|----------|----------------|
| Thruster degradation | Continuous efficiency loss (0–100%) |
| Thruster failure | Complete actuator failure |
| Sensor noise | Gaussian |
| External disturbances | Constant disturbance torques |
| Inertia uncertainty | ±10% variation |

---

## 🤖 Reinforcement Learning

Algorithm:

- Proximal Policy Optimisation (PPO)

Framework:

- Stable-Baselines3

Environment:

- Gymnasium

---

## 📊 Experiments

Three controller architectures are compared.

### 1️⃣ Nominal PPO

Trained only under fault-free conditions.

---

### 2️⃣ Specialist PPO

Multiple policies trained individually for predefined fault scenarios.

---

### 3️⃣ Domain-Randomised PPO

A single policy trained over randomly sampled actuator effectiveness distributions.

---

## 📈 Evaluation Metrics

The controllers are evaluated using:

- Recovery Success Rate
- Recovery Accuracy
- Training Timesteps
- Training Efficiency
- Robustness to Unseen Faults

---

## 📄 Results

The domain-randomised controller:

- Maintains strong recovery performance across unseen degradation scenarios
- Requires significantly fewer training timesteps than specialist controllers
- Eliminates the need to maintain multiple trained policies

---

## 📚 Paper

**Title**

> Domain-Randomised Deep Reinforcement Learning for Spacecraft Fault Recovery: A Trade-Off Between Training Efficiency and Recovery Performance

---

## 🛠 Installation

Clone the repository

```bash
git clone https://github.com/yourusername/spacecraft-fault-recovery.git

cd spacecraft-fault-recovery
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

## ▶ Training

Nominal

```bash
python train_nominal.py
```

Specialist

```bash
python train_specialist.py
```

Domain Randomised

```bash
python train_domain_randomised.py
```

---

## 📊 Evaluation

```bash
python evaluate.py
```

---

## 📦 Dependencies

- Python 3.10+
- Gymnasium
- Stable-Baselines3
- NumPy
- PyTorch
- Matplotlib

---

## 👩‍💻 Author

**Hiya Singh**

Department of Computer Science and Engineering  
Specialisation in Artificial Intelligence and Machine Learning  
VIT Bhopal University

---

## 📜 Citation

If you use this repository, please cite:

```bibtex
@article{Singh2026,
  title={Domain-Randomised Deep Reinforcement Learning for Spacecraft Fault Recovery: A Trade-Off Between Training Efficiency and Recovery Performance},
  author={Hiya Singh},
  year={2026}
}
```

---

## ⭐ Acknowledgements

This work was developed as undergraduate research investigating the application of Deep Reinforcement Learning to autonomous spacecraft fault recovery under actuator degradation and uncertainty.
