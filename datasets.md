# Datasets

Benchmarks and data used to study prompt sensitivity.

## MMLU (Massive Multitask Language Understanding)

- **Source:** Hendrycks et al., ICLR 2021
- **Description:** 57 multiple-choice tasks across STEM, humanities, social sciences and more, scored with few-shot prompts.
- **Application:** Standard benchmark for testing how accuracy changes across prompt formats and templates (e.g. Hugging Face's 8-format MMLU consistency experiments).
- **Link:** https://github.com/hendrycks/test
- **Note:** Also on Hugging Face as cais/mmlu; MIT licence per the dataset card.

## GSM8K

- **Source:** Cobbe et al., OpenAI, 2021
- **Description:** 8.5K grade-school math word problems requiring multi-step reasoning.
- **Application:** Testing prompt effects on multi-step reasoning, chain-of-thought style prompts and answer-format sensitivity.
- **Link:** https://github.com/openai/grade-school-math
- **Note:** Paper: https://arxiv.org/abs/2110.14168

## PromptSET

- **Source:** Razavi et al., 2025
- **Description:** Prompt variations generated from TriviaQA and HotpotQA questions, for the Prompt Sensitivity Prediction task.
- **Application:** Training and evaluating methods that predict whether a rephrased prompt will still get a correct answer.
- **Link:** https://arxiv.org/abs/2502.06065
- **Note:** Described in the paper. Not to be confused with the unrelated 'PromptSet: A Programmer's Prompting Dataset'.

## Human vs LLM brittleness data

- **Source:** Li, Papay and Klinger, University of Bamberg, 2025
- **Description:** Human annotations and LLM outputs for text-classification tasks under the same prompt/instruction modifications.
- **Application:** Comparing human and LLM sensitivity to label-set, label-order and typo changes.
- **Link:** https://www.uni-bamberg.de/en/nlproc/resources/human-brittleness/
- **Note:** About 31 MB download from the authors' page.

