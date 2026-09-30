# Awesome Prompt Sensitivity in LLMs

A curated collection of research papers, datasets, tools, implementations and learning resources on **prompt sensitivity** in large language models, and its effect on the **stability of LLM-generated research conclusions**. Each scholarly paper was checked against a publisher, DOI, ACL Anthology or arXiv record before being added. The collection grew out of my AI-assisted review paper and its citation-integrity audit.

## Contents

- [Topic Overview](#topic-overview)
- [AI-Assisted Research Paper](#ai-assisted-research-paper)
- [Citation Integrity Audit](#citation-integrity-audit)
- [Curated Research Papers](#curated-research-papers)
- [Datasets](#datasets)
- [Tools and Libraries](#tools-and-libraries)
- [GitHub Implementations](#github-implementations)
- [Tutorials and Learning Resources](#tutorials-and-learning-resources)
- [How This List Was Verified](#how-this-list-was-verified)
- [License](#license)

## Topic Overview

Large language models are now used to screen literature, extract data, summarise evidence and even draft interpretations. Yet the same request, phrased slightly differently, can produce a different answer. This behaviour, called **prompt sensitivity** (or prompt brittleness), shows up when delimiters, casing, wording, example order or template style change while the meaning stays the same. Studies report accuracy swings of tens of points from formatting alone, and the best format for one model often does not carry over to another.

For research use this matters because the prompt becomes an uncontrolled variable: if a conclusion changes under paraphrase, it may reflect the prompt rather than the evidence. Prompt sensitivity also has to be separated from task ambiguity, sampling randomness (even at temperature zero on some APIs) and silent model updates.

Work in this area falls into a few directions: **measurement** (FormatSpread, POSIX, ProSA, prompt stability scoring), **benchmarks** (PromptBench, multi-prompt evaluation), **mechanistic explanations** (gradient bounds and token interactions), **mitigation** (calibration, template ensembles, self-consistency, declarative prompt optimisation) and **reporting practice** for reproducible LLM-assisted research. Open problems include shared reporting standards, benchmarks for scientific reasoning, and longitudinal tracking of model drift. This repository collects verified resources for all of these.

## AI-Assisted Research Paper

**Prompt Sensitivity and Its Effect on the Stability of LLM-Generated Research Conclusions: A Review of Mechanisms, Evidence, and Methodological Implications for Research Reliability**

A review paper synthesising evidence on how meaning-preserving prompt changes affect LLM outputs, why this threatens the stability and reproducibility of LLM-generated research conclusions, and what measurement, mitigation and reporting practices exist. It also outlines open gaps: standard sensitivity-reporting norms, prompt-invariance benchmarks for scientific reasoning, and governance for LLM-assisted evidence synthesis.

[View Paper](paper/AI_Assisted_Research_Paper.pdf)

## Citation Integrity Audit

References and claims in my paper were checked against original sources instead of being accepted from AI output. Corrections found during the audit are logged in [citation-audit/audit-notes.md](citation-audit/audit-notes.md).

[View Audit](citation-audit/Citation_Integrity_Audit.pdf)

## Curated Research Papers

21 verified papers. Full citation-check table: [references/references.md](references/references.md).

### Foundational Papers

- **Calibrate Before Use: Improving Few-Shot Performance of Language Models**  
  Tony Z. Zhao, Eric Wallace, Shi Feng, Dan Klein, Sameer Singh, 2021, ICML 2021 (PMLR 139, pp. 12697-12706)  
  [Paper / DOI](https://arxiv.org/abs/2102.09690)  
  Early evidence that few-shot accuracy swings with example order, label words and format; proposes contextual calibration.
- **Fantastically Ordered Prompts and Where to Find Them: Overcoming Few-Shot Prompt Order Sensitivity**  
  Yao Lu, Max Bartolo, Alastair Moore, Sebastian Riedel, Pontus Stenetorp, 2022, ACL 2022 (pp. 8086-8098)  
  [Paper / DOI](https://doi.org/10.18653/v1/2022.acl-long.556)  
  Shows that the order of few-shot examples alone can move performance from near state-of-the-art to near chance.
- **Do Prompt-Based Models Really Understand the Meaning of Their Prompts?**  
  Albert Webson, Ellie Pavlick, 2022, NAACL 2022 (pp. 2300-2344)  
  [Paper / DOI](https://doi.org/10.18653/v1/2022.naacl-main.167)  
  Finds models learn as fast with irrelevant or misleading prompts as with sensible ones, questioning what prompts mean to a model.

### Measuring Prompt Sensitivity

- **Quantifying Language Models' Sensitivity to Spurious Features in Prompt Design or: How I Learned to Start Worrying about Prompt Formatting**  
  Melanie Sclar, Yejin Choi, Yulia Tsvetkov, Alane Suhr, 2024, ICLR 2024  
  [Paper / DOI](https://arxiv.org/abs/2310.11324)  
  Introduces FormatSpread; formatting alone changes accuracy by up to 76 points, so report a range instead of a single-prompt score.
- **POSIX: A Prompt Sensitivity Index For Large Language Models**  
  Anwoy Chatterjee, H S V N S Kowndinya Renduchintala, Sumit Bhatia, Tanmoy Chakraborty, 2024, Findings of EMNLP 2024  
  [Paper / DOI](https://arxiv.org/abs/2410.02185)  
  Proposes a task-independent index based on how a response's likelihood shifts under intent-preserving prompt variants.
- **ProSA: Assessing and Understanding the Prompt Sensitivity of LLMs**  
  Jingming Zhuo, Songyang Zhang, Xinyu Fang, Haodong Duan, Dahua Lin, Kai Chen, 2024, Findings of EMNLP 2024  
  [Paper / DOI](https://arxiv.org/abs/2410.12405)  
  Adds instance-level PromptSensiScore and links sensitivity to decoding confidence; larger models and few-shot examples are more robust.
- **What Did I Do Wrong? Quantifying LLMs' Sensitivity and Consistency to Prompt Engineering**  
  Federico Errica, Davide Sanvito, Giuseppe Siracusano, Roberto Bifulco, 2025, NAACL 2025 Long Papers (pp. 1543-1558)  
  [Paper / DOI](https://doi.org/10.18653/v1/2025.naacl-long.73)  
  Defines sensitivity (no ground-truth labels needed) and consistency metrics for classification under prompt rephrasing.
- **Prompt Stability Scoring for Text Annotation with Large Language Models**  
  Christopher Barrie, Elli Palaiologou, Petter Törnberg, 2024, arXiv preprint 2407.02039  
  [Paper / DOI](https://arxiv.org/abs/2407.02039)  
  Adapts inter- and intra-coder reliability to score how stable LLM annotations are across prompt variants; ships a Python package.
- **State of What Art? A Call for Multi-Prompt LLM Evaluation**  
  Moran Mizrahi, Guy Kaplan, Dan Malkin, Rotem Dror, Dafna Shahaf, Gabriel Stanovsky, 2024, TACL 12, pp. 933-949  
  [Paper / DOI](https://doi.org/10.1162/tacl_a_00681)  
  Large study (6.5M instances, 20 LLMs) showing single-template benchmarks are brittle; proposes metrics over many paraphrases.

### Robustness Benchmarks and Evaluation

- **PromptBench (PromptRobust): Towards Evaluating the Robustness of Large Language Models on Adversarial Prompts**  
  Kaijie Zhu, Jindong Wang, Jiaheng Zhou, Zichen Wang, Hao Chen, Yidong Wang, Linyi Yang, Wei Ye, Yue Zhang, Neil Zhenqiang Gong, Xing Xie, 2023, arXiv preprint 2306.04528  
  [Paper / DOI](https://arxiv.org/abs/2306.04528)  
  Benchmark applying character-, word-, sentence- and semantic-level prompt perturbations to test LLM robustness.
- **PromptBench: A Unified Library for Evaluation of Large Language Models**  
  Kaijie Zhu, Qinlin Zhao, Hao Chen, Jindong Wang, Xing Xie, 2024, Journal of Machine Learning Research (MLOSS) 25(254), pp. 1-22  
  [Paper / DOI](https://www.jmlr.org/beta/papers/v25/24-0023.html)  
  Open-source library covering prompt construction, adversarial attacks and evaluation protocols.
- **Mind Your Format: Towards Consistent Evaluation of In-Context Learning Improvements**  
  Anton Voronov, Lena Wolf, Max Ryabinin, 2024, Findings of ACL 2024 (pp. 6287-6310)  
  [Paper / DOI](https://doi.org/10.18653/v1/2024.findings-acl.375)  
  Shows a poor template can drop strong models to random-guess level and best templates do not transfer; proposes Template Ensembles.
- **Benchmarking Prompt Sensitivity in Large Language Models**  
  Amirhossein Razavi, Mina Soltangheis, Negar Arabzadeh, Sara Salamat, Morteza Zihayat, Ebrahim Bagheri, 2025, arXiv preprint 2502.06065  
  [Paper / DOI](https://arxiv.org/abs/2502.06065)  
  Defines the Prompt Sensitivity Prediction task and releases PromptSET, built on TriviaQA and HotpotQA.

### Mechanistic Explanations

- **Understanding the Prompt Sensitivity**  
  Yang Liu, Chenhui Chu, 2026, ACL 2026 (Long Papers, pp. 44362-44388)  
  [Paper / DOI](https://arxiv.org/abs/2604.18389)  
  Uses a first-order Taylor expansion and Cauchy-Schwarz bound to explain why meaning-preserving prompts diverge; templates matter more than questions.
- **Evaluating and Explaining Prompt Sensitivity of LLMs Using Interactions**  
  Ruiyang Qin, Qingzhuo Wang, Tian Wang, Zhihua Wei, Wen Shen, 2026, ICML 2026  
  [Paper / DOI](https://arxiv.org/abs/2608.18539)  
  Interaction-based sensitivity metric over 50 open-source LLMs; fine-tuning, scale, dense architecture and few-shot prompts lower sensitivity.

### Stability, Drift and Non-Determinism

- **How Is ChatGPT's Behavior Changing over Time?**  
  Lingjiao Chen, Matei Zaharia, James Zou, 2024, Harvard Data Science Review  
  [Paper / DOI](https://doi.org/10.1162/99608f92.5317da47)  
  Shows the same commercial LLM service can change behaviour within months, so prompt effects must be separated from model drift.
- **Are Humans as Brittle as Large Language Models?**  
  Jiahui Li, Sean Papay, Roman Klinger, 2025, IJCNLP-AACL 2025 (Long Papers)  
  [Paper / DOI](https://arxiv.org/abs/2509.07869)  
  Compares LLMs and human annotators under identical instruction changes to ask whether prompt brittleness is unique to LLMs.

### Reproducibility in Research Workflows

- **A Primer for Evaluating Large Language Models in Social-Science Research**  
  Suhaib Abdurahman, Alireza Salkhordeh Ziabari, Alexander K. Moore, Daniel M. Bartels, Morteza Dehghani, 2025, Advances in Methods and Practices in Psychological Science 8(2)  
  [Paper / DOI](https://doi.org/10.1177/25152459251325174)  
  Practical recommendations for authors and reviewers on replicable, valid research that uses LLMs.
- **Compiling Prompts, Not Crafting Them: A Reproducible Workflow for AI-Assisted Evidence Synthesis**  
  Teo Susnjak, 2025, arXiv preprint 2509.00038  
  [Paper / DOI](https://arxiv.org/abs/2509.00038)  
  Argues for declarative, test-driven prompt optimisation instead of hand-crafted prompts in systematic literature reviews.
- **A Reproducibility and Generalizability Study of Large Language Models for Query Generation**  
  Moritz Staudinger, Wojciech Kusa, Florina Piroi, Aldo Lipani, Allan Hanbury, 2024, SIGIR-AP 2024 (pp. 186-196)  
  [Paper / DOI](https://doi.org/10.1145/3673791.3698432)  
  Reproduces and extends LLM Boolean-query generation for systematic reviews, testing replicability across ChatGPT and open models.
- **Transforming Literature Screening: The Emerging Role of Large Language Models in Systematic Reviews**  
  Fernando M. Delgado-Chaves, Matthew J. Jennings, Antonio Atalaia, Justus Wolff, Rita Horvath, Zeinab M. Mamdouh, Jan Baumbach, Linda Baumbach, 2025, PNAS 122(2), e2411962122  
  [Paper / DOI](https://doi.org/10.1073/pnas.2411962122)  
  Compares 18 LLMs against human title/abstract screening for three systematic reviews; results depend on how inclusion criteria are phrased.

## Datasets

- **MMLU (Massive Multitask Language Understanding)**  
  Source: Hendrycks et al., ICLR 2021  
  57 multiple-choice tasks across STEM, humanities, social sciences and more, scored with few-shot prompts.  
  Use: Standard benchmark for testing how accuracy changes across prompt formats and templates (e.g. Hugging Face's 8-format MMLU consistency experiments).  
  [Link](https://github.com/hendrycks/test)
- **GSM8K**  
  Source: Cobbe et al., OpenAI, 2021  
  8.5K grade-school math word problems requiring multi-step reasoning.  
  Use: Testing prompt effects on multi-step reasoning, chain-of-thought style prompts and answer-format sensitivity.  
  [Link](https://github.com/openai/grade-school-math)
- **PromptSET**  
  Source: Razavi et al., 2025  
  Prompt variations generated from TriviaQA and HotpotQA questions, for the Prompt Sensitivity Prediction task.  
  Use: Training and evaluating methods that predict whether a rephrased prompt will still get a correct answer.  
  [Link](https://arxiv.org/abs/2502.06065)
- **Human vs LLM brittleness data**  
  Source: Li, Papay and Klinger, University of Bamberg, 2025  
  Human annotations and LLM outputs for text-classification tasks under the same prompt/instruction modifications.  
  Use: Comparing human and LLM sensitivity to label-set, label-order and typo changes.  
  [Link](https://www.uni-bamberg.de/en/nlproc/resources/human-brittleness/)

More detail: [datasets/datasets.md](datasets/datasets.md)

## Tools and Libraries

- **lm-evaluation-harness (EleutherAI)**  
  Unified framework for few-shot evaluation of language models across many tasks, with templated prompts. Run the same task under different prompt templates and compare scores reproducibly.  
  [Link](https://github.com/EleutherAI/lm-evaluation-harness)
- **PromptBench (Microsoft Research Asia)**  
  Library for prompt construction, adversarial prompt attacks, dataset/model loading and evaluation protocols. Test robustness of a model to character-, word- and sentence-level prompt perturbations. Repository is archived (read-only since 17 Mar 2026) but still usable.  
  [Link](https://github.com/microsoftarchive/promptbench)
- **promptstability (Prompt Stability Score)**  
  Python package that scores annotation stability across repeated runs and prompt variants using Krippendorff's alpha. Check stability of an LLM classifier before using its labels in research.  
  [Link](https://promptstability.readthedocs.io/en/stable/)
- **prompt-sensitivity-index (POSIX)**  
  pip-installable implementation of the POSIX prompt sensitivity index for Hugging Face models. Compute a task-independent sensitivity number for a set of intent-aligned prompts.  
  [Link](https://pypi.org/project/prompt-sensitivity-index/)
- **DSPy (Stanford NLP)**  
  Framework for programming rather than hand-writing prompts, with optimisers that tune prompts and weights. Replace brittle hand-tuned prompts with compiled, testable pipelines.  
  [Link](https://github.com/stanfordnlp/dspy)

More detail: [tools/tools.md](tools/tools.md)

## GitHub Implementations

- **msclar/formatspread**  
  FormatSpread: samples many plausible prompt formats and reports a performance interval. Companion code for Sclar et al. (ICLR 2024).  
  [Repository](https://github.com/msclar/formatspread)
- **open-compass/ProSA**  
  Code and project for PromptSensiScore and decoding-confidence analysis. Companion code for Zhuo et al. (Findings of EMNLP 2024).  
  [Repository](https://github.com/open-compass/ProSA)
- **kowndinya-renduchintala/POSIX**  
  Source code to reproduce the POSIX prompt sensitivity index experiments. Companion code for Chatterjee et al. (Findings of EMNLP 2024).  
  [Repository](https://github.com/kowndinya-renduchintala/POSIX)
- **yandex-research/mind-your-format**  
  Code and results for template sensitivity across models and datasets, plus Template Ensembles. Companion code for Voronov et al. (Findings of ACL 2024).  
  [Repository](https://github.com/yandex-research/mind-your-format)
- **ku-nlp/Understanding_the_Prompt_Sensitivity**  
  Experiments for the Taylor-expansion analysis of prompt sensitivity. Companion code for Liu and Chu (ACL 2026).  
  [Repository](https://github.com/ku-nlp/Understanding_the_Prompt_Sensitivity)
- **awebson/prompt_semantics**  
  Code for testing whether models respond to the meaning of prompt templates. Companion code for Webson and Pavlick (NAACL 2022).  
  [Repository](https://github.com/awebson/prompt_semantics)

Selection notes: [implementations/github-repositories.md](implementations/github-repositories.md)

## Tutorials and Learning Resources

- **Improving Prompt Consistency with Structured Generations**  
  Hugging Face blog with Dottxt: shows how MMLU scores vary across 8 prompt formats and how structured generation reduces the spread.  
  [Link](https://huggingface.co/blog/evaluation-structured-outputs)
- **promptstability documentation**  
  Official docs for the Prompt Stability Score package (API reference).  
  [Link](https://promptstability.readthedocs.io/en/stable/)
- **Prompt Stability Scoring walkthrough (C. Barrie)**  
  Author's slides explaining the idea and code for measuring intra- and inter-prompt stability.  
  [Link](https://cjbarrie.quarto.pub/prompt-stability-scoring-d729)
- **DSPy documentation**  
  Official docs and tutorials for compiling and optimising prompts declaratively.  
  [Link](https://dspy.ai)
- **prompt-sensitivity-index usage guide**  
  PyPI page with a worked example of computing POSIX for a Hugging Face model.  
  [Link](https://pypi.org/project/prompt-sensitivity-index/)
- **Prompt engineering overview (Anthropic docs)**  
  Vendor documentation on writing clear, structured prompts; useful baseline for what a 'reasonable' prompt variant looks like.  
  [Link](https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview)

## How This List Was Verified

For every paper I checked the title, authors, year, venue, DOI or arXiv identifier, and that the link opens the same paper. AI tools were used only to find candidates and to check formatting. Papers I could not confirm were left out. Preprints are labelled as preprints. Code repositories were taken from the papers' own pages.

## License

This repository's own text is released under the [MIT License](LICENSE). Linked papers, datasets and code belong to their respective authors and are subject to their own licences. No third-party paper PDFs are hosted here.
