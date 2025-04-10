# Tracking a Historic Market Crash through Articles

## 项目简介 | Project Overview

本项目通过分析金融新闻文本与经济指标的时序变化，探索在 2008 年金融危机前后，文本内容与市场波动之间的相关性，目标是理解新闻在金融风险传播中的作用。  
This project explores the relationship between financial news content and market volatility around the 2008 crisis, aiming to understand how textual signals correlate with systemic risk.

---

## 数据来源 | Dataset

我们使用了两个主要数据集：

1. **Bloomberg 新闻语料**（2006–2013）：涵盖每日财经报道，提供文本信号用于建模。  
2. **美国经济指标数据**：包括 VIX（恐慌指数）、股市表现、GDP 增速等宏观经济信号。

---

## 分析方法 | Methods

### 📘 文本特征提取

- **TF-IDF 向量化**：对季度 / 月度分组的文本进行词频统计；
- **LSA 降维**：由于分组处理导致 TF-IDF 向量维度不一致，我们使用 **Latent Semantic Analysis (LSA)** 进行统一降维。
  - LSA 基于奇异值分解（SVD），将高维稀疏矩阵投影到统一的低维语义空间；
  - 它既降低了计算负担，又捕捉到了潜在语义结构，增强后续建模的稳定性和一致性。

### 🤖 情感建模：四种预训练 Transformer 模型

为识别新闻中潜在的市场情绪信号，我们使用四种 Transformer 模型对新闻进行情感分类，输出每日情感均值和方差：

- **DistilBERT**：轻量版 BERT，保留语言理解能力，提升推理效率；
- **Twitter-roBERTa**：基于 tweet 数据优化的情感分类模型；
- **FinBERT**：专为金融文本预训练的 BERT 模型；
- **FinBERT-Tone**：在分析师报告上精调的版本，专注于语气识别（positive / neutral / negative）。

⚠️ 在情感统计中，我们剔除了中性情绪样本（score=0），以更聚焦于对市场可能造成认知偏移的极性内容。

---

## 建模与评估 | Modeling & Evaluation

- **情感统计特征建模**：使用每日情感均值 / 方差预测 VIX 指数；
- **回归模型**：包括 Ridge Regression、Random Forest, MLP, CNN；
- **交叉验证**：评估模型稳定性，提升泛化性能；
- **时序可视化**：结合历史事件分析模型预测信号与真实波动之间的对齐程度。

---

## 项目网站 | Project Website

📎 [https://fdh.epfl.ch/index.php/Tracking_a_Historic_Market_Crash_through_Articles](https://fdh.epfl.ch/index.php/Tracking_a_Historic_Market_Crash_through_Articles)  
📎 If you want the access of our full datasets, please click https://drive.google.com/drive/folders/1Qub83w8ZarZNbc8vtlHzzgrigN9g8IKu?usp=drive_link
---

## 作者 | Authors

- Zimu Zhao  
- Xingyu Pan



