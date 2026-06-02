Miguel Xochicale

# 

<div style="background-color: rgba(22,22,22,0.75);    border-radius: 10px;    text-align:center;    padding: 0px;    padding-left: 1.5em;    padding-right: 1.5em;    max-width: min-content;    min-width: max-content;    margin-left: auto;    margin-right: auto;    padding-top: 0.2em;    padding-bottom: 0.2em;    line-height: 1.5em!important;">

<span style="color:#939393; font-size:1.75em; text-align:left; display:block;">

<span style="color:#e0e0e0; font-size:1.65em; display:block; font-weight:600;">Modernising
Robotics Skills  
for Collaborative Science</span>

<!-- 
Distributed Intelligence, Cloud Computing, and Sensor-Driven Discovery Across Networked Systems
-->

</span>

------------------------------------------------------------------------

<span style="font-size:0.55em; color:#aaaaaa;">[**Miguel
Xochicale**](http://name-surname.github.io/) · [UCL Advanced Research
Computing](https://www.ucl.ac.uk/advanced-research-computing/)</span>

</div>

<div class="footer">

<span class="dim-text" style="&quot;text-align:left;'">Q1-2026
[(web-animations 2025 by
mxochicale)](https://mxochicale.github.io/web-animations/)</span>

</div>

<div class="notes">

<span style="border-bottom: 0.5px solid #00ccff;">[`open-healthcare-slides`](https://github.com/mxochicale/physical-ai-in-healthcare-slides/)</span>

</div>

<!-- ============================================================
     OVERVIEW
     ============================================================ -->

## Overview

<div class="columns">

<div class="column" width="50%">

### What We’ll Cover

1.  **Introduction** — Modernising robotics skills at UCL
2.  **UCL Infrastructure** — Cloud, network & physical layers
3.  **Demonstrations** — Real use cases & live tooling
4.  **Future Work** — Next hackathons & calls to action

</div>

<div class="column" width="50%">

### Key Themes

> [!NOTE]
>
> ### :cloud: Cloud-native robotics
>
> Kubernetes, Terraform, container registries

> [!TIP]
>
> ### :robot: Simulation at scale
>
> IsaacSim, IsaacLab, reinforcement learning

> [!IMPORTANT]
>
> ### :busts_in_silhouette: Collaborative science
>
> Cross-department infrastructure, shared testbeds

</div>

</div>

<!-- ============================================================
     SECTION: INTRODUCTION
     ============================================================ -->

# Introduction

**Modernising Robotics Skills**

<div class="notes">

Set the scene: why does UCL need modernised robotics infrastructure? The
challenge is bridging simulation, cloud compute, and real sensors in a
way that’s accessible to researchers and students.

</div>

<!-- ============================================================ -->

## :wrench: Hacking Cloud Brains, Physical Sensors, and the Network, and Orchestrating Talent

<div id="fig-hackathon">

<img src="figures/team-ucl-cps-hackathon.svg" style="width:90.0%"
data-fig-align="center" />

Figure 1: *Participants working across cyber-physical systems, cloud
layers, and sensor networks at UCL Here East.*

</div>

<div class="notes">

Describe the hackathon format: participants connected VMs, physical
sensors, and cloud nodes in a supervised setting. This became the model
for scaling robotics education at UCL.

</div>

<!-- ============================================================
     SECTION: UCL INFRASTRUCTURE
     ============================================================ -->

# UCL Infrastructure

**Orchestrating Cloud, Network, and Physical Sensors**

<div class="notes">

Walk through the three layers: cloud VMs managed via Terraform/k8s, the
campus network, and physical hardware (sensors, robots).

</div>

<!-- ============================================================ -->

## :robot: UCL Infrastructure Overview

<div id="fig-network">

<img src="figures/cyber-physical-hackathon-network.svg"
style="width:88.0%" data-fig-align="center" />

Figure 2: *Server topology and network communication across UCL’s
cyber-physical infrastructure.*

</div>

<div class="notes">

Key point: the infrastructure is reproducible. Terraform configs and
container images are versioned on GitHub, so any team can spin up the
same environment.

> [!TIP]
>
> ### Infrastructure Stack
>
> - **Compute**: VMs managed with Terraform + Kubernetes (k8s)  
> - **Containers**: ROS 2 images via GitHub Container Registry  
> - **Middleware**: `zenoh-plugin-ros2dds` for VM↔VM and bare-metal↔VM
>   bridging  
> - **Networking**: High-performance campus fabric, 10 Gbps+ links

</div>

<!-- ============================================================
     SECTION: DEMOS
     ============================================================ -->

# Demonstrations

**Cloud Brains · Physical Sensors · Real Networks**

<div class="notes">

Three demos: (1) VM-to-VM ROS 2 comms via zenoh, (2) IsaacSim
interactive control, (3) IsaacLab RL training at scale.

</div>

<!-- ============================================================ -->

## Demo 1. VM↔VM Communication with `zenoh-plugin-ros2dds`

<div class="columns">

<div class="column" width="35%">

### What Was Built

- ROS 2 Docker container pushed to GitHub Container Registry
- VMs provisioned and torn down with **Terraform + k8s**
- `zenoh-plugin-ros2dds` bridges DDS traffic across VM boundaries
- Enables bare-metal ↔ VM and VM ↔ VM ROS 2 topic sharing with **zero
  config changes** on the robot side

</div>

<div class="column" width="65%">

<div id="fig-pipeline">

<img src="figures/hacking-pipeline.svg" data-fig-align="center" />

Figure 3: *End-to-end pipeline: container build → registry → VM
deployment → zenoh bridge → ROS 2 topic relay.*

</div>

</div>

</div>

<div class="notes">

Emphasise that the zenoh bridge makes the infrastructure topology
transparent to application code. ROS 2 nodes don’t need to know they’re
crossing VM boundaries.

> [!NOTE]
>
> **Repo**:
> [UCL-CyberPhysicalSystems/hackathon-01](https://github.com/UCL-CyberPhysicalSystems/hackathon-01)

</div>

<!-- ============================================================ -->

## Demo 2. IsaacSim & IsaacLab

<div class="columns">

<div class="column" width="38%">

<div id="fig-isaacsim">

<img src="figures/ezgif-4fa230460975b3.gif" style="width:70.0%"
data-fig-align="center" />

Figure 4: *IsaacSim IDE: interactive robot key control.*

</div>

<div id="fig-franka">

<img src="figures/ezgif-Isaac-Lift-Cube-Franka-v0.gif"
style="width:70.0%" data-fig-align="center" />

Figure 5: *Franka Lift Cube — RL policy training.*

</div>

</div>

<div class="column" width="60%">

<div id="fig-humanoid-train">

<img src="figures/ezgif-train_Isaac-Humanoid-v0_iter_2000.gif"
style="width:70.0%" data-fig-align="center" />

Figure 6: *Humanoid training — 128 parallel environments, 2000
iterations.*

</div>

``` bash
# Train
./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/train.py \
  --task Isaac-Humanoid-v0 --num_envs 128 \
  --max_iterations 2000 --headless

# Play / evaluate
./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/play.py \
  --task Isaac-Humanoid-v0 --num_envs 1000 \
  --checkpoint logs/rsl_rl/humanoid
```

</div>

</div>

<div class="notes">

IsaacLab unlocks GPU-parallelised RL training on UCL’s compute nodes.
Highlight the jump from 128 envs (training) to 1000 envs (evaluation) as
evidence of the infrastructure’s headroom.

<img src="figures/ezgif-train_Isaac-Humanoid-v0_iter_2000.gif"
data-fig-align="center" />

./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/train.py –task
Isaac-Humanoid-v0 –num_envs 128 –max_iterations 2000 –headless

<img src="figures/ezgif-play_Isaac-Humanoid-v0_1000env.gif"
data-fig-align="center" />

./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/play.py –task
Isaac-Humanoid-v0 –num_envs 1000 –checkpoint logs/rsl_rl/humanoid

</div>

<!-- ============================================================
     SECTION: FUTURE WORK & TAKEAWAYS
     ============================================================ -->

# Future Work & Key Takeaways

<div class="notes">

Wrap up: upcoming hackathons, what the community should take away, and a
concrete call to action for collaboration and funding.

</div>

<!-- ============================================================ -->

## Upcoming Hackathons

<div class="columns">

<div class="column" width="40%">

> [!IMPORTANT]
>
> ### :calendar: Hackathon 1 — **2 March 2026**
>
> **Preliminary Small Hackathon**  
> Feasibility testing & idea generation  
> 📍 UCL Here East, Room G40

> [!TIP]
>
> ### :calendar: Hackathon 2 — **Q4 2026**
>
> **Larger Collaborative Hackathon**  
> Explore ideas · Create research projects  
> 📍 TBC

[**Register / follow progress
→**](https://github.com/UCL-CyberPhysicalSystems/hackathon-01)

</div>

<div class="column" width="60%">

<div id="fig-future-network">

<img src="figures/cyber-physical-hackathon-network.svg"
style="width:95.0%" data-fig-align="center" />

Figure 7: *The same infrastructure will underpin both hackathons.*

</div>

</div>

</div>

<div class="notes">

Hackathon 1 is a low-stakes day to validate the setup with a small
group. Hackathon 2 opens it to a much larger audience with external
collaborators.

</div>

<!-- ============================================================ -->

## Key Takeaways

<div style="font-size: 90%;">

<div class="incremental">

- **:unlock: Lowering the barrier to advanced robotics** Cloud-ready,
  cost-aware infrastructure enables hands-on training with real sensors
  and real network constraints, without specialist hardware budgets.

- **:arrows_counterclockwise: A proven, scalable model for
  collaboration** High-performance networking and shared platforms make
  cross-department and cross-institution work practical and repeatable.

- **:test_tube: A living testbed for research & training** The
  infrastructure supports skills transfer, rapid prototyping of robotics
  workflows, and publishable research experiments.

- **:handshake: Call to Action** Partner with us to extend the testbed.
  We are actively seeking collaboration and funding to scale training,
  expand use cases, and deploy beyond UCL.

</div>

</div>

<div class="notes">

Deliver these one at a time with the incremental reveal. End on the call
to action — have contact details ready.

1.  Lowering the Barrier to Advanced Robotics
2.  A Scalable Model for Cross-Department Collaboration
3.  Real Sensors, Real Networks, Real Constraints
4.  High-Performance Networking Enables New Workflows
5.  Cloud-Ready Robotics Training at Scale
6.  Hands-On Learning Accelerates Skills Transfer
7.  Cost-Aware, Sustainable Infrastructure Design
8.  A Testbed for Research, Training, and Innovation
9.  Clear Opportunities for Collaboration & Funding

**Sciortino et al. 2017** in Computers in Biology and Medicine
https://doi.org/10.1016/j.compbiomed.2017.01.008;  
**He et al. 2021** in Front. Med.
https://doi.org/10.3389/fmed.2021.729978

</div>

<!-- ============================================================ -->

## Thank You · Let’s Connect

<div class="columns">

<div class="column" width="50%">

### UCL CEGE

[Mickey Li](https://github.com/mhl787156) · [Chris
Bendkowski](https://github.com/ctbend)

### UCL ARC

[Marlon Wijeyasinghe](https://github.com/mwij02) · [James
Legg](https://github.com/cjlegg) · [Mack
Nixon](https://github.com/TOADD) · [Mahmoud
Abdelrazek](https://github.com/TOADD) · [Sunny
Park](https://github.com/TOADD) · [Emily
Dubrovska](https://github.com/pineapple-cat) · [Yagmur
Ozdemir](https://github.com/yidilozdemir) · [Ruaridh
Gollifer](https://github.com/ruaridhg) · [Samantha
Ahern](https://github.com/quirksahern) · [James
Hetherington](https://github.com/jamespjh)

</div>

<div class="column" width="50%">

### Teams

**Unified-AI**: Andrew Esterson · Sylvie Ramos  
**Condenser**: Sam Reece · Brian Maher

------------------------------------------------------------------------

> [!NOTE]
>
> ### :speech_balloon: Get in Touch
>
> **GitHub**: [github.com/mxochicale](https://github.com/mxochicale)  
> **UCL ARC**: [ucl.ac.uk/arc](https://www.ucl.ac.uk/arc)  
> **Hackathon repo**:
> [UCL-CyberPhysicalSystems/hackathon-01](https://github.com/UCL-CyberPhysicalSystems/hackathon-01)

</div>

</div>

<div class="notes">

Thank the room. Leave the slide up during questions — GitHub handle and
repo URL are visible for anyone who wants to follow up.

</div>

<!-- ============================================================
     EXTRA SLIDES (appendix)
     ============================================================ -->

# Appendix

Extra slides for Q&A

<!-- ============================================================ -->

## My Journey

<img src="figures/mx.svg" style="width:100.0%"
data-fig-align="center" />

<div class="notes">

Use this slide if asked about background — brief overview of the path
from robotics research to ARC infrastructure work.

</div>
