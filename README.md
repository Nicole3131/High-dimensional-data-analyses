https://nicole3131.github.io/High-dimensional-data-analyses/Variable-Selection-in-High-Dimensional-Settings.html

# 🧬 Variable Selection and Post-Selection Inference in High-Dimensional Settings

## 📌 Project Overview
This repository contains an advanced statistical learning project focused on the challenges of **Variable Selection** and **Post-Selection Inference** in high-dimensional datasets (where the number of features $p$ greatly exceeds or is comparable to the number of observations $n$).

Traditional statistical inference fails in high-dimensional settings. While regularization techniques like LASSO are excellent for selecting a sparse subset of relevant variables, performing standard inference (p-values, confidence intervals) on the selected model using the *same* dataset leads to severely biased results. This project explores, implements, and compares methodologies to guarantee valid statistical inference post-selection, controlling for Type I errors.

> **Note on Data:** If a proprietary or specific academic dataset was used for this analysis, the raw data files might not be included in this repository. However, the complete R codebase, simulation scripts (if applicable), and final reports are provided to reproduce the methodology.

## 🛠 Tech Stack
* **Language:** R
* **Variable Selection:** `glmnet` (LASSO regularization)
* **Statistical Inference:** Custom R scripts for hypothesis testing and multiple testing corrections
* **Data Visualization:** `ggplot2`

## 🧠 Methodological Pipeline
The project systematically evaluates different approaches to high-dimensional inference:

1. **LASSO Regularization:** 
   Applying $L_1$ penalty to shrink non-informative feature coefficients to exactly zero, effectively selecting a sparse predictive model.
2. **The Naïve 2-Step Procedure:** 
   * *Method:* Performing LASSO selection and classical OLS inference on the same dataset. 
   * *Analysis:* Demonstrating why this approach is statistically flawed (invalid p-values and inflated Type I errors due to "data snooping").
3. **Data Splitting Strategies:**
   To recover valid inference, the dataset is decoupled into a *selection set* and an *inference set*:
   * **Single Data Split:** A 50/50 split to select variables on one half and compute unbiased p-values on the other. (Analyzed for its trade-off involving loss of statistical power).
   * **Multi-Data Split:** Repeating the splitting process multiple times and aggregating the resulting p-values to stabilize the inference and mitigate the randomness of a single split.
4. **Error Control (Multiple Testing):**
   Applying rigorous statistical thresholds to the resulting p-values to control false discoveries among the selected variables:
   * **FWER (Family-Wise Error Rate):** Controlling the probability of making at least one Type I error (e.g., Bonferroni correction).
   * **FDR (False Discovery Rate):** Controlling the expected proportion of false rejections among all rejections (e.g., Benjamini-Hochberg procedure) for a more powerful, scalable approach in high dimensions.


