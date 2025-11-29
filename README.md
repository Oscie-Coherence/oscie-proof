# **Oscie-Proof**
### *Operational Coherence Governor for LLM Stability*

Oscie-Proof is a lightweight, open-source **Operational Coherence Governor** that wraps around any large-language model to stabilize long-context reasoning, reduce semantic drift, and improve jailbreak resistance — all **without modifying model weights**.

The system is intentionally compact:

- `oscie.py` — coherence scanner + governor  
- `OSCIE_BENCHMARK_SUITE.py` — drift + jailbreak evaluation  
- Optional adapters for external LLM APIs  

The goal: **third-party-verifiable coherence**, not theory.

---

## **Why Oscie-Proof Exists**
Modern LLMs are powerful, but they’re noisy dynamical systems.  
As context windows grow, drift grows. As prompts get complex, jailbreaks increase.

Oscie-Proof tests a simple engineering hypothesis:

> **A small, physics-inspired coherence governor can stabilize LLM behavior without retraining.**

It uses oscillator-style metrics to keep the reasoning chain phase-aligned:

- **CPL** — Coherence Phase Lifetime  
- **CV** — Coupling Vector  
- **Γ_noise** — Noise Floor  

Operational stability condition:

CPL × CV > Γ_noise

If this holds, drift remains bounded.

---

## **Repository Structure**

oscie-proof/
├── oscie.py # Primary coherence governor
├── OSCIE_BENCHMARK_SUITE.py # Drift, jailbreak, and coherence tests
├── examples/ # Minimal usage demos
└── README.md # (This file)

---

## **Installation**

```bash
git clone https://github.com/Oscie-Coherence/oscie-proof.git
cd oscie-proof
pip install -r requirements.txt
Create a .env file if you want to benchmark external LLMs:
PRIMARY_KEY="your-key-here"
SCANNER_KEY="your-key-here"
Usage
Run the Governor
python oscie.py
The governor scans user inputs with a lightweight coherence evaluator before forwarding them to the LLM.
If coherence drops below threshold, the governor restructures or blocks the request.
Run Benchmarks
python OSCIE_BENCHMARK_SUITE.py
Benchmark suite includes:
Long-session drift tests
Semantic stability tests
Adversarial jailbreak tests
Input-governor correctness tests
All tests are vendor-neutral and reproducible.
Minimal Example
from oscie import OscieGovernor

osc = OscieGovernor()

user_input = "Explain gravitational lensing."
response = osc.run(user_input)

print(response)
Research Motivation
Oscie-Proof experiments with using dynamical-systems concepts to stabilize LLMs:
Weak coupling
Phase-locking analogues
Noise-floor estimation
Lightweight coherence-energy heuristics
Not philosophy — engineering validation.
Safety
Oscie-Proof is:
non-diagnostic
non-medical
vendor-neutral
privacy-preserving
telemetry-free
No training.
No collection of user data.
No hidden logging.
Coherence scans are local and ephemeral.

License
Apache 2.0
Free for research, commercial use, modification, and extension under the license.
Contributing
PRs welcome — especially around:
test coverage
drift metrics
additional LLM backends
benchmarking improvements
