# Style-Perturbed Hate Speech Benchmark

## Overview

This repository provides a style-perturbed benchmark for robustness evaluation in hate speech detection. The benchmark is derived from three widely used datasets:

- **IHC**
- **SBIC**
- **DynaHate**

For each source dataset, we construct multiple stylistic perturbation settings while preserving the original label semantics as much as possible. Each benchmark includes the original test set together with several matched perturbed variants, enabling controlled comparison between clean and style-shifted inputs.

The benchmark is designed to test whether a model relies on task-relevant semantic content or exhibits residual dependence on superficial stylistic cues. In addition to perturbed texts and class labels, the released files retain sample-level metadata when available, supporting reproducible evaluation and fine-grained analysis across perturbation types and annotation rounds.

This resource provides a practical testbed for studying:

- robustness under stylistic variation
- prediction consistency
- label stability under semantically preserving perturbations

It is particularly suitable for evaluating:

- large language model based classifiers
- robustness-oriented text classifiers
- causal content-style disentanglement methods

---

## Benchmark Design

Each source dataset contains **four matched versions** of the test set:

- **O**: Original
- **A**: AAE-style perturbation
- **B**: Gang slang perturbation
- **C**: Internet slang perturbation

These matched variants are intended for robustness evaluation under controlled stylistic changes. The goal is to assess whether model predictions remain stable when surface realization changes while label-relevant semantic content is preserved as much as possible.

---

## Dataset Structure

### IHC
- `ihc_test_processed_O.tsv`
- `ihc_test_processed_A.tsv`
- `ihc_test_processed_B.tsv`
- `ihc_test_processed_C.tsv`

### SBIC
- `sbic_test_processed_O.csv`
- `sbic_test_processed_A.csv`
- `sbic_test_processed_B.csv`
- `sbic_test_processed_C.csv`

### DynaHate
- `dyna_test_processed_O.csv`
- `dyna_test_processed_A.csv`
- `dyna_test_processed_B.csv`
- `dyna_test_processed_C.csv`

---

## How to Use

This benchmark is intended primarily for **evaluation**, rather than unrestricted standalone training.

A recommended usage protocol is:

1. Evaluate a model on the original test set (**O**).
2. Evaluate the same model on the corresponding perturbed test sets (**A**, **B**, **C**).
3. Compare predictive behavior across conditions.
4. Analyze whether prediction changes are induced by stylistic perturbations.

Files from the same source dataset should always be treated as **matched evaluation variants**.

---

## Recommended Evaluation Metrics

We recommend reporting the following metrics:

- **Accuracy**
- **Macro-F1**
- **Consistency**
- **Flip Rate**

### Metric Intuition

- **Accuracy / Macro-F1** measure predictive performance under each perturbation setting.
- **Consistency** measures how often predictions remain unchanged relative to the original input.
- **Flip Rate** measures how often predictions change under stylistic perturbation.

Together, these metrics support both performance evaluation and robustness analysis.

---

## Important Notes

- The perturbation condition is indicated by the file name suffix: `O`, `A`, `B`, `C`.
- Files from the same source dataset are matched and should be compared jointly.
- This benchmark is designed for **robustness evaluation** and **style sensitivity analysis**.
- Some files retain metadata fields such as annotator identifiers, target categories, and annotation rounds to support reproducibility and more fine-grained analysis.
- Because the perturbed versions are designed for controlled evaluation, users should avoid mixing all variants indiscriminately for standard supervised training without considering the benchmark design.

---

## Intended Use Cases

This benchmark is suitable for studying questions such as:

- Does a model rely on semantic content or stylistic shortcuts?
- How stable are predictions under semantically preserving stylistic shifts?
- Which perturbation types cause the largest degradation?
- Do different architectures differ in robustness to style variation?
  year={2026},
  note={Dataset release}
}
