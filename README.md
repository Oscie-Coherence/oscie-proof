\documentclass[12pt]{article}

\usepackage{geometry}
\geometry{margin=1in}
\usepackage{hyperref}
\usepackage{setspace}
\usepackage{listings}
\usepackage{xcolor}

\definecolor{codegray}{gray}{0.95}

\lstset{
  backgroundcolor=\color{codegray},
  basicstyle=\ttfamily\small,
  breaklines=true
}

\title{\textbf{Oscie-Proof}\\
\large Operational Coherence Governor for LLM Stability}
\date{}

\begin{document}

\maketitle
\onehalfspacing

\section*{Overview}

\textbf{Oscie-Proof} is a lightweight, open-source \emph{Operational Coherence Governor} for large language models.  
It provides a physics-inspired stability layer that reduces drift, increases long-context reliability, and improves jailbreak resistance without modifying the underlying LLM.

The architecture is intentionally compact:
\begin{itemize}
    \item one coherence scanner (\texttt{oscie.py})
    \item one evaluation suite (\texttt{OSCIE\_BENCHMARK\_SUITE.py})
    \item optional adapters for external LLM APIs
\end{itemize}

Oscie-Proof is designed for:
\begin{itemize}
    \item reproducible safety testing  
    \item long-run coherence verification  
    \item research into synchronization-based governance  
    \item multi-model orchestration experiments  
\end{itemize}

This repository is fully public, auditable, and does not contain private models or proprietary datasets.

\section*{Key Concepts}

Oscie-Proof operationalizes a small set of stability principles inspired by dynamical systems and oscillator networks:

\begin{itemize}
    \item \textbf{Coherence Phase Lifetime (CPL)}:  
    Maximum number of inference steps before semantic drift increases.

    \item \textbf{Coupling Vector (CV)}:  
    Strength of the governor's influence over downstream reasoning chains.

    \item \textbf{Noise Floor $\Gamma_{\text{noise}}$}:  
    Aggregate uncertainty from model sampling, user input, and context history.

    \item \textbf{Operational Coherence Condition}:  
    \[
        \mathrm{CPL} \times \mathrm{CV} > \Gamma_{\text{noise}}
    \]
    When satisfied, long-context drift remains bounded.
\end{itemize}

These metrics are non-proprietary and generic; they do not depend on a specific architecture or vendor.

\section*{Repository Structure}

\begin{lstlisting}
oscie-proof/
├── oscie.py                    # Primary coherence-governor module
├── OSCIE_BENCHMARK_SUITE.py    # Drift, jailbreak, and stability tests
├── examples/                   # Optional usage demos
└── README.tex                  # This document (LaTeX version)
\end{lstlisting}

\section*{Installation}

\begin{lstlisting}
git clone https://github.com/Oscie-Coherence/oscie-proof.git
cd oscie-proof
pip install -r requirements.txt
\end{lstlisting}

You will need API keys for any external LLMs you want to benchmark.  
Place them in a local \texttt{.env} file:

\begin{lstlisting}
PRIMARY_KEY = "your-key-here"
SCANNER_KEY = "your-key-here"
\end{lstlisting}

\section*{Usage}

\subsection*{Run the Governor}

\begin{lstlisting}
python oscie.py
\end{lstlisting}

By default, the governor evaluates each user message with a lightweight coherence scan before forwarding it to the selected LLM backend.  
If a message exceeds the threshold, it is restructured or declined according to policy rules.

\subsection*{Run Benchmark Tests}

\begin{lstlisting}
python OSCIE_BENCHMARK_SUITE.py
\end{lstlisting}

The suite includes:
\begin{itemize}
    \item long-session drift tests
    \item semantic stability tests
    \item adversarial jailbreak attempts
    \item input-governor correctness tests
\end{itemize}

All tests are reproducible and do not rely on any proprietary models.

\section*{Example Minimal Script}

\begin{lstlisting}
from oscie import OscieGovernor

osc = OscieGovernor()

user_input = "Explain gravitational lensing."
response = osc.run(user_input)

print(response)
\end{lstlisting}

\section*{Research Motivation}

Oscie-Proof explores the idea that LLM stability can be improved using:
\begin{itemize}
    \item coupling-based moderation  
    \item phase-locking analogues  
    \item noise-floor estimation  
    \item lightweight coherence-energy functions  
\end{itemize}

This is not a philosophical claim.  
It is an engineering hypothesis:
\begin{quote}
A small governor can meaningfully improve reliability of large language models without modifying model weights.
\end{quote}

\section*{Safety}

Oscie-Proof is:
\begin{itemize}
    \item non-diagnostic  
    \item non-medical  
    \item vendor-neutral  
    \item privacy-preserving  
    \item free from surveillance code  
\end{itemize}

It includes no model training, no user data collection, and no hidden logging.  
All coherence scans occur locally at runtime.

\section*{License}

Apache 2.0.  
Free for research, modification, and commercial use under the terms of the license.

\section*{Contributing}

Pull requests are welcome.  
Test coverage, evaluation expansions, and new LLM adapter modules are especially valuable.

\section*{Contact}

Project repository:
\begin{quote}
\url{https://github.com/Oscie-Coherence/oscie-proof}
\end{quote}

\end{document}
