# 🚀 AXI4 Verification IP (VIP) using UVM

> **A comprehensive SystemVerilog UVM-based Verification IP for AXI4 Protocol**

<div align="center">

![AXI4](https://img.shields.io/badge/Protocol-AXI4-blue?style=flat-square)
![UVM](https://img.shields.io/badge/Framework-UVM-green?style=flat-square)
![SystemVerilog](https://img.shields.io/badge/Language-SystemVerilog-orange?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-success?style=flat-square)

[Features](#-features) • [Architecture](#-architecture) • [Getting Started](#-getting-started) • [Tests](#-test-scenarios) • [Contributing](#-contributing)

</div>

---

## 📋 Overview

This project implements a **complete UVM-based Verification IP for the AXI4 protocol**, enabling comprehensive functional verification of AXI4 master and slave devices. The VIP is designed with modularity, reusability, and scalability in mind.

**Key Characteristics:**
- ✅ Full AXI4 protocol compliance
- ✅ Parameterized master and slave agents
- ✅ Functional coverage collection
- ✅ SystemVerilog Assertions (SVA) integration
- ✅ Golden memory model with scoreboard
- ✅ Comprehensive test suite
- ✅ Automated regression capabilities

---

## 🎯 Features

### Master Agent
- 🔧 **Complete AXI4 Master Implementation**
  - Write Address, Write Data, Write Response channels
  - Read Address, Read Data channels
  - Configurable burst types (FIXED, INCR, WRAP)
  - Address alignment and randomization

### Slave Agent
- 🎛️ **Functional Slave Model**
  - Byte-addressable memory implementation
  - Automatic response generation
  - Configurable latency and behavior
  - Memory read/write tracking

### Verification Components
- 📊 **Scoreboard** - Golden memory comparison and data integrity checking
- 📈 **Functional Coverage** - Comprehensive coverage collection for AXI4 transactions
- 🔍 **Monitors** - Non-intrusive transaction monitoring for both master and slave
- 🛡️ **Assertions** - Protocol compliance verification

### Test Infrastructure
- 🧪 **Multiple Test Scenarios**
  - INCR Burst Tests
  - RAW Hazard Detection
  - Burst Type Variations
- 🎲 **Randomization** - Constrained random generation
- 📜 **Virtual Sequencer** - Multi-agent coordination

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────┐
│              TESTBENCH (axi_top.sv)             │
│                                                  │
│  ┌──────────────────────────────────────────┐  │
│  │        ENVIRONMENT (env.sv)              │  │
│  │                                          │  │
│  │  ┌─────────────┐      ┌─────────────┐  │  │
│  │  │  Master UVC │      │  Slave UVC  │  │  │
│  │  ├─────────────┤      ├─────────────┤  │  │
│  │  │   Master    │      │    Slave    │  │  │
│  │  │   Agent     │      │    Agent    │  │  │
│  │  │             │      │             │  │  │
│  │  │ ┌─────────┐ │      │ ┌─────────┐ │  │  │
│  │  │ │ Driver  │ │      │ │ Driver  │ │  │  │
│  │  │ │ Monitor │ │      │ │ Monitor │ │  │  │
│  │  │ │ Seqr    │ │      │ │ Seqr    │ │  │  │
│  │  │ └─────────┘ │      │ └─────────┘ │  │  │
│  │  └─────────────┘      └─────────────┘  │  │
│  │                                          │  │
│  │  ┌──────────────────────────────────┐  │  │
│  │  │      Scoreboard                  │  │  │
│  │  │  (Golden Memory Comparison)      │  │  │
│  │  └──────────────────────────────────┘  │  │
│  │                                          │  │
│  │  ┌──────────────────────────────────┐  │  │
│  │  │   Functional Coverage Collector  │  │  │
│  │  │         (Subscribers)            │  │  │
│  │  └──────────────────────────────────┘  │  │
│  │                                          │  │
│  └──────────────────────────────────────────┘  │
│                                                  │
│  ┌──────────────────────────────────────────┐  │
│  │      AXI4 Interface (axi_if.sv)         │  │
│  │                                          │  │
│  │  - Write Address/Data/Response Channels │  │
│  │  - Read Address/Data Channels           │  │
│  │  - Clocking Blocks for Master/Slave    │  │
│  └──────────────────────────────────────────┘  │
│                                                  │
└─────────────────────────────────────────────────┘
```

---

## 📁 Project Structure

```
Development-of-AXI4-Verification-IP-VIP-using-UVM/
│
├── axi_defs.sv                 # AXI4 Protocol Definitions & Parameters
├── axi_pkg.sv                  # UVM Package Includes
├── Makefile                    # Build & Simulation Automation
│
├── interface/
│   └── axi_if.sv              # AXI4 Interface with Clocking Blocks
│
├── agent/
│   ├── axi_txn.sv             # Transaction Definition
│   ├── subscriber.sv           # Functional Coverage Collection
│   ├── m_uvc.sv               # Master UVC Container
│   ├── s_uvc.sv               # Slave UVC Container
│   │
│   ├── master_agent/
│   │   ├── m_config.sv        # Master Configuration Object
│   │   ├── m_driver.sv        # Master Driver Implementation
│   │   ├── m_monitor.sv       # Master Monitor
│   │   ├── m_seqr.sv          # Master Sequencer
│   │   ├── master_agent.sv    # Master Agent Container
│   │   └── master_seq.sv      # Master Test Sequences
│   │
│   └── slave_agent/
│       ├── s_config.sv        # Slave Configuration Object
│       ├── s_driver.sv        # Slave Driver (Memory Model)
│       ├── s_monitor.sv       # Slave Monitor
│       ├── s_seqr.sv          # Slave Sequencer
│       └── slave_agent.sv     # Slave Agent Container
│
├── env/
│   ├── axi_top.sv             # Top-level Testbench Module
│   ├── env_config.sv          # Environment Configuration
│   ├── env.sv                 # Environment Container
│   └── scoreboard.sv          # Golden Memory & Comparison Logic
│
├── assertions/
│   ├── axi_assertions.sv      # SVA Protocol Assertions
│   └── axi_assertions_bind.sv # Assertion Binding
│
├── v_seqr/
│   ├── v_seqr.sv             # Virtual Sequencer
│   └── v_seq.sv              # Virtual Sequences
│
├── tests/
│   └── axi_test.sv           # Test Scenarios & Testcases
│
└── README.md                 # This File
```

---

## 🔧 Prerequisites

### Software Requirements
- **Simulator**: QuestaSim 2021.1 or later
- **SystemVerilog**: IEEE 1800-2012 or later
- **UVM**: UVM 1.2 or UVM IEEE 1800.2

### Installation Steps

```bash
# Clone the repository
git clone <repository-url>
cd Development-of-AXI4-Verification-IP-VIP-using-UVM-main

# Verify directory structure
ls -la
```

---

## 🚀 Getting Started

### Quick Start

#### 1. **Compile the Design**
```bash
make comp
```

#### 2. **Run Default Test**
```bash
make run TEST=incr_burst_test
```

#### 3. **Run All Tests (Regression)**
```bash
make regress
```

#### 4. **View Coverage**
```bash
make cov
```

### Available Makefile Targets

| Command | Description |
|---------|-------------|
| `make comp` | Compile all SystemVerilog files |
| `make run TEST=<test_name>` | Run specific test |
| `make regress` | Run all tests in regression |
| `make cov` | Generate coverage report |
| `make all` | Compile, run regression, and coverage |
| `make clean` | Clean work directory and logs |
| `make help` | Display help message |

---

## 🧪 Test Scenarios

### 1. **INCR Burst Test** (`incr_burst_test`)
Tests incrementing burst transactions with:
- Sequential address increments
- Configurable burst lengths
- Mixed read/write operations
- Data integrity verification

**Run:**
```bash
make run TEST=incr_burst_test SEED=12345
```

### 2. **RAW Hazard Test** (`raw_hazard_test`)
Detects Read-After-Write hazards:
- Write followed by immediate read to same address
- Data consistency validation
- Memory update tracking
- Response timing verification

**Run:**
```bash
make run TEST=raw_hazard_test
```

### 3. **Burst Variation Test** (`burst_variation_test`)
Comprehensive burst type coverage:
- FIXED burst mode (same address)
- INCR burst mode (incrementing address)
- WRAP burst mode (wrap-around addressing)
- Cross-burst transfers

**Run:**
```bash
make run TEST=burst_variation_test
```

---

## 📊 Key Components

### Transaction (axi_txn.sv)
- Captures complete AXI4 read/write transactions
- Supports burst transactions with multiple beats
- Address, ID, burst type, size, and response tracking
- Constraint-based randomization

### Master Driver
- Drives AXI4 protocol signals on master side
- Handles address and data phase coordination
- Response monitoring and completion
- Supports all three burst types

### Slave Driver
- Implements byte-addressable memory model
- Automatic read/write response generation
- Configurable response latency
- Error injection capabilities

### Scoreboard
- Golden memory model for data verification
- Tracks write transactions and memory updates
- Validates read data against golden model
- Error reporting and statistics

### Functional Coverage
- Address range coverage
- Burst type and length distribution
- WSTRB (write strobes) patterns
- Cross-coverage for burst parameters

---

## 🎓 Usage Examples

### Running Tests with Different Seeds
```bash
make run TEST=incr_burst_test SEED=42
make run TEST=incr_burst_test SEED=100
make run TEST=incr_burst_test SEED=random
```

### Changing Verbosity Levels
```bash
make run TEST=incr_burst_test VERBOSITY=UVM_HIGH
make run TEST=incr_burst_test VERBOSITY=UVM_MEDIUM
make run TEST=incr_burst_test VERBOSITY=UVM_LOW
```

### Running Multiple Tests
```bash
make regress
```

---

## 📈 Functional Coverage

The VIP collects comprehensive coverage for:

✅ **Write Transactions**
- Address ranges and alignment
- Burst lengths (single, power-of-2, large)
- Data widths and strobes
- Burst type combinations

✅ **Read Transactions**
- Address ranges and patterns
- Burst lengths and sizes
- Data response verification

✅ **Cross-Coverage**
- Burst type × Length combinations
- Size × Length interactions
- Address alignment × Burst type

---

## 🛡️ Assertions

The VIP includes protocol assertions to verify:
- Valid signal timing
- Ready signal protocol compliance
- Last signal correctness in bursts
- ID matching in responses
- Response type validity
- Address alignment rules

---

## 📝 Customization

### Modifying Parameters
Edit `axi_defs.sv`:
```systemverilog
parameter int ADDR_WIDTH = 32;    // Address bus width
parameter int DATA_WIDTH = 32;    // Data bus width
parameter int ID_WIDTH   = 4;     // Transaction ID width
parameter int LEN_WIDTH  = 8;     // Burst length width
```

### Adding Custom Sequences
Create new sequence classes in `tests/` or modify `master_seq.sv`:
```systemverilog
class custom_seq extends master_base_seq;
    `uvm_object_utils(custom_seq)
    
    // Your custom sequence logic
endclass
```

### Enabling/Disabling Components
Edit `env_config.sv`:
```systemverilog
env_cfg.has_scoreboard = 1;           // Enable scoreboard
env_cfg.has_virtual_sequencer = 1;    // Enable virtual sequencer
```

---

## 🐛 Debugging Tips

### View Detailed Logs
```bash
make run TEST=incr_burst_test VERBOSITY=UVM_HIGH
```

### Check Waveform Dump
Waveforms are saved to `dump.wdb` (QuestaSim format)
```bash
# Open in QuestaSim
vsim -view dump.wdb
```

### Review Compilation Logs
```bash
cat comp.log
```

### Check Simulation Output
```bash
cat work/transcript
```

---

## 📊 Generated Reports

After running tests, the following are generated:

- `work/transcript` - Simulation transcript
- `dump.wdb` - Waveform database
- `cov/` - Coverage database and reports
- `comp.log` - Compilation log
- `sim.log` - Simulation log

---

## ✨ Highlights

🏆 **Production-Ready VIP**
- Fully compliant with AXI4 protocol specification
- Extensive protocol coverage
- Ready for integration into complex SoCs

🔄 **Reusable Components**
- Modular agent architecture
- Configuration-driven behavior
- Easy to extend and customize

📊 **Comprehensive Verification**
- Golden memory model
- Functional coverage metrics
- Protocol assertions
- Multi-scenario testing

⚡ **High Performance**
- Efficient transaction handling
- Minimal simulation overhead
- Scalable to multi-agent scenarios

---

## 📚 References

- [AMBA AXI4 Protocol Specification](https://developer.arm.com/)
- [UVM User Guide](https://accellera.org/)
- [SystemVerilog LRM](http://standards.ieee.org/)
- [QuestaSim Documentation](https://www.mentor.com/)

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Guidelines
- Follow existing code style and naming conventions
- Add comments for complex logic
- Update README for new features
- Test thoroughly before submitting PR

---

## 📄 License

This project is provided as-is for educational and research purposes.

---

## 👤 Author

**Keshvi Agarwal**
- 🔗 GitHub: [@Keshviagg12](https://github.com/Keshviagg12)
- 📧 Contact: [GitHub Profile](https://github.com/Keshviagg12)

---

## 🙏 Acknowledgments

This VIP was developed as a comprehensive solution for AXI4 protocol verification using industry-standard UVM methodology. Special thanks to the UVM and SystemVerilog communities for providing excellent frameworks and resources.

---

## 📞 Support & Questions

For issues, questions, or suggestions:
1. 📝 Open an **Issue** on GitHub
2. 📧 Contact the author directly
3. 💬 Discuss in project discussions

---

<div align="center">

---

*Last Updated: April 28, 2026*

</div>
