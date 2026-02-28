# 📊 PDF Learning — Assignment 2

> **Learning a Probability Density Function Using a Roll-Number-Based Non-Linear Transformation**

---

## 🧾 Overview

This project estimates a **Probability Density Function (PDF)** from real-world environmental data after applying a personalized non-linear transformation. It demonstrates the practical relationship between data preprocessing, mathematical distortion, and probabilistic modeling.

The dataset used contains **Nitrogen Dioxide (NO₂)** concentration measurements from India's air quality monitoring records. A sinusoidal transformation — uniquely parameterized by the student's roll number — is applied before fitting a Gaussian-like PDF to the resulting distribution.

---

## 📂 Dataset

| Property | Details |
|---|---|
| **Dataset** | India Air Quality Dataset |
| **Source** | [Kaggle](https://www.kaggle.com/) |
| **Feature Used** | NO₂ (Nitrogen Dioxide Concentration) |
| **Data Type** | Continuous numerical measurements |

### Preprocessing Steps
- Removed non-numeric entries
- Discarded missing/null values
- Standardized column names for consistency

---

## 🔁 Step 1: Roll-Number-Based Non-Linear Transformation

Each original NO₂ value $x$ is transformed into $z$ using:

$$z = x + a_r \sin(b_r x)$$

The coefficients $a_r$ and $b_r$ are derived from roll number $r$ as follows:

$$a_r = 0.05 \times (r \mod 7)$$

$$b_r = 0.3 \times ((r \mod 5) + 1)$$

### Parameters for Roll Number `102317299`

| Parameter | Calculation | Value |
|---|---|---|
| $a_r$ | `0.05 × (102317299 mod 7)` = `0.05 × 0` | **0.00** |
| $b_r$ | `0.3 × ((102317299 mod 5) + 1)` = `0.3 × 5` | **1.50** |

> Since $a_r = 0$, the transformation simplifies to $z = x$ — meaning the sinusoidal distortion has **no effect** for this roll number, and the transformed distribution mirrors the original NO₂ data.

---

## 📐 Step 2: Learning the PDF

The transformed data is modeled using a **Gaussian-like PDF**:

$$\hat{p}(z) = c \cdot e^{-\lambda(z - \mu)^2}$$

### Parameter Estimation

| Symbol | Meaning | Formula |
|---|---|---|
| $\mu$ | Mean (central tendency) | $\mu = \frac{1}{n} \sum_{i=1}^{n} z_i$ |
| $\sigma^2$ | Variance (spread) | $\sigma^2 = \frac{1}{n} \sum_{i=1}^{n} (z_i - \mu)^2$ |
| $\lambda$ | Spread control parameter | $\lambda = \frac{1}{2\sigma^2}$ |
| $c$ | Normalization constant | $c = \frac{1}{\sigma\sqrt{2\pi}}$ |

All parameters are computed directly from the transformed dataset using standard statistical estimation.

---

## 📈 Visualization & Analysis

The following plots are generated to validate the learned distribution:

1. **Histogram** of the transformed variable $z$
2. **PDF curve** of the estimated Gaussian-like function $\hat{p}(z)$
3. **Overlay plot** comparing the empirical histogram with the fitted PDF

These visualizations confirm that the estimated PDF is a reasonable approximation of the actual data distribution.

---

## 🧪 Workflow Summary

```
1. Load the India Air Quality dataset
2. Extract and clean NO₂ concentration values
3. Apply roll-number-dependent transformation: z = x + a_r·sin(b_r·x)
4. Compute μ, σ², λ, and c from transformed data
5. Construct the Gaussian-like PDF: p̂(z) = c·exp(−λ(z−μ)²)
6. Visualize: histogram, PDF curve, and overlay comparison
```

---

## 🚀 How to Run

1. Download the **India Air Quality Dataset** from [Kaggle](https://www.kaggle.com/)
2. Place the dataset CSV in the working directory (or update the file path in the notebook)
3. Set your **roll number** in the notebook configuration cell
4. Run all cells sequentially
5. Review the estimated parameters and generated plots

---

## 📌 Key Takeaways

- The roll-number-based transformation ensures **every student gets a unique dataset variant**
- For roll number `102317299`, $a_r = 0$, so $z = x$ (no sinusoidal distortion)
- The Gaussian-like PDF provides a simple yet effective model for continuous environmental data
- Parameters $\mu$, $\lambda$, and $c$ fully characterize the learned distribution

---

## 📎 References

- Gaussian (Normal) Distribution — Statistical Theory
- Maximum Likelihood & Method of Moments — Parameter Estimation
- [India Air Quality Dataset — Kaggle](https://www.kaggle.com/)
- Probability Theory and Statistical Modeling — Course Materials
