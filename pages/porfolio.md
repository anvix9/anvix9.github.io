---
layout: page
title: Portfolio
permalink: /portfolio/
---

# Portfolio

![Wanderer above the Sea of Fog](https://upload.wikimedia.org/wikipedia/commons/b/b9/Caspar_David_Friedrich_-_Wanderer_above_the_sea_of_fog.jpg)
<center>Fig.1: Wanderer above the Sea of Fog — Caspar David Friedrich, 1818.</center>

<br>

There is something interesting about the act of building. Not building for the sake of producing, but building as a way to understand. Every project listed here started from a question I could not answer by reading alone — I had to construct something to see whether my intuition held or collapsed under its own weight.

This page gathers research, tools, teaching, and the traces of that process.

______

## Research Projects

### Question-Knowledge Compression RAG

*Enhancing Multihop Document Retrieval without Fine-tuning*

The central question was simple: why do we need tens of thousands of embedding vectors to represent a hundred papers? The answer turned out to be — we don't.

This pipeline compresses scientific papers into lightweight "paper-cards" (~5 KB each) using generated questions and queries. It replaces 44,809 chunk embeddings with just 109 vectors — roughly 80% storage reduction — while outperforming BM25 and fine-tuned baselines on both single-hop and multi-hop retrieval.

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

*Research Search Engine for Literature Reviews*

![The Alchemist Discovering Phosphorus](https://upload.wikimedia.org/wikipedia/commons/8/80/Joseph_Wright_of_Derby_-_The_Alchymist.jpg)
<center>Fig.2: The Alchemist Discovering Phosphorus — Joseph Wright of Derby, 1771.</center>

<br>

Haut was born from a frustration familiar to any researcher: the time spent searching for what has already been done before you can even begin to think about what hasn't. It is a platform for building literature reviews on NLP and deep learning, designed to find relevant articles based on a specific methodology or research question — and to suggest potential future directions.

It introduces a semantic chunking system based on *question anchors* with a FlashRank reranking method. The compression is drastic: initial texts of 2–70 MB reduce to approximately 1 KB per file in the vector database, with response quality comparable to traditional methods.

**Links:** [GitHub](https://github.com/anvix9/haut)

______

### Sherlock-lit

*Python Package for Research Paper Analysis*

Sherlock-lit is a tool built out of necessity — part of the Haut ecosystem. It leverages NLP and LLMs to quickly extract the contributions and research questions from academic papers, generating concise markdown cards. It is designed to run efficiently on CPUs (under 70 MB), with optional GPU support.

```
$ pip install sherlock-lit
$ sherlock_lit paper.pdf
# → Generates a markdown card in card-papers/
```

**Links:** [GitHub](https://github.com/anvix9/sherlock-lit) · [PyPI](https://pypi.org/project/sherlock-lit/)

______

## Other Projects

**Convolution in C++** — From-scratch implementation of 2D convolution using C++ template metaprogramming. An educational deep-dive into the fundamental operations underlying CNNs. [GitHub](https://github.com/anvix9/convolution) · [Blog Post](https://anvix9.github.io/2024/08/08/Experiment-1-2D-Convolution-in-C++-from-scratch-with-intuition)

**AWS Token Refresh Automation** — Guide and Python script for refreshing AWS SSO tokens automatically, solving the common pain of expired credentials in CI/CD workflows. [GitHub](https://github.com/anvix9/AWS-Token-Refresh-Automation-Guide-in-terminal-)

______

## Publications

![A Philosopher Lecturing on the Orrery](https://upload.wikimedia.org/wikipedia/commons/8/8f/A_Philosopher_Lecturing_on_the_Orrery.jpg)
<center>Fig.3: A Philosopher Lecturing on the Orrery — Joseph Wright of Derby, 1766.</center>

<br>

1. **Eponon, A.A.**, Batyrshin, I., Maldonado-Sifuentes, C.E. and Sidorov, G., 2025. *How Psychological Learning Paradigms Shaped and Constrained Artificial Intelligence.* arXiv. [Paper](https://arxiv.org/abs/2603.18203)

2. **Eponon, A.A.**, Shahiki-Tash, M., Batyrshin, I., Maldonado-Sifuentes, C.E., Sidorov, G. and Gelbukh, A., 2025. *Knowledge and Context Compression via Question Generation: Enhancing Multihop Document Retrieval without Fine-tuning.* Preprint. [DOI](https://doi.org/10.20944/preprints202601.1757.v2)

3. Alex Eponon and Luis Ramos Perez, 2024. *Pinealai at SemEval-2024 Task 1: Exploring Semantic Relatedness Prediction using Syntactic, TF-IDF, and Distance-Based Features.* SemEval-NAACL, Mexico City.

4. **Eponon, A.A.**, Batyrshin, I. and Sidorov, G., 2024. *Pinealai stressident LT-EDI@EACL2024: Minimal Configurations for Stress Identification in Tamil and Telugu.* EACL, Malta.

5. Alex-Eponon, A., Tayyab-Zamir, M., Kawo-Eyob, L., Ramos-Perez, L.I., et al., 2024. *From Simple Detection to Quality-aware Prediction: Exploring Argument Complexity with Machine Learning.* MICAI, Mexico.

6. **Eponon, A.A.** and Dimililer, K., 2022. *A Bert Model with Deep Learning Approach in Natural Language Processing.* 12th WCIS, Tashkent. Springer Nature Switzerland.

______

## Teaching & Talks

![The School of Athens](https://upload.wikimedia.org/wikipedia/commons/4/49/%22The_School_of_Athens%22_by_Raffaello_Sanzio_da_Urbino.jpg)
<center>Fig.4: The School of Athens — Raphael, 1511.</center>

<br>

Teaching, to me, is not about transferring information — it is about transferring the desire to investigate. The courses I design are built around that principle: give students real tools, real problems, and real constraints, and let the curiosity do the rest.

### Professor — M.Sc. in Artificial Intelligence

**Universidad Mayor de San Andrés (UMSA)**, La Paz, Bolivia — *Feb 2025 – Present*

Four modules spanning business strategy and AI ecosystems, ETL pipeline development (Scrapy, Pandas, SQL), NLP fundamentals from Bag of Words to Transformers with practical RAG system building, and advanced model optimization covering NeMo Curator, fine-tuning, distillation, pruning, and quantization.

The classroom operates as a collaborative environment on Hugging Face, where student groups build and deploy their own models — from data curation to API serving.

**Links:** [UMSA Classroom on Hugging Face](https://huggingface.co/umsa-v1) (15 models, 20 datasets, 22 students)

### Master's Workshop — NVIDIA NeMo Curator Pipeline

**UMSA**, La Paz, Bolivia — *Dec 2–3, 2025*

### Invited Speaker — AI in Social Sciences

**UNAM Conference**, Mexico City — *Nov 25, 2025*

Topic: Intersection between Social Sciences and Artificial Intelligence — Exploring the link between social sciences and advanced technology.

### Invited Speaker — Role of Semantics in AI

**EVCCCPLN** — *Jul 2024*

______

## Education

![The Astronomer](https://upload.wikimedia.org/wikipedia/commons/3/3c/Johannes_Vermeer_-_The_Astronomer_-_1668.jpg)
<center>Fig.5: The Astronomer — Johannes Vermeer, 1668.</center>

<br>

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

*For questions or collaboration, reach out at [epononanvi@gmail.com](mailto:epononanvi@gmail.com) or find me on [GitHub](https://github.com/anvix9) and [Twitter](https://x.com/anvi_al).*
