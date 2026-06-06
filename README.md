# ⚛️ Formula-Aware Chunking for RAG in Physics Documents

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![LangChain](https://img.shields.io/badge/LangChain-Enabled-green.svg)
![ChromaDB](https://img.shields.io/badge/ChromaDB-Vector_Store-orange.svg)
![Groq](https://img.shields.io/badge/Groq-Llama_3.1-black.svg)

**Mitigating Mathematical Context Degradation in Physics Documents Using Formula-Aware Chunking in Retrieval-Augmented Generation (RAG) Architectures.**

This repository contains the source code, and evaluation datasets for an undergraduate research project conducted at the **School of Computer Science, Bina Nusantara (BINUS) University**.

## 📖 Project Overview
Retrieval-Augmented Generation (RAG) is a powerful architecture that grounds Large Language Models (LLMs) with external knowledge. However, applying RAG to STEM (Science, Technology, Engineering, and Mathematics) literature presents a unique challenge: **standard recursive text chunking arbitrarily breaks mathematical formulas and separates them from their explanatory context.** 

This project proposes a **Hybrid Formula-Aware Chunking** mechanism. By utilizing Regex-based boundary detection and a dynamic 1,200-character safety net, this architecture prevents formula fragmentation and resolves LLM context overflow (the "Context Blow-Up" challenge).

## 📊 Key Results
We evaluated the system using the OpenStax University Physics dataset and 50 college-level physics questions from the MMLU Benchmark. The evaluation metric used was Exact Match (EM) Accuracy.

| Experiment Scale | Baseline (Recursive Chunking) | Proposed (Formula-Aware Chunking) | Performance Gain |
| :--- | :--- | :--- | :--- |
| **Small Scale** (Pure Mechanics) | 14.29% | **42.86%** | **+ 28.57%** |
| **Massive Scale** (50 Physics Qs) | 36.00% | **46.00%** | **+ 10.00%** |

*Conclusion:* Preserving the structural integrity of physics formulas alongside their textual definitions significantly enhances LLM reasoning and retrieval precision.

## 🗂️ Repository Structure
```text
formula-aware-rag/
├── data/
│   ├── benchmark/              # MMLU dataset and evaluation CSV outputs
│   └── raw_pdfs/               # (Excluded in git) Place OpenStax PDFs here
│   └── chroma_baseline_large/  # Chroma DB for baseline large scale experiment
│   └── chroma_formula_large/   # Chroma DB for formula aware large scale experiment
├── notebooks/                  # Jupyter Notebooks for experiments
│   ├── 01_baseline_small.ipynb
│   ├── 02_formula_small.ipynb
│   ├── 03_baseline_large.ipynb
│   ├── 04_formula_large.ipynb
│   └── 05_final_evaluation_metrics.ipynb
├── requirements.txt        # Python dependencies
└── README.md
