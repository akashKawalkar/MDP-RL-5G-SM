Multi Sleep Mode with Q-Learning for 5G Energy Efficiency
🔍 Overview
With the rapid deployment of 5G and dense Small Base Station (SBS) infrastructure, network energy consumption has become a critical concern. While Base Stations (BSs) are responsible for over 70% of network energy use, they continue to consume up to 60% of power even when idle. This project explores an intelligent sleep mode management strategy using Q-Learning to enhance energy efficiency while preserving network Quality of Service (QoS).

🧠 Motivation
Binary ON/OFF sleep schemes often degrade network coverage and QoS. Instead, this project implements multi-level sleep modes, allowing SBSs to enter varying power states with different transition delays and power costs. By using Reinforcement Learning (Q-learning), SBSs can autonomously decide which sleep mode to enter based on real-time network conditions.

🏗️ System Architecture
Heterogeneous Network (HetNet):
Two-tier system with:

1x Macro Base Station (MBS) – always active.

4x Small Base Stations (SBSs) – managed using Q-learning.

Key Features:

SBSs operate in different sleep modes based on traffic, buffer state, and interference.

MBS provides guaranteed coverage and control signaling.

😴 Sleep Modes (from [27])
Sleep Mode	Components Shutdown	Activation Delay	Minimum Duration	Power (W)
SM1	PA + partial processing	35.68 μs	71.36 μs	13.2
SM2	More components	0.5 ms	1 ms	8.22
SM3	Most components	5 ms	10 ms	3.55
SM4	Full standby (not used)	0.5 s	1 s	3.0

⚠️ Note: SM4 is not usable due to 5G NR synchronization signal periodicity.

📶 Traffic & Buffer Model
Each SBS manages data for users as data blocks in a buffer:

Packet size: λ = T × Rmin

Data blocks have Time-To-Live (TTL) to reflect QoS urgency.

Buffer management ensures expired or served packets are removed.


🧪 Training Process
Each SBS acts as an independent learning agent:

Initialize Q-table

For each episode:

Observe current state

Choose action via ε-greedy policy

Execute action, observe reward and next state

Update Q-value

After training, a lookup table is used for decision making in real-time.


📚 References
[27] B. Debaillie, C. Desset, and F. Louagie, “A flexible and future-proof power model for
cellular base stations”, in 2015 IEEE 81st Vehicular Technology Conference (VTC
Spring), 2015, pp. 1–7. doi: 10.1109/VTCSpring.2015.7145603.




