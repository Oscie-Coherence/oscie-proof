# **Oscie-Proof**
### *Operational Coherence Governor for LLM Stability*

Oscie-Proof is a lightweight, open-source **Operational Coherence Governor** for large language models.  
It applies physics-inspired stability principles that reduce drift, increase long-context reliability, and improve jailbreak resistance — without modifying any model weights.

The architecture is intentionally compact:

- `oscie.py` — coherence scanner + governor  
- `OSCIE_BENCHMARK_SUITE.py` — drift, jailbreak, and coherence tests  
- Optional adapters for external LLM APIs  

Oscie-Proof is built for:

- reproducible safety testing  
- long-run coherence verification  
- synchronization-based governance research  
- multi-model orchestration experiments  

This repository is fully public, auditable, and contains no proprietary models.

---

## **Key Concepts**

Oscie-Proof uses lightweight dynamical-systems–inspired metrics:

### **Coherence Phase Lifetime (CPL)**  
Maximum number of inference steps before semantic drift begins to accelerate.

### **Coupling Vector (CV)**  
How strongly the governor influences downstream reasoning stability.

### **Noise Floor (Γ_noise)**  
Uncertainty from sampling variance, user input, and context history.

### **Operational Coherence Condition**

CPL × CV > Γ_noise

If this inequality holds, long-context drift remains bounded and controllable.

These metrics are model-agnostic and vendor-neutral.

---

## **Repository Structure**

oscie-proof/
├── oscie.py # Primary coherence-governor module
├── OSCIE_BENCHMARK_SUITE.py # Drift, jailbreak, and stability tests
├── examples/ # Optional usage demos
└── README.md # Documentation

---

## **Installation**

```bash
git clone https://github.com/Oscie-Coherence/oscie-proof.git
cd oscie-proof
pip install -r requirements.txt
If you want to call external APIs, create a .env file:
PRIMARY_KEY="your-key-here"
SCANNER_KEY="your-key-here"
Usage
Run the Governor
python oscie.py
The governor performs a coherence scan on each incoming message before forwarding it to the LLM.
Messages that violate coherence thresholds are blocked or restructured.
Run Benchmark Tests
python OSCIE_BENCHMARK_SUITE.py
The benchmark suite includes:
long-session drift tests
semantic stability tests
adversarial jailbreak attempts
input-governor correctness tests
All tests are reproducible and portable.
Minimal Example
from oscie import OscieGovernor

osc = OscieGovernor()

user_input = "Explain gravitational lensing."
response = osc.run(user_input)

print(response)
Research Motivation
Oscie-Proof explores the possibility that LLM stability can be improved via:
weak coupling
phase-locking analogues
noise-floor estimation
coherence-energy heuristics
It is not philosophy — it is a testable engineering hypothesis:
A small governor can meaningfully improve reliability of large language models without modifying internal weights.
Safety
Oscie-Proof is:
non-diagnostic
non-medical
vendor-neutral
privacy-preserving
telemetry-free
It performs no training, collects no user data, and logs nothing by default.
All scans are local and ephemeral.
License
Apache 2.0
Free for research, modification, and commercial use under standard open-source terms.
Contributing
Pull requests are welcome.
High-value contributions include:
additional drift tests
new coupling heuristics
backend adapters
expanded evaluation datasets
Project Repository
https://github.com/Oscie-Coherence/oscie-proof
