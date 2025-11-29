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

\title{\textbf{Oscie-Proof}\\[4pt]
\large Operational Coherence Governor for LLM Stability}

\date{}

\begin{document}

\maketitle
\onehalfspacing

%---------------------------------------------------------
\section*{Overview}
%---------------------------------------------------------

\textbf{Oscie-Proof} is a lightweight, open-source \emph{Operational Coherence Governor} for large language models.  
It provides a physics-inspired stability layer that reduces drift, improves long-context reliability, and increases jailbreak resistance without modifying the underlying LLM.

The architecture is intentionally compact:
\begin{itemize}
    \item a coherence scanner (\texttt{oscie.py})
    \item a full evaluation suite (\texttt{OSCIE\_BENCHMARK\_SUITE.py})
    \item optional adapters for external LLM APIs
\end{itemize}

Oscie-Proof is designed for:
\begin{itemize}
    \item reproducible safety testing
    \item long-run coherence verification
    \item research into synchronization-based governance
    \item multi-model orchestration experiments
\end{itemize}

This repository is fully public, auditable, and contains no private models or proprietary datasets.

%---------------------------------------------------------
\section*{Key Concepts}
%---------------------------------------------------------

Oscie-Proof operationalizes a compact set of stability principles inspired by dynamical systems and oscillator networks:

\begin{itemize}
    \item \textbf{Coherence Phase Lifetime (CPL)}:  
    Maximum number of inference steps before semantic drift increases.

    \item \textbf{Coupling Vector (CV)}:  
    Effective influence of the governor over downstream reasoning chains.

    \item \textbf{Noise Floor $\Gamma_{\text{noise}}$}:  
    Aggregate uncertainty from sampling, user input variability, and historical context.

    \item \textbf{Operational Coherence Condition}:
    \[
        \mathrm{CPL} \times \mathrm{CV} > \Gamma_{\text{noise}}
    \]
    When satisfied, long-context drift remains bounded and predictable.
\end{itemize}

These metrics are generic, architecture-neutral, and vendor-independent.

%---------------------------------------------------------
\section*{Repository Structure}
%---------------------------------------------------------

\begin{lstlisting}
oscie-proof/
├── oscie.py                    # Primary coherence-governor module
├── OSCIE_BENCHMARK_SUITE.py    # Drift, jailbreak, and stability tests
├── examples/                   # Optional usage demos
└── README.tex                  # LaTeX documentation (this file)
\end{lstlisting}

%---------------------------------------------------------
\section*{Installation}
%---------------------------------------------------------

\begin{lstlisting}
git clone https://github.com/Oscie-Coherence/oscie-proof.git
cd oscie-proof
pip install -r requirements.txt
\end{lstlisting}

Provide API keys for any external LLMs via a \texttt{.env} file:

\begin{lstlisting}
PRIMARY_KEY="your-key-here"
SCANNER_KEY="your-key-here"
\end{lstlisting}

%---------------------------------------------------------
\section*{Usage}
%---------------------------------------------------------

\subsection*{Run the Governor}

\begin{lstlisting}
python oscie.py
\end{lstlisting}

The governor evaluates each user message with a lightweight coherence scan before forwarding it to the LLM backend. Messages exceeding threshold are restructured or declined per policy.

\subsection*{Run Benchmark Tests}

\begin{lstlisting}
python OSCIE_BENCHMARK_SUITE.py
\end{lstlisting}

The benchmark suite includes:
\begin{itemize}
    \item long-session drift tests
    \item semantic stability tests
    \item adversarial jailbreak attempts
    \item input-governor correctness tests
\end{itemize}

All tests are reproducible and vendor-neutral.

%---------------------------------------------------------
\section*{Example Minimal Script}
%---------------------------------------------------------

\begin{lstlisting}
from oscie import OscieGovernor

osc = OscieGovernor()

user_input = "Explain gravitational lensing."
response = osc.run(user_input)

print(response)
\end{lstlisting}

%---------------------------------------------------------
\section*{Research Motivation}
%---------------------------------------------------------

Oscie-Proof tests the hypothesis that LLM stability can be improved via:
\begin{itemize}
    \item coupling-based moderation
    \item phase-locking analogues
    \item noise-floor estimation
    \item lightweight coherence-energy functions
\end{itemize}

This is an engineering exploration:

\begin{quote}
A compact governor can meaningfully improve reliability of large language models without altering model weights.
\end{quote}

%---------------------------------------------------------
\section*{Safety}
%---------------------------------------------------------

Oscie-Proof is:
\begin{itemize}
    \item non-diagnostic  
    \item non-medical  
    \item vendor-neutral  
    \item privacy-preserving  
    \item free from surveillance or telemetry  
\end{itemize}

It performs no training, collects no user data, and logs nothing by default.  
All coherence scanning is local and ephemeral.

%---------------------------------------------------------
\section*{License}
%---------------------------------------------------------

Licensed under Apache 2.0.  
Free for research, modification, and commercial deployment under the license terms.

%---------------------------------------------------------
\section*{Contributing}
%---------------------------------------------------------

Pull requests are welcome.  
Contributions to test coverage, drift metrics, and adapter modules are especially appreciated.

%---------------------------------------------------------
\section*{Contact}
%---------------------------------------------------------

Project Repository:  
\url{https://github.com/Oscie-Coherence/oscie-proof}

\end{document}
