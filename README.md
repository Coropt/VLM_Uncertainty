# VLM Uncertainty

# Literature Review: Uncertainty in LLMs

## Literature Summaries

### 1. Uncertainty Decomposition
- [Hou et al. (2024). *Decomposing Uncertainty for Large Language Models through Input Clarification Ensembling*]
- [summary](papers/hou2023decomposing.md)

### 2. Uncertainty Quantification via Reasoning

- [Li et al. (2025) — *Language Model Uncertainty Quantification with Attention Chain*]
- [summary](papers/li2025language.md)  

### 3. Tools and Frameworks

- [Fadeeva et al. (2023) — *LM-Polygraph: Uncertainty Estimation for Language Models*]  
  We used the **LM-Polygraph** framework in our experiments. It provides a unified Python interface and benchmark for state-of-the-art uncertainty estimation methods (information-based, ensemble-based, density-based, and black-box approaches). In this project, we leveraged their released codebase rather than reproducing all methodological details.

### 4. Benchmarks

- [Yue et al. (2025) — *MMMU-Pro: A More Robust Multi-discipline Multimodal Understanding Benchmark*](https://arxiv.org/abs/2501.04648)  
  We used **MMMU-Pro** as a large-scale evaluation benchmark. It covers a broad set of multi-discipline, multimodal tasks with diverse formats (text, charts, diagrams, images), aiming to more robustly test reasoning and uncertainty quantification in multimodal LLMs. In this project, MMMU-Pro served as the **evaluation dataset** for validating our methods.
