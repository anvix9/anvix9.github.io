-
layout: page
title: Portfolio
permalink: /portfolio/
---

# Portfolio

A selection of research, tools, and teaching work in NLP, deep learning, and knowledge retrieval.

______

## Research Projects

### Question-Knowledge Compression RAG
**Enhancing Multihop Document Retrieval without Fine-tuning**

A pipeline that compresses scientific papers into lightweight "paper-cards" (~5 KB each) using generated questions and queries. Replaces 44,809 chunk embeddings with just 109 vectors — an ~80% storage reduction — while outperforming BM25 and fine-tuned baselines on both single-hop and multi-hop retrieval.

The system introduces a syntactic reranking method that decomposes queries at POS boundaries and reranks passages by document frequency, all without any model fine-tuning.

| Metric | Our Approach | Best Baseline |
|--------|-------------|---------------|
| Accuracy (Single-hop) | **0.844** | 0.789 (BM25) |
| MRR (Single-hop) | **0.803** | 0.677 (BM25) |
| F1 (Multi-hop, Llama3) | **0.550** | 0.412 (CFIC-7B) |
| Embedding Records | **109** | 44,809 (Fixed-size) |

**Pipeline:** Paper Input (2–70 MB) → Section Extraction → Question Generation → Paper-Card (~5 KB) → Syntactic Reranking → Result

**Links:** [GitHub](https://github.com/anvix9/question-knowledge-compression-rag) · [Paper (Preprint)](https://doi.org/10.20944/preprints202601.1757.v2)

______

### Haut
**Research Search Engine for Literature Reviews**

A platform for building literature reviews on NLP and deep learning. Finds relevant articles based on specific methodology or research questions and suggests potential future directions.

Introduces a semantic chunking system based on *question anchors* with a FlashRank reranking method. The final method compresses the initial text from 2–70 MB to ~1 KB per file in the vector database, with relevant response quality compared to traditional methods.

**Links:** [GitHub](https://github.com/anvix9/haut)

______

### Sherlock-lit
**Python Package for Research Paper Analysis**

A Python package (available on PyPI) that leverages NLP and LLMs to quickly find the contributions and research questions of a paper, outputting precise markdown cards. Part of the Haut platform ecosystem.

```
$ pip install sherlock-lit
$ sherlock_lit paper.pdf
# → Generates a markdown card in card-papers/
```

Designed for CPU efficiency (< 70 MB), with optional GPU acceleration.

**Links:** [GitHub](https://github.com/anvix9/sherlock-lit) · [PyPI](https://pypi.org/project/sherlock-lit/)

______

## Other Projects

### Convolution in C++
From-scratch implementation of 2D convolution using C++ template metaprogramming. An educational deep-dive into the operations underlying CNNs.

**Links:** [GitHub](https://github.com/anvix9/convolution) · [Blog Post](https://anvix9.github.io/2024/08/08/Experiment-1-2D-Convolution-in-C++-from-scratch-with-intuition)

### AWS Token Refresh Automation
Guide and Python script for refreshing AWS SSO tokens automatically, solving the common pain of expired tokens in CI/CD workflows.

**Links:** [GitHub](https://github.com/anvix9/AWS-Token-Refresh-Automation-Guide-in-terminal-)

______

## Publications

1. **Eponon, A.A.**, Shahiki-Tash, M., Batyrshin, I., Maldonado-Sifuentes, C.E., Sidorov, G. and Gelbukh, A., 2025. *Knowledge and Context Compression via Question Generation: Enhancing Multihop Document Retrieval without Fine-tuning.* Preprint. [DOI](https://doi.org/10.20944/preprints202601.1757.v2)

2. Alex Eponon and Luis Ramos Perez, 2024. *Pinealai at SemEval-2024 Task 1: Exploring Semantic Relatedness Prediction using Syntactic, TF-IDF, and Distance-Based Features.* SemEval-NAACL, Mexico City.

3. **Eponon, A.A.**, Batyrshin, I. and Sidorov, G., 2024. *Pinealai stressident LT-EDI@EACL2024: Minimal Configurations for Stress Identification in Tamil and Telugu.* EACL, Malta.

4. Alex-Eponon, A., Tayyab-Zamir, M., Kawo-Eyob, L., Ramos-Perez, L.I., et al., 2024. *From Simple Detection to Quality-aware Prediction: Exploring Argument Complexity with Machine Learning.* MICAI, Mexico.

5. **Eponon, A.A.** and Dimililer, K., 2022. *A Bert Model with Deep Learning Approach in Natural Language Processing.* 12th WCIS, Tashkent. Springer Nature Switzerland.

______

## Teaching & Talks

### Professor — M.Sc. in Artificial Intelligence
**Universidad Mayor de San Andrés (UMSA)**, La Paz, Bolivia — *Feb 2025 – Present*

Modules: Business & Ecosystem Analysis, Data Acquisition & ETL, NLP & RAG Systems, Model Optimization (NeMo Curator, fine-tuning, distillation, pruning, quantization).

### Master's Workshop — NVIDIA NeMo Curator Pipeline
**UMSA**, La Paz, Bolivia — *Dec 2–3, 2025*

### Invited Speaker — AI in Social Sciences
**UNAM Conference**, Mexico City — *Nov 25, 2025*

Topic: Intersection between Social Sciences and Artificial Intelligence.

### Invited Speaker — Role of Semantics in AI
**EVCCCPLN** — *Jul 2024*

______

## Education

- **Ph.D. in Natural Language Processing** — Instituto Politécnico Nacional (CIC), Mexico City — *2023 – Present*
- **M.Sc. in Software Engineering** (GPA 3.8/4.0) — Near East University, Cyprus — *2020 – 2023*
- **B.Sc. in Computer Science** (GPA 7.2/10) — Valoris International University — *2016 – 2020*

______

## Technical Skills

**Languages:** Python, C++, JavaScript, Bash, SQL, HTML/CSS

**ML / NLP:** PyTorch, Hugging Face, Spacy, NVIDIA NeMo Curator, LLM fine-tuning & distillation, RAG, pruning & quantization

**Data & Vector:** Pinecone, FAISS, Pandas, NumPy, PostgreSQL, MySQL, web scraping, ETL/ELT

**DevOps & Tools:** Git/GitHub, Docker, FastAPI, Selenium, Linux/Ubuntu, VIM

**Languages spoken:** French (native), English (C2), Spanish (C1)

______

*For questions or collaboration, reach out at [
