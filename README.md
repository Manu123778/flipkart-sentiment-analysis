# 🛒 Flipkart Product Review — Sentiment Analysis

![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square&logo=python)
![NLP](https://img.shields.io/badge/NLP-TF--IDF-orange?style=flat-square)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-green?style=flat-square)
![HuggingFace](https://img.shields.io/badge/Deploy-HuggingFace-yellow?style=flat-square&logo=huggingface)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)

An end-to-end NLP project that classifies **163,000+ Flipkart product reviews** into
Positive, Neutral, and Negative sentiment using XGBoost + TF-IDF — with a live
interactive dashboard deployed on Hugging Face Spaces.

---

## 🚀 Live Dashboard

👉 **[https://manu9390-flipkart-sentiment-dashboard.hf.space](https://manu9390-flipkart-sentiment-dashboard.hf.space)**

---

## 📊 Key Findings

| Insight | Finding |
|---|---|
| Overall Positive sentiment | 78.8% of reviews |
| Overall Negative sentiment | 14.4% of reviews |
| Avg Rating | 4.06 / 5 |
| Worst price range | ₹2K–5K (17.1% negative) |
| #1 complaint word | "quality" (6,148 mentions) |
| Negative reviews are longer | Avg 12.6 words vs 9.8 for Positive |

---

## 🧠 Model Performance

| Model | Macro F1 | Weighted F1 | Accuracy |
|---|---|---|---|
| **XGBoost** ✅ | **0.92** | 0.96 | 0.96 |
| Random Forest | 0.90 | 0.95 | 0.95 |
| Logistic Regression | 0.88 | 0.94 | 0.94 |

> **Why Macro F1?** Dataset is imbalanced (76% Positive). Macro F1 treats all
> 3 classes equally and is a more honest metric than accuracy.

---

## 🗂️ Project Structure

```
flipkart-sentiment-analysis/
│
├── sentiment_analysis.ipynb     ← main notebook (all steps)
├── flipkart_dashboard_data.csv  ← cleaned data with predictions
├── app.py                       ← Plotly Dash dashboard
├── Dockerfile                   ← HuggingFace deployment
├── requirements.txt
└── README.md
```

---

## 🔄 Project Pipeline

```
Raw Data (189,874 reviews)
        ↓
Data Cleaning
  → Remove duplicates (24,861)
  → Fix encoding issues (â¹, ??, emojis)
  → Fix Rate column (product names in wrong column)
  → Combine Review + Summary into single text
        ↓
Text Preprocessing
  → Lowercase + remove punctuation
  → Remove stopwords (NLTK)
  → Lemmatization
  → TF-IDF Vectorization (10,000 features, bigrams)
        ↓
Train-Test Split (80/20, stratified)
        ↓
Model Training
  → Logistic Regression (baseline)
  → Random Forest
  → XGBoost (best)
        ↓
Business Insights + Live Dashboard
```

---

## 💼 Business Insights

**What the data reveals about Flipkart sellers:**

1. **Quality is the #1 problem** — "quality" appears 6,148 times in negative reviews,
   far ahead of any other complaint word. This points to systematic supplier-level issues.

2. **Customers feel cheated** — "money" (4,424) and "waste" (4,297) appear together
   frequently, meaning product listings do not match what customers receive.

3. **₹2K–5K range has highest dissatisfaction** — Mid-premium customers spending
   significant money on appliances are the most disappointed segment (17.1% negative).

4. **Products are failing post-purchase** — "working" and "stopped" frequently appear
   in negative reviews, indicating reliability and durability issues.

**Recommendations:**
- Flag sellers with >20% negative reviews for quality audit
- Enforce stricter product listing accuracy for ₹2K–5K category
- Use this NLP pipeline in production to auto-tag incoming reviews daily

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Data Wrangling | pandas, numpy |
| Text Processing | NLTK, re |
| Modeling | scikit-learn, XGBoost |
| Visualization | matplotlib, seaborn, wordcloud |
| Dashboard | Plotly Dash |
| Deployment | Docker, Hugging Face Spaces |

---

## 📁 Dataset

- **Source:** [Flipkart Product Reviews — Kaggle](https://www.kaggle.com/)
- **Raw rows:** 189,874
- **After cleaning:** 162,975
- **Columns used:** ProductName, Price, Rate, Review, Summary

---

## ⚙️ Run Locally

```bash
# Clone the repo
git clone https://github.com/manu9390/flipkart-sentiment-analysis.git
cd flipkart-sentiment-analysis

# Install dependencies
pip install -r requirements.txt

# Run dashboard
python app.py
```

Open `http://localhost:7860` in your browser.

---

## 👤 Author

**Manu** | Data Analyst | Bangalore, India

[![HuggingFace](https://img.shields.io/badge/HuggingFace-manu9390-yellow?logo=huggingface)](https://huggingface.co/manu9390)
