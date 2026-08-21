# Tracking a Historic Market Crash through Articles

## Project Overview

This project explores the relationship between financial news content and market volatility around the 2008 financial crisis by analyzing temporal changes in financial news and economic indicators. The goal is to understand how textual signals in news coverage correlate with market fluctuations and the propagation of financial risk.

---

## Dataset

We used two primary datasets:

1. **Bloomberg News Corpus (2006–2013):** Daily financial news articles used as textual signals for modeling.
2. **U.S. Economic Indicators:** Macroeconomic and market indicators including the VIX (Volatility Index), stock market performance, and GDP growth.

---

## Methods

### 📘 Text Feature Extraction

- **TF-IDF Vectorization:** We applied TF-IDF to news articles grouped by quarter or month to extract term-frequency-based textual features.
- **Latent Semantic Analysis (LSA):** Because TF-IDF representations generated from different temporal groups can have inconsistent dimensionality, we used **Latent Semantic Analysis (LSA)** to project them into a unified lower-dimensional semantic space.
  - LSA applies Singular Value Decomposition (SVD) to transform high-dimensional sparse matrices into compact semantic representations.
  - This reduces computational complexity while capturing latent semantic structure, improving the consistency and stability of downstream modeling.

### 🤖 Sentiment Modeling with Pretrained Transformer Models

To identify potential market sentiment signals in financial news, we applied four pretrained Transformer models for sentiment classification. For each day, we calculated the mean and variance of sentiment scores:

- **DistilBERT:** A lightweight version of BERT designed to retain strong language-understanding capabilities while improving inference efficiency.
- **Twitter-RoBERTa:** A RoBERTa-based sentiment model optimized on Twitter data.
- **FinBERT:** A BERT-based model pretrained specifically for financial text.
- **FinBERT-Tone:** A FinBERT variant fine-tuned on analyst reports for financial tone classification into positive, neutral, and negative categories.

> **Note:** Neutral samples (`score = 0`) were excluded from sentiment statistics so that the analysis could focus on polarized content that may be more closely associated with shifts in market perception.

---

## Modeling & Evaluation

- **Sentiment Feature Modeling:** Daily sentiment means and variances were used as features for predicting the VIX.
- **Regression Models:** We evaluated Ridge Regression, Random Forest, MLP, and CNN models.
- **Cross-Validation:** Cross-validation was used to assess model stability and generalization performance.
- **Temporal Visualization:** Model predictions and observed market movements were visualized over time and compared with major historical events to examine their alignment.

---

## Project Website

📎 [Project Website](https://fdh.epfl.ch/index.php/Tracking_a_Historic_Market_Crash_through_Articles)

📎 [Full Dataset](https://drive.google.com/drive/folders/1Qub83w8ZarZNbc8vtlHzzgrigN9g8IKu?usp=drive_link)

---

## Authors

- Zimu Zhao
- Xingyu Pan
