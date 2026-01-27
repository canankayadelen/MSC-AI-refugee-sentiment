# MSC-AI-refugee-sentiment
MSc AI dissertation code: refugee inflows and media sentiment analysis

# MSc AI – Refugee Inflows and Media Sentiment Analysis

This repository contains the code developed for my MSc Artificial Intelligence dissertation at Kingston University.

The project applies machine learning (ML) and natural language processing (NLP) methods to analyse refugee inflows and media sentiment across Germany, Turkey, and the United Kingdom over the period 2019–2023.
The focus of the work is analytical and methodological rather than predictive, with particular attention to transparency, reproducibility, and data limitations.

---

## Project Overview

The dissertation consists of two independent analytical components:

### 1. Machine Learning (ML)

The ML component models annual refugee inflows using regression techniques applied to UNHCR administrative data.  
Due to the extremely small dataset size (five annual observations per country), the emphasis is on model behaviour, interpretability, and limitations rather than forecasting accuracy.

The ML analysis is descriptive and exploratory. It does not aim to produce a deployable prediction system.

### 2. Natural Language Processing (NLP)

The NLP component analyses media sentiment in news articles using transformer-based sentiment analysis.  
Sentiment is inferred at sentence level and aggregated to yearly, country-level trends to examine how media discourse evolves over time.

The ML and NLP components are analysed separately and aligned only at the interpretation stage.  
No causal relationship between sentiment and refugee inflows is assumed or modelled.

---

├── NLP_Refugee_Sentiment_2019_2023.ipynb
├── ML_Refugee_Inflows_2019_2023.ipynb
├── requirements.txt
├── README.md


---

## Data Sources

### Machine Learning Data

- Annual refugee inflow statistics obtained from the **UNHCR Data Finder**
- Publicly available administrative data
- Aggregated at country-year level

### NLP Data (Licensed)

- News articles collected from **LexisNexis**
- Languages: English, German, Turkish
- Balanced sampling: 250 articles per country per year

### Important Note on Data Availability

LexisNexis data is subject to licensing restrictions and cannot be redistributed publicly.  
For this reason, the raw news articles are **not included** in this repository.

Users wishing to reproduce the NLP analysis must obtain their own licensed access to LexisNexis (or an equivalent news database) and place the documents in the expected folder structure described in the notebooks.

All preprocessing steps, sentiment computation logic, and aggregation procedures are fully documented in the code and in the dissertation.

---

## NLP Methodology Summary

- Transformer-based sentiment analysis using pre-trained language models
- Sentence-level sentiment inference
- Probabilistic sentiment outputs (positive / neutral / negative, depending on language)
- Continuous sentiment score computed as: sentiment_score = p_positive − p_negative


- Sentiment scores are averaged across sentences, articles, and years
- Z-normalised probabilities are used as a robustness check to account for model- and language-specific calibration differences

Explicit n-gram features are **not** used for sentiment modelling.  
N-grams appear only in TF–IDF analysis for descriptive and interpretative purposes.

---

## ML Methodology Summary

- Regression modelling of annual refugee inflows
- Extremely small dataset: five observations per country
- Models used:
  - Linear Regression (baseline)
  - Decision Tree Regressor (with constrained depth)
  - Random Forest Regressor (limited ensemble)

The only input feature is **Year**, and the target variable is **annual refugee inflow**.  
Model simplicity is a deliberate methodological choice to minimise overfitting.

---

## Reproducibility

- All analysis was conducted in Python using Jupyter notebooks
- Processing steps, model parameters, and evaluation logic are explicitly defined
- Figures used in the dissertation are reproducible given access to the original data sources

Due to licensing restrictions on the NLP data, full end-to-end reproduction requires independent access to LexisNexis.

---

## Requirements

Main Python dependencies include:

- pandas  
- numpy  
- scikit-learn  
- matplotlib  
- transformers  
- torch  
- python-docx  

Install dependencies using:

```bash
pip install -r requirements.txt


How to Run
1) Install the required Python packages
2) Open the notebooks using Jupyter Notebook or Google Colab
3) Run cells sequentially

For the NLP notebook, users must provide their own licensed news article data in order to execute the full pipeline.

Disclaimer
This repository is provided for academic examination and reproducibility assessment purposes only.
The project is descriptive and analytical in nature and does not aim to produce a deployed predictive system or make causal claims regarding refugee inflows or media sentiment.
Author

Canan Kayadelen
MSc Artificial Intelligence
Kingston University


## Repository Structure

