# 🚀 AXI4 Verification IP (VIP) using UVM

> **A Production-Ready UVM-Based Verification IP for AXI4 Protocol**

<div align="center">

![AXI4](https://img.shields.io/badge/Protocol-AXI4-blue?style=for-the-badge)
![UVM](https://img.shields.io/badge/Framework-UVM-green?style=for-the-badge)
![SystemVerilog](https://img.shields.io/badge/Language-SystemVerilog-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)

<br>

**High-performance AXI4 Verification Environment built using UVM**

<br>

[✨ Features](#-features) • [🏗 Architecture](#-architecture) • [📊 Results](#-simulation-results) • [🚀 Quick Start](#-quick-start) • [👩‍💻 Author](#-author)

</div>

---

## 📋 Overview

This project implements a **complete UVM-based Verification IP (VIP)** for the **AXI4 protocol**, designed to verify high-performance SoC interconnects.

It supports:
- Multiple outstanding transactions  
- Out-of-order responses  
- Burst-based transfers  

---

## ✨ Features

| Feature | Description |
|--------|------------|
| 🔄 AXI Channels | Full support for all 5 AXI4 channels |
| ⚡ Performance | Handles multiple outstanding transactions |
| 🔀 Advanced | Supports out-of-order completion |
| 🧪 UVM Testbench | Fully modular UVM environment |
| 📊 Coverage | Functional coverage + assertions |
| 🧠 Scoreboard | Golden memory-based checking |

---

## 🏗 Architecture

### 🔷 AXI4 Channel Flow

<p align="center">
  <img src="axi4_architecture.png.png" width="800">
</p>

---

### 🔷 UVM Environment Hierarchy

```text
TESTBENCH (axi_top.sv)
│
├── ENVIRONMENT (env.sv)
│   ├── Master UVC
│   │   └── Master Agent
│   ├── Slave UVC
│   │   └── Slave Agent
│   ├── Scoreboard
│   └── Coverage Collector
📊 Simulation Results
🔹 Read Channel Verification
<p align="center"> <img src="read_channel_waveform.png.png" width="900"> </p>
🔹 Outstanding & Out-of-Order Transactions
<p align="center"> <img src="outstanding_and_ooo_waveforms.png.png" width="900"> </p>
🧪 Verification Components
🔧 Agents
Master Agent
Burst types: FIXED, INCR, WRAP
Address randomization
Slave Agent
Memory model
Configurable latency
📊 Metrics
✔️ Scoreboard
✔️ Functional Coverage
✔️ Assertions (SVA)
🚀 Quick Start
Step	Command	Description
⚙️ Compile	make comp	Compile full environment
🧪 Run Test	make run TEST=incr_burst_test SEED=12345	Run test
📊 Coverage	make cov	Generate report
📸 Sample Output
TEST PASSED ✅
Coverage: 98.7%
Assertions: All Passed

📂 Project Structure
axi_vip/
├── tb/
├── env/
├── agent/
├── sequences/
├── tests/
├── coverage/
└── Makefile

⚙️ Prerequisites
Simulator: QuestaSim 2021.1+
Methodology: UVM 1.2 / IEEE 1800.2
👩‍💻 Author
<div align="center">
Keshvi Agarwal

🎓 B.Tech (ECE)
🔬 VLSI | Functional Verification | UVM

GitHub Profile

📫 Open for VLSI Opportunities

</div>
🌟 Support

If you like this project:

⭐ Star the repo
🍴 Fork it
🚀 Contribute

