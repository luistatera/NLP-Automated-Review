# 🧠 NLP Project: Automated Review Analysis and Product Recommendations

> Final project for Ironhack AI/ML Bootcamp by **Luis Guimarães**

---

## 📌 Project Overview

This project automates the analysis of customer reviews for fashion products on Amazon using Natural Language Processing (NLP). The goal is to help small e-commerce businesses extract meaningful insights from large volumes of textual data — identifying product sentiment, clustering products, and generating helpful summaries for marketing and product teams.

---

## 🧪 Objectives

1. **Sentiment Classification**  
   Predict whether customer reviews are *positive*, *negative*, or *neutral* based on review text.

2. **Product Clustering**  
   Group products into meta-categories using semantic similarity.

3. **Review Summarization**  
   Summarize reviews (positive and negative) and generate product recommendations using generative AI.

4. **(Optional) Deployment**  
   Provide a simple interface for users to interact with the models.

---

## 📦 Dataset

- **Source**: Amazon Product Reviews and Metadata (fashion category)
- **Size Used**: 90,000 records (filtered down to ~237 clean reviews)
- **Main Fields**:  
  - `reviewText`  
  - `stars` (rating)  
  - `product_title`  
  - `category`, `features`, `description`

---

## 🔍 Methodology

### 1. 🔧 Preprocessing
- Loaded `.json.gz` files using `Polars` for fast lazy evaluation
- Filtered for fashion-related products
- Cleaned missing data, short/empty reviews, and duplicates
- Created `combined_category` and `product_context` for clustering

### 2. 🎯 Sentiment Classification
- Ground truth:  
  - 1–2 stars → Negative  
  - 3 stars → Neutral  
  - 4–5 stars → Positive
- Model used: `siebert/sentiment-roberta-large-english` (Hugging Face)
- Accuracy: **~95%**
- Evaluation: Classification report + Confusion matrix

### 3. 🧩 Product Clustering
- Sentence embeddings using `all-MiniLM-L6-v2`
- Grouped into **2 meta-categories** using `KMeans`
- Assigned human-readable cluster labels
- Visualized distribution with Seaborn

### 4. ✨ Text Summarization
- Used `facebook/bart-large-cnn` to summarize individual reviews
- Used OpenAI GPT-3.5 to consolidate summaries:
  - Top 3 product strengths & suggestions
  - Top negative feedback
  - Worst product per cluster and reason to avoid

---

## 📊 Results

- ✅ 237 cleaned and filtered reviews analyzed
- ✅ Reviews categorized into sentiment classes with high accuracy
- ✅ Products grouped into logical clusters (e.g., athletic wear vs casual wear)
- ✅ GPT-generated summaries helped extract actionable product insights

#### 📈 Classification Accuracy
