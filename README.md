# Awesome Trajectory Optimization 🚀

<p align="center">
  <img src="assets/banner.svg" alt="Awesome Trajectory Optimization Banner" width="100%">
</p>

<p align="center">
  <a href="https://github.com/ishandutta2007/Awesome-Awesome-Awesome"><img src="https://img.shields.io/badge/Awesome-%E2%9C%94-blueviolet?style=flat-square&logo=github" alt="Awesome"/></a><a href="https://discord.gg/jc4xtF58Ve"><img src="https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord" /></a><a href="https://github.com/ishandutta2007/Awesome-Trajectory-Optimization/stargazers"><img src="https://img.shields.io/github/stars/ishandutta2007/Awesome-Trajectory-Optimization?style=flat-square" alt="Stars"/></a><a href="https://github.com/ishandutta2007/Awesome-Trajectory-Optimization/network/members"><img src="https://img.shields.io/github/forks/ishandutta2007/Awesome-Trajectory-Optimization?style=flat-square" alt="Forks"/></a><a href="https://github.com/ishandutta2007"><img alt="GitHub followers" src="https://img.shields.io/github/followers/ishandutta2007?label=Follow" /></a>
</p>

---

## 🌟 Trajectory Optimization in AI: Evolution, Variants, Types, & Applications

**Trajectory Optimization** is a foundational computational framework in artificial intelligence, robotics, and reinforcement learning (RL). It focuses on finding a sequence of control inputs and system states (a trajectory) that minimizes a specified cost function (such as energy consumption or travel time) while satisfying physical, environmental, and system constraints. In AI, trajectory optimization bridges the gap between high-level behavioral planning and low-level physical execution, transforming abstract strategic goals into precise, safe, and dynamically feasible physical trajectories.

---

## 📅 1. The Chronological Evolution

The development of trajectory calculation has transitioned from classical numerical physics solvers to data-driven neural policy guides and multi-horizon generative transformer models.

```mermaid
flowchart LR
    A["Classical Boundary Solvers<br/>(Shooting / Collocation Math)"]
    --> B["Model Predictive Control (MPC)<br/>(Real-Time Receding Horizons)"]
    --> C["Modern Neural & Generative Trajectories<br/>(Decision Transformers / Diffuser Networks)"]
```

| Era / Stage | Year | Paper | Description & Limitations |
| :--- | :--- | :--- | :--- |
| [**The Classical Numerical Solvers Era (Pre-Deep Learning)**](details/classical_solvers.md) | 1987 | [Hargraves & Paris (1987)](https://arc.aiaa.org/doi/10.2514/3.20223) | **Concept:** Rooted in traditional optimal control theory and numerical optimal control. Standard methodologies focused on solving explicit differential equations using mathematical pipelines like **Direct Transcription**, **Collocation**, or **Shooting Methods**.<br><br>**Limitation:** Required a completely perfect, explicit analytical physics model of the system. These setups were highly latent, prone to getting stuck in local minima, and struggled with complex, high-dimensional spaces like soft robotics. |
| [**The Real-Time Receding Horizon Era (Model Predictive Control / MPC, ~2010s)**](details/mpc.md) | 1978 | [Richalet et al. (1978)](https://doi.org/10.1016/0005-1098(78)90001-8) | **Concept:** Shifted from calculating a static global path beforehand to continuously resolving trajectory chunks online. By solving an optimization problem over a short, finite future horizon, executing the very first step, and immediately re-solving with updated physical tracking data, MPC introduced robust feedback loops.<br><br>**Limitation:** Limited by the available on-board computer hardware clock speed, forcing developers to simplify the system's mathematical physics models to keep calculations fast. |
| [**The Deep Neural & Generative Sequence Era (~2020s–Present)**](details/deep_neural_generative.md) | 2021 | [Chen et al. (2021)](https://arxiv.org/abs/2106.01345) | **Concept:** The current modern state-of-the-art framework. Trajectory optimization merged with generative deep learning. Architectures like **Decision Transformers** and **Diffusion Policy / Diffuser Networks** reframe trajectory planning as a generative sequence modeling task. Instead of executing step-by-step calculus loops, the network treats path generation exactly like text completion or image denoising, outputting multi-horizon, fluid trajectories instantly. |

---

## ⚙️ 2. Core Functional & Transcription Variants

Trajectory optimization frameworks are strictly categorized based on how the underlying mathematical state and control dimensions are discretized and handled across time intervals.

| Variant | Year | Paper | Mechanism & Properties |
| :--- | :--- | :--- | :--- |
| [**Indirect Methods (Optimality Conditions)**](details/indirect_methods.md) | 1956 | [Pontryagin et al. (1956)](https://books.google.com/books?id=0s5QAAAAMAAJ) | **Mechanism:** Uses Calculus of Variations and *Pontryagin’s Minimum Principle* to convert the trajectory problem into a complex system of boundary value problems, solving for theoretical optimality conditions first.<br><br>**Pros:** Provides highly exact mathematical solutions, but is notoriously difficult to initialize and fails when encountering non-smooth environmental limits (like sudden physical collisions). |
| [**Direct Shooting Methods**](details/direct_shooting.md) | 1971 | [Hicks & Ray (1971)](https://doi.org/10.1002/cjce.5450490418) | **Mechanism:** Discretizes *only* the control variables over a sequence of time blocks. The algorithm parameterizes the inputs, uses a simulator to step the physics forward ("shoots" the trajectory), checks the terminal errors, and optimizes the control parameters iteratively. |
| [**Direct Collocation / Transcription Methods**](details/direct_collocation.md) | 1987 | [Hargraves & Paris (1987)](https://arc.aiaa.org/doi/10.2514/3.20223) | **Mechanism:** Discretizes *both* the system states and the control variables simultaneously across a fine chronological grid. The optimization engine treats the physical equations of motion as individual structural equality constraints at every single grid node (collocation point).<br><br>**Pros:** Easily handles highly intricate path limitations (such as absolute obstacle avoidance boundaries), making it the primary engineering baseline for autonomous systems. |

---

## 🧠 3. Deep Learning & Reinforcement Learning Integrations

Modern artificial intelligence pipelines utilize distinct architectural layers to accelerate trajectory generation or guide neural exploration.

| Integration | Year | Paper | Mechanism & Examples |
| :--- | :--- | :--- | :--- |
| [**Model-Based Reinforcement Learning (MBRL / Trajectory Rollouts)**](details/mbrl.md) | 2018 | [Ha & Schmidhuber (2018)](https://arxiv.org/abs/1803.10122) | **Mechanism:** The AI system trains a deep neural network to act as a **World Model**, learning the transition physics of the environment from raw interaction logs. It then runs imaginary trajectory rollouts inside its hidden layers to optimize its policy network without risking physical damage.<br><br>**Examples:** World Models, DreamerV3, and MuZero. |
| [**Diffusion-Based Trajectory Policy (Diffuser)**](details/diffuser_policy.md) | 2022 | [Janner et al. (2022)](https://arxiv.org/abs/2205.09991) | **Mechanism:** Replicates image diffusion. It initializes a trajectory path as pure, random Gaussian noise vectors over a fixed sequence window. It then iteratively removes noise tokens over a series of steps, molding the random array into a globally optimal, obstacle-free trajectory path matching a targeted final reward constraint. |
| [**Guided Policy Search (GPS)**](details/guided_policy_search.md) | 2013 | [Levine & Koltun (2013)](http://proceedings.mlr.press/v28/levine13.html) | **Mechanism:** Uses classical trajectory optimization (like Differential Dynamic Programming - DDP) to discover high-quality localized trajectory paths, utilizing those trajectories as precise supervised demonstrations to rapidly train a deep, global neural network policy. |

---

## 🛡️ 4. Production Engineering Challenges & Mitigations

Executing trajectory calculations across real-world physical boundaries and low-latency control loops introduces critical computational and safety constraints.

| Challenge / Bottleneck | Year | Paper | Problem & Mitigation |
| :--- | :--- | :--- | :--- |
| [**The Local Minima and Obstacle Explosion Barrier**](details/local_minima_obstacle.md) | 2020 | [Banerjee et al. (2020)](https://ieeexplore.ieee.org/document/9172773) | **The Problem:** When an autonomous system maps a complex architectural space containing hundreds of moving obstacles, the mathematical cost function becomes highly non-convex. Traditional optimization engines frequently get trapped in sub-optimal local minima, causing the system to freeze or fail.<br><br>**Mitigation:** Implementing **Neural Warm-Starting**. A deep convolutional network or vision-language model evaluates the scene context first, instantly outputting a near-optimal candidate path array to seed the numerical solver, bypassing the exploration loop. |
| [**The High-Frequency Inference Latency Bottleneck**](details/inference_latency.md) | 2015 | [Rusu et al. (2015)](https://arxiv.org/abs/1511.06295) | **The Problem:** Safety-critical physical systems (like an autonomous vehicle correcting for a tyre slip) require control loops running at speeds exceeding $100\text{ Hz}$ to $1000\text{ Hz}$. Standard deep generative models can introduce processing latencies that stall execution rates.<br><br>**Mitigation:** Running **Actor-Critic Distillation Frameworks**. Complex multi-horizon trajectory generation is calculated on powerful edge chips or server nodes, distilling the optimal output trajectories down into highly compact, single-turn student networks running on fast microcontrollers. |

---

## 🌐 5. Frontier Real-World AI Applications

| Application | Year | Paper | Description |
| :--- | :--- | :--- | :--- |
| [**Autonomous Vehicle Obstacle Avoidance & Path Replanning**](details/autonomous_vehicles.md) | 2007 | [Falcone et al. (2007)](https://ieeexplore.ieee.org/document/4200833) | **Application:** Coordinates active driving paths for autonomous consumer vehicles or long-haul trucks. Trajectory optimization modules ingest streaming lidar and computer vision tokens, calculating safe lane changes and collision avoidance curves at high speeds to manage dynamic highway traffic boundaries smoothly. |
| [**Spatio-Temporal Control for Bipedal Humanoid Robotics**](details/humanoid_robotics.md) | 2016 | [Kuindersma et al. (2016)](https://doi.org/10.1007/s10514-015-9479-3) | **Application:** Drives real-time locomotion stacks for advanced bipedal and quadrupedal robots. Trajectory engines map out target center-of-mass vectors and foot placement coordinate timelines, calculating precise joint torque adjustments to help the machine cross uneven, volatile debris fields stably. |
| [**Next-Generation Rocketry & Aerospace Guidance Loops**](details/aerospace_guidance.md) | 2007 | [Açıkmeşe & Ploen (2007)](https://arc.aiaa.org/doi/10.2514/1.27350) | **Application:** Directs vertical landing maneuvers for reusable orbital booster rockets or orbital station-keeping systems. Real-time trajectory optimization solvers continuously evaluate shifting wind shears, fuel weight decay rates, and telemetry variations, updating aerodynamic grid-fin parameters dynamically to achieve pinpoint landing accuracy. |

---

## 📈 Star History

<div align="center">
<a href="https://www.star-history.com/?repos=ishandutta2007%2FAwesome-Trajectory-Optimization&type=date&legend=bottom-right">
<picture>
<source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=ishandutta2007/Awesome-Trajectory-Optimization&type=date&theme=dark&legend=bottom-right" />
<source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=ishandutta2007/Awesome-Trajectory-Optimization&type=date&legend=bottom-right" />
<img alt="Star History Chart" src="https://api.star-history.com/chart?repos=ishandutta2007/Awesome-Trajectory-Optimization&type=date&legend=bottom-right" />
</picture>
</a>
</div>
