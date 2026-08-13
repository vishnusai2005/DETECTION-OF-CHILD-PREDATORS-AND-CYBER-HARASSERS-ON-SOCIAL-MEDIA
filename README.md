<div align="center">

# 🛡️ Detection of Child Predators & Cyber Harassers on Social Media

### An NLP-powered system for flagging toxic, aggressive & predatory language patterns on social platforms

[![Python](https://img.shields.io/badge/Python-3.14-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-Classifier-EB5E28?style=flat-square)](https://xgboost.readthedocs.io/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-TF--IDF-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![NLTK](https://img.shields.io/badge/NLTK-NLP-3776AB?style=flat-square)](https://www.nltk.org/)
[![Status](https://img.shields.io/badge/Status-Active%20Development-brightgreen?style=flat-square)]()
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)]()

</div>

---

## 🎯 Problem Statement

Social media platforms see millions of interactions every day — and a meaningful fraction of them are abusive, aggressive, or predatory in nature, disproportionately harming minors and vulnerable users. Manual moderation cannot scale to this volume. This project is a **final-year academic initiative** aimed at building an automated pipeline capable of identifying **cyber harassment, online aggression, and predatory conversational patterns**, laying the groundwork for safer social platforms.

The current phase focuses on the **core NLP classification engine**: a text-based harmful-content detector trained on a large, diverse corpus of real-world labeled social media data. This engine is the foundation on top of which predator/grooming-specific detection (conversation-level context, code-mixed language support, etc.) is being built.

---

## 🧠 Approach & Methodology

### 1. Data Aggregation
Combined **8 independent, publicly available datasets** covering different flavors of online harm — aggression, personal attacks, general toxicity, racism, sexism, and platform-specific abuse (Twitter, YouTube, Kaggle) — into a single unified corpus of **~4.49 lakh (448,874) labeled text samples**.

| Dataset | Focus Area |
|---|---|
| `aggression_parsed_dataset` | Aggressive language |
| `attack_parsed_dataset` | Personal attacks |
| `kaggle_parsed_dataset` | General toxic comments |
| `toxicity_parsed_dataset` | Toxicity detection |
| `twitter_parsed_dataset` | General Twitter abuse |
| `twitter_racism_parsed_dataset` | Racist content |
| `twitter_sexism_parsed_dataset` | Sexist content |
| `youtube_parsed_dataset` | YouTube comment abuse |

### 2. Text Preprocessing
- Lowercasing + regex-based cleanup (URLs, mentions, punctuation stripped)
- Stopword removal using **NLTK**
- Produces a `cleaned_text` field used for all downstream modeling

### 3. Feature Engineering
- **TF-IDF vectorization** with unigrams + bigrams (`ngram_range=(1,2)`)
- Top 5,000 features, sublinear TF scaling for better handling of skewed term frequencies

### 4. Modeling
- **Stratified 80/20 train-test split** to preserve class balance across splits
- **XGBoost Classifier** tuned with `scale_pos_weight` to counter class imbalance (harmful content is the minority class)
- Hyperparameters: `n_estimators=250`, `max_depth=7`, `learning_rate=0.08`, `colsample_bytree=0.8`

---

## 📊 Results

Evaluated on a held-out test set of **89,775 samples**:

| Metric | Non-Harmful (0) | Harmful (1) |
|---|---|---|
| Precision | 0.96 | 0.62 |
| Recall | 0.93 | 0.75 |
| F1-Score | 0.95 | 0.67 |

**Overall Accuracy: 91%** &nbsp;|&nbsp; **Weighted F1: 0.91**

> The model is deliberately tuned to favor **recall on the harmful class (75%)** — in a content-moderation context, missing genuinely harmful content is far costlier than a false alarm.

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python |
| Data Handling | Pandas, NumPy |
| NLP | NLTK, Scikit-learn (TF-IDF) |
| Modeling | XGBoost |
| Visualization | Matplotlib, Seaborn |
| Environment | Jupyter Notebook |

---

## 📁 Repository Structure

```
DETECTION-OF-CHILD-PREDATORS-AND-CYBER-HARASSERS-ON-SOCIAL-MEDIA/
├── Final-year-project.ipynb   # End-to-end pipeline: data merge → preprocessing → TF-IDF → XGBoost → evaluation
└── README.md
```

> 📌 Raw dataset CSVs are not tracked in this repo due to size — see [Getting Started](#-getting-started) below.

---

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/vishnusai2005/DETECTION-OF-CHILD-PREDATORS-AND-CYBER-HARASSERS-ON-SOCIAL-MEDIA.git
cd DETECTION-OF-CHILD-PREDATORS-AND-CYBER-HARASSERS-ON-SOCIAL-MEDIA

# Install dependencies
pip install nltk xgboost pandas numpy scikit-learn matplotlib seaborn

# Launch the notebook
jupyter notebook Final-year-project.ipynb
```

Place the 8 source CSV files in the project root before running (see table above for filenames).

---

## 🗺️ Roadmap

- [ ] Conversation-level (multi-turn) grooming pattern detection, not just single-message toxicity
- [ ] Extend to **Telugu / Tenglish code-mixed** text for regional-language coverage
- [ ] Ensemble with Naive Bayes / Random Forest for comparison against XGBoost baseline
- [ ] Deploy as a lightweight API for real-time moderation demos
- [ ] Explainability layer (SHAP) to surface *why* content was flagged

---

## 👤 Author

**Vydhyam Vishnusai**
Final-year B.Tech CSE (AI & ML), Mohan Babu University

[![GitHub](https://img.shields.io/badge/GitHub-vishnusai2005-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/vishnusai2005)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-vishnusai--vydhyam-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/vishnusai-vydhyam)
[![Hugging Face](https://img.shields.io/badge/🤗%20Hugging%20Face-v2005-FFD21E?style=flat-square)](https://huggingface.co/v2005)
[![X](https://img.shields.io/badge/X-@VishnusaiSaii-000000?style=flat-square&logo=x&logoColor=white)](https://x.com/VishnusaiSaii)

---

<div align="center">

