---
title: "fin-news-fusion: Fusing Financials and News to Predict Industry Outperformance"
excerpt: "Multimodal deep learning (PyTorch) that combines structured financial statements with news-headline embeddings to predict which A-share companies beat their industry peers. MIT 15.773 Hands-On Deep Learning."
collection: portfolio
---

**Code:** [github.com/x1c0124/fin-news-fusion](https://github.com/x1c0124/fin-news-fusion)

A multimodal neural network that predicts whether a company's return on assets beats its industry median. It uses two inputs:

- **Financial data**: 63 structured features from 277 Chinese A-share companies, including engineered ratios and industry one-hot encodings
- **News text**: Yahoo Finance headlines, embedded with `all-MiniLM-L6-v2` (384 dimensions)

Each input goes through its own encoder. The two encodings are concatenated and passed through a learned sigmoid gate before the classifier.

**Results**

| Model | Test AUC |
|---|:---:|
| Financial-only MLP baseline | 0.927 |
| Multimodal (financials + news) | 0.875 |

The multimodal model scores an AUC of 0.892 ± 0.034 in 5-fold cross-validation. On this dataset, adding news text did not beat the financial-only baseline. A likely reason is that the label is built from Net Profit and Total Assets, which the financial features already include.

*Tools: PyTorch, sentence-transformers, scikit-learn, pandas*
