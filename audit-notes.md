# Citation Audit Notes

Findings from re-checking the reference list of my review paper against original sources.

## Corrections needed

| Reference in paper | Problem | Correct entry |
|---|---|---|
| Katz, U., et al. (2025), PNAS | Wrong first author. The DOI is correct. | Delgado-Chaves, F. M., et al. (2025). Transforming literature screening: The emerging role of large language models in systematic reviews. *PNAS*, 122(2), e2411962122. In-text: "Delgado-Chaves et al., 2025" instead of "PNAS, 2025". |
| "Understanding the prompt sensitivity of LLMs" (2026) | No authors or venue. | Liu, Y., & Chu, C. (2026). Understanding the prompt sensitivity. *ACL 2026*. arXiv:2604.18389. |
| "Evaluating and explaining prompt sensitivity of LLMs using interactions" (2026) | No authors. | Qin, R., Wang, Q., Wang, T., Wei, Z., & Shen, W. (2026). *ICML 2026*. arXiv:2608.18539. |
| "POSIX" (2024) | No authors. | Chatterjee, A., Renduchintala, H. S. V. N. S. K., Bhatia, S., & Chakraborty, T. (2024). POSIX: A prompt sensitivity index for large language models. *Findings of EMNLP 2024*. arXiv:2410.02185. |
| "Are humans as brittle as large language models?" (2025) | No authors. | Li, J., Papay, S., & Klinger, R. (2025). *IJCNLP-AACL 2025*. arXiv:2509.07869. |
| Staudinger et al. (2024) | Page range given as 1-11. | SIGIR-AP 2024, pp. 186-196. DOI 10.1145/3673791.3698432. |
| PromptBench library (Zhu et al., 2023) | Cited as arXiv only. | Also published: *JMLR* 25(254), 1-22, 2024. |
| Zhu et al. (2023), PromptBench/PromptRobust | Author order differs from the POSIX reference list (Yue Zhang before Neil Zhenqiang Gong). | Check the arXiv 2306.04528 author list and fix. |
| "PMC, 2025" (radiology perturbation study) | No authors or title. PMC ID not confirmed. | Probably Sorin V. et al., "Evaluating prompt and data perturbation sensitivity in large language models for radiology reports classification", *JAMIA Open* 2025;8(4). Confirm that PMC12343119 is this article before citing. |
| "Open Source Advantage in LLMs literature, 2024" | Cited in Section 5 but missing from the reference list. | Find the real source or remove the citation. |

## Verified in this pass

Abdurahman et al. (2025); Barrie et al. (2024); Susnjak (2025); Sclar et al. (2024, arXiv record); Zhao et al. (2021, details match POSIX's reference list); Staudinger et al. (2024); Delgado-Chaves et al. (2025); Liu & Chu (2026); Qin et al. (2026); Chatterjee et al. (2024); Li et al. (2025).

## Not yet checked (do these yourself)

Gougherty & Clipp (2024); Ji et al. (2023); Wang et al. (2022); Wei et al. (2022). Also confirm the Sclar et al. venue (ICLR 2024) on OpenReview and the claim about Cohen's kappa above .90 in Abdurahman et al. (2025).

## Update the paper

Fix the entries above in the paper and its BibTeX file, then re-export the PDF before uploading it to `paper/`.
