# StableRL_VoltageCtrl
This repository contains source code necessary to reproduce the results presented in the following paper: Stability Constrained Reinforcement Learning for Real-Time Voltage Control (https://arxiv.org/pdf/2109.14854.pdf).

Authors: Yuanyuan Shi, Guannan Qu, Steven Low, Anima Anandkumar and Adam Wierman

Accepted to be present at 2022 American Control Conference (ACC).

### Citation
@inproceedings{shi2021stability,
  title={Stability constrained reinforcement learning for real-time voltage control},
  author={Shi, Yuanyuan and Qu, Guannan and Low, Steven and Anandkumar, Anima and Wierman, Adam},
  booktitle={2022 Annual American Control Conference (ACC)},
  year={2022},
  organization={IEEE}
}

### Voltage Control Performance in South California Edison 56 bus distribution system

### Visualization of DDPG, Stable-DDPG and Baseline Linear Policy

![alt text](https://github.com/Yuanyuan-Shi/stable_rl_voltagecontrol/blob/main/policy.png)

### DDPG v.s. Stable-DDPG v.s. Baseline Linear Policy

As shown in Fig 4 in the submitted paper, baseline DDPG does not guarantee stability and thus can lead to ``infinite'' voltage recovery time and control cost. To obtain a reasonable comparison, we limit the max episode length to be T= 100, and compare the voltage recovery time (steps) and reactive power consumption (MVar) on 500 different voltage violation scenarios. Here are the results.

|            |Voltage recovery time (Steps) Mean |Std       |Reactive power consumption (MVar) Mean|Std       |
| -----------|-----------------------------------|----------|--------------------------------------|----------|
| Linear     |     48.38                         |   19.57  |      179.08                          | 129.03   |
| Stable-DDPG|     31.96                         |   14.49  |      119.30                          | 89.05    |
| DDPG       |     42.87                         |   38.32  |      152.53                          | 175.62   |


Out of the 500 scenarios, we found that DDPG is able to stabilize 350 scenarios. For the scenarios baseline DDPG can stabilize, we observed that it can further reduce the control cost and recovery time, compared to Stable-DDPG and linear policy, possibly due to the more expressive power of standard neural network compared to monotone network.

Table 2: Performance of linear and Stable-DDPG policies on the 288 voltage violation scenarios where DDPG can stablize voltage. Note: reactive power consumption denotes the control cost.

|            |Voltage recovery time (Steps) Mean |Std       |Reactive power consumption (MVar) Mean|Std       |
| -----------|-----------------------------------|----------|--------------------------------------|----------|
| Linear     |     41.11                         |   18.93  |      128.81                          |  102.97  |
| Stable-DDPG|     25.80                         |   14.40  |      80.75                           |  67.98   |
| DDPG       |     18.38                         |   9.96   |      41.09                           |  39.86   |

