# Inference Latency & Actor-Critic Distillation ⏱️

High-frequency, safety-critical systems require control loops running at rates exceeding $100\text{ Hz}$ to $1000\text{ Hz}$. Large-scale neural planners or solvers cannot meet these timing constraints directly on edge devices.

## 📋 Core Concepts

To bypass the latency of online trajectory optimization, developers use **Policy Distillation** (or knowledge distillation):

1. **Expert Generation:** An expensive, multi-horizon trajectory optimizer (the teacher) calculates optimal trajectories offline or on high-performance compute nodes.
2. **Student Training:** A compact, fast neural network (the student) is trained via supervised learning to mimic the actions or trajectories produced by the expert.
3. **Edge Deployment:** The student network—often a simple multilayer perceptron (MLP) or small CNN—is deployed on microcontrollers or edge chips, achieving sub-millisecond inference times.

---

## 📊 Distillation Process

```mermaid
flowchart TD
    Teacher[Expert Trajectory Planner / Solver] -->|Generates Trajectories| Dataset[(Expert Dataset)]
    Dataset -->|Supervised Training / Distillation| Student[Compact Student Network]
    Student -->|Deployed on Edge| Microcontroller[Fast Edge Microcontroller]
    Microcontroller -->|High Frequency Control (>1kHz)| Actuators[System Actuators]
```

---

## ⚠️ Key Trade-offs

- **Pros:** Real-time feedback capability on low-cost hardware.
- **Cons:** Generalization gap; if the student encounters a state outside the expert's training set, it might fail catastrophically.

---

## 📚 References
- Rusu, A. A., Colmenarejo, S. G., Gulcehre, C., Desjardins, G., Kirkpatrick, J., Pascanu, R., Mnih, V., Kavukcuoglu, K., & Hadsell, R. (2015). *Policy Distillation*. ICLR. [arXiv Link](https://arxiv.org/abs/1511.06295)
