---
layout: page
title: Portfolio
permalink: /portfolio/
---

<figure style="text-align: center;">
    <img src="https://upload.wikimedia.org/wikipedia/commons/b/b9/Caspar_David_Friedrich_-_Wanderer_above_the_sea_of_fog.jpg" alt="Wanderer above the Sea of Fog" width="300"/>
    <figcaption>Fig.1: Wanderer above the Sea of Fog — Caspar David Friedrich, 1818.</figcaption>
</figure>
<br/>

<p style="text-align: justify;">There is something interesting about the act of building. Not building for the sake of producing, but building as a way to understand. Every project listed here started from a question I could not answer by reading alone, I had to construct something to see whether my intuition held or collapsed under its own weight.</p>

This page gathers research, tools, teaching, and the traces of that process.

______

## Featured Work: ReSynth
<br/>
### How Psychological Learning Paradigms Shaped and Constrained Artificial Intelligence

<figure style="text-align: center;">
    <img src="https://upload.wikimedia.org/wikipedia/commons/b/ba/Filhol_1814.jpg" alt="Philosopher in Meditation" width="300"/>
    <figcaption>Fig.2: Philosopher in Meditation — Rembrandt van Rijn, 1632.</figcaption>
</figure>
<br/>

<p style="text-align: justify;">This paper is, in many ways, the philosophical backbone behind everything else on this page. It asks a question that is rarely posed in our field: what if the limitations we observe in current AI systems are not merely technical, but inherited? Inherited from the very psychological theories that inspired them.</p>

<p style="text-align: justify;">Behaviorism gave us reinforcement learning, but also its blindness to the internal structure of knowledge. Cognitivism gave rise to deep learning, but compressed representations into opaque parameter spaces that resist principled update. Constructivism influenced curriculum learning, yet we still lack a formal account of how new understanding is constructed from existing components.</p>

<p style="text-align: justify;">The paper traces this genealogy from psychological paradigm to AI method, and diagnoses the structural constraints each paradigm carried into its artificial offspring. It also examines a cross-cultural divergence in the interpretation of rote learning: the Eastern conception of memorization as a structured, multi-phase precursor to understanding offers a bridge between psychological theory and AI methodology that remains largely unexploited.</p>

<p style="text-align: justify;">From this analysis emerges <b>ReSynth</b>, a trimodular framework that separates three architecturally independent components:</p>

- **Intellect** - the reasoning mechanism
- **Identity** - the purpose and directional coherence
- **Memory** - the knowledge substrate

<p style="text-align: justify;">The central argument is that adaptability, the challenge at the heart of artificial general intelligence requires a representational architecture in which systematic behavior is a <i>necessary consequence</i> rather than an accidental property.</p>

<p style="text-align: justify;">A white paper expanding this framework is currently in preparation.</p>

<p style="text-align: justify;">An interactive evaluation demo is available, it walks through the paper's genealogy from psychology to AI, the rote learning reappraisal, the structural diagnosis of each paradigm, and the ReSynth trimodular architecture. It also includes an interactive scoring tool for reviewers and readers to assess the work across six criteria.</p>

<br/>
**Links:** [arXiv](https://arxiv.org/abs/2603.18203) · [PDF](https://arxiv.org/pdf/2603.18203) · [Evaluation Demo](https://github.com/anvix9/resynth-evaluation-demo/tree/main)

______

## Research Projects

<br/>
### Question-Knowledge Compression RAG

*Enhancing Multihop Document Retrieval without Fine-tuning*

<p style="text-align: justify;">The central question was simple: why do we need tens of thousands of embedding vectors to represent a hundred papers? The answer turned out to be — we don't.</p>

<p style="text-align: justify;">This pipeline compresses scientific papers into lightweight "paper-cards" (~5 KB each) using generated questions and queries. It replaces 44,809 chunk embeddings with just 109 vectors roughly 80% storage reduction — while outperforming BM25 and fine-tuned baselines on both single-hop and multi-hop retrieval.</p>

<p style="text-align: justify;">The system introduces a syntactic reranking method that decomposes queries at POS boundaries and reranks passages by document frequency, all without any model fine-tuning.</p>

| Metric | Our Approach | Best Baseline |
|--------|-------------|---------------|
| Accuracy (Single-hop) | **0.844** | 0.789 (BM25) |
| MRR (Single-hop) | **0.803** | 0.677 (BM25) |
| F1 (Multi-hop, Llama3) | **0.550** | 0.412 (CFIC-7B) |
| Embedding Records | **109** | 44,809 (Fixed-size) |

<br/>

**Pipeline:** Paper Input (2–70 MB) → Section Extraction → Question Generation → Paper-Card (~5 KB) → Syntactic Reranking → Result

<br/>
**Links:** [GitHub-Demo](https://github.com/anvix9/question-knowledge-compression-rag) · [Paper (Preprint)](https://doi.org/10.20944/preprints202601.1757.v2)

______

<br/>
### Haut

*Research Search Engine for Literature Reviews*

<figure style="text-align: center;">
    <img src="https://upload.wikimedia.org/wikipedia/commons/archive/9/9c/20170902010738%21Joseph_Wright_of_Derby_The_Alchemist.jpg" alt="The Alchemist Discovering Phosphorus" width="300"/>
    <figcaption>Fig.3: The Alchemist Discovering Phosphorus — Joseph Wright of Derby, 1771.</figcaption>
</figure>
<br/>

<p style="text-align: justify;">Haut was born from a frustration familiar to any researcher: the time spent searching for what has already been done before you can even begin to think about what hasn't. It is a platform for building literature reviews on NLP and deep learning, designed to find relevant articles based on a specific methodology or research question, and to suggest potential future directions.</p>

<p style="text-align: justify;">It introduces a semantic chunking system based on <i>question anchors</i> with a FlashRank reranking method. The compression is drastic: initial texts of 2–70 MB reduce to approximately 1 KB per file in the vector database, with response quality comparable to traditional methods.</p>

<br/>
**Links:** [GitHub](https://github.com/anvix9/haut)

______

<br/>
### Sherlock-lit

*Python Package for Research Paper Analysis*

<p style="text-align: justify;">Sherlock-lit is a tool built out of necessity, part of the Haut ecosystem. It leverages NLP and LLMs to quickly extract the contributions and research questions from academic papers, generating concise markdown cards. It is designed to run efficiently on CPUs (under 70 MB), with optional GPU support.</p>

```
$ pip install sherlock-lit
$ sherlock_lit paper.pdf
# → Generates a markdown card in card-papers/
```

<br/>
**Links:** [GitHub](https://github.com/anvix9/sherlock-lit) · [PyPI](https://pypi.org/project/sherlock-lit/)

______

<br/>
## Other Projects

<p style="text-align: justify;"><b>Convolution in C++</b> — From-scratch implementation of 2D convolution using C++ template metaprogramming. An educational deep-dive into the fundamental operations underlying CNNs. <a href="https://github.com/anvix9/convolution">GitHub</a> · <a href="https://anvix9.github.io/2024/08/08/Experiment-1-2D-Convolution-in-C++-from-scratch-with-intuition">Blog Post</a></p>

<p style="text-align: justify;"><b>AWS Token Refresh Automation</b> — Guide and Python script for refreshing AWS SSO tokens automatically, solving the common pain of expired credentials in CI/CD workflows. <a href="https://github.com/anvix9/AWS-Token-Refresh-Automation-Guide-in-terminal-">GitHub</a></p>

______

## Publications

<figure style="text-align: center;">
    <img src="https://www.thoughtco.com/thmb/DlzsYR0whBb3taEl45YTviOZtxM=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc()/GettyImages-11410491702-07f03ccd0eb54d36a9b62212cd2f55a1.jpg" alt="Plato - Allegory of the Cave" width="300"/>
    <figcaption>Fig.4: Plato - Allegory of the Cave.</figcaption>
</figure>
<br/>

1. **Eponon, A.A.**, Batyrshin, I., Maldonado-Sifuentes, C.E. and Sidorov, G., 2025. *How Psychological Learning Paradigms Shaped and Constrained Artificial Intelligence.* arXiv. [Paper](https://arxiv.org/abs/2603.18203) — See [Featured Work](#featured-work--resynth) above.

2. **Eponon, A.A.**, Shahiki-Tash, M., Batyrshin, I., Maldonado-Sifuentes, C.E., Sidorov, G. and Gelbukh, A., 2025. *Knowledge and Context Compression via Question Generation: Enhancing Multihop Document Retrieval without Fine-tuning.* Preprint. [DOI](https://doi.org/10.20944/preprints202601.1757.v2)

3. Alex Eponon and Luis Ramos Perez, 2024. *Pinealai at SemEval-2024 Task 1: Exploring Semantic Relatedness Prediction using Syntactic, TF-IDF, and Distance-Based Features.* SemEval-NAACL, Mexico City.

4. **Eponon, A.A.**, Batyrshin, I. and Sidorov, G., 2024. *Pinealai stressident LT-EDI@EACL2024: Minimal Configurations for Stress Identification in Tamil and Telugu.* EACL, Malta.

5. Alex-Eponon, A., Tayyab-Zamir, M., Kawo-Eyob, L., Ramos-Perez, L.I., et al., 2024. *From Simple Detection to Quality-aware Prediction: Exploring Argument Complexity with Machine Learning.* MICAI, Mexico.

6. **Eponon, A.A.** and Dimililer, K., 2022. *A Bert Model with Deep Learning Approach in Natural Language Processing.* 12th WCIS, Tashkent. Springer Nature Switzerland.

______

## Teaching & Talks

<figure style="text-align: center;">
    <img src="https://upload.wikimedia.org/wikipedia/commons/4/49/%22The_School_of_Athens%22_by_Raffaello_Sanzio_da_Urbino.jpg" alt="The School of Athens" width="300"/>
    <figcaption>Fig.5: The School of Athens — Raphael, 1511.</figcaption>
</figure>
<br/>

<p style="text-align: justify;">Teaching, to me, is not about transferring information — it is about transferring the desire to investigate. The courses I design are built around that principle: give students real tools, real problems, and real constraints, and let the curiosity do the rest.</p>

<br/>
### Professor - M.Sc. in Artificial Intelligence

<br/>
**Universidad Mayor de San Andrés (UMSA)**, La Paz, Bolivia — *Feb 2025 – Feb 2026*

<p style="text-align: justify;">Four modules spanning business strategy and AI ecosystems, ETL pipeline development (Scrapy, Pandas, SQL), NLP fundamentals from Bag of Words to Transformers with practical RAG system building, and advanced model optimization covering NeMo Curator, fine-tuning, distillation, pruning, and quantization.</p>

<p style="text-align: justify;">The classroom operates as a collaborative environment on Hugging Face, where student groups build and deploy their own models — from data curation to API serving.</p>

<br/>
**Links:** [UMSA Classroom on Hugging Face](https://huggingface.co/umsa-v1) (22 students)

<br/>
### Master's Workshop — NVIDIA NeMo Curator Pipeline

<br/>
**UMSA**, La Paz, Bolivia — *Dec 2–3, 2025*

### Invited Speaker - AI in Social Sciences
<br/>

**UNAM Conference**, Mexico City — *Nov 25, 2025*

<p style="text-align: justify;">Topic: Intersection between Social Sciences and Artificial Intelligence — Exploring the link between social sciences and advanced technology.</p>

<br/>
### Invited Speaker - Role of Semantics in AI

**EVCCCPLN** — *Jul 2024*

______

## Education

<figure style="text-align: center;">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e4/Johannes_Vermeer_-_The_Astronomer_-_1668.jpg/3840px-Johannes_Vermeer_-_The_Astronomer_-_1668.jpg" alt="The Astronomer" width="300"/>
    <figcaption>Fig.6: The Astronomer — Johannes Vermeer, 1668.</figcaption>
</figure>
<br/>

- **Ph.D. in Natural Language Processing** — Instituto Politécnico Nacional (CIC), Mexico City — *2023 – Present*
- **M.Sc. in Software Engineering** (GPA 3.8/4.0) — Near East University, Cyprus — *2020 – 2023*
<!-- - **B.Sc. in Computer Science** (GPA 7.2/10) — Valoris International University — *2016 – 2020* -->

______

## Technical Skills

**Languages:** Python, C++, JavaScript, Bash, SQL, HTML/CSS

**ML / NLP:** PyTorch, Hugging Face, Spacy, NVIDIA NeMo Curator, LLM fine-tuning & distillation, RAG, pruning & quantization

**Data & Vector:** Pinecone, FAISS, Pandas, NumPy, PostgreSQL, MySQL, web scraping, ETL/ELT

**DevOps & Tools:** Git/GitHub, Docker, FastAPI, Selenium, Linux/Ubuntu, VIM

**Languages spoken:** French (native), English (C2), Spanish (C1)

______

*For questions or collaboration, reach out at [epononanvi@gmail.com](mailto:epononanvi@gmail.com) or find me on [GitHub](https://github.com/anvix9) and [Twitter](https://x.com/anvi_al).*
