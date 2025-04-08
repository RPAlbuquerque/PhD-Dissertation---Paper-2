
# 📍 Consumer Mobility Dynamics

### **Paper 2 — _Pathways to Consumption: Physical Mobility, Digital Voice, and the Geography of Market Access_**

**Abstract:**  
This study investigates how physical consumer mobility influences retail sales, moderated by the digital sentiment expressed in geolocated tweets (e-WOM). Specifically, it explores:  
(1) the direct effect of mobility on sales;  
(2) how online discourse — measured via geolocated tweets — amplifies or mitigates this effect;  
(3) the asymmetric roles of positive and negative e-WOM.  
By combining spatial econometrics and machine learning, we propose new metrics to quantify sociotechnical consumption dynamics. These insights can inform more inclusive and data-driven marketing strategies, especially in underserved areas of emerging markets.

---

## 🚀 Getting Started

This repository contains all scripts and data pipelines to replicate the core analyses from the paper.

---

## 📦 Folder Structure

```bash
├── bloco_1_regex.py                 # Keyword filtering (raw tweet selection)
├── bloco_2_extracao.py             # Tweet extraction and keyword matching
├── bloco_3_validacao_bert.py       # Semantic validation using BERT (cosine similarity)
├── bloco_4_amostras_qualitativas.py# Qualitative sampling for validation
├── bloco_5_exploratoria.py         # Exploratory analysis of volume and sentiment
├── bloco_6_sentimento.py           # Sentiment scoring using Hugging Face
├── bloco_7_mapeamento_municipios.py# Mapping tweets to Brazilian municipalities
├── bloco_8_mapeamento_setores.py   # Mapping tweets to census tracts (setores censitários)
├── calculo_gewi.py                 # Computation of GEWI v1, v2, and v3 indices
├── visualizacao_gewis.py           # GEWI trend visualization
```

---

## 📋 Prerequisites

- Python 3.8+
- GPU support (optional, but recommended)
- Recomm. Environment: `JupyterLab` or `VSCode`

Main packages:

```bash
pandas
numpy
tqdm
shapely
matplotlib
seaborn
transformers
sentence-transformers
```

---

## 🧪 Pipeline Summary

The analysis consists of the following stages:

### 1. 🧹 Data Filtering and Preprocessing
- Apply regex patterns to identify tweets related to electrical materials and installation.
- Extract and normalize geotweets using multiprocessing and 64 cores.

### 2. 🧠 Semantic Validation (BERT)
- Use sentence transformers to calculate cosine similarity between tweets and predefined anchor phrases.
- Retain only tweets semantically aligned with consumer behavior.

### 3. 😃 Sentiment Analysis
- Apply pretrained BERT model for sentiment scoring (via Hugging Face).

### 4. 🌍 Geospatial Mapping
- Assign tweets to municipalities and census tracts via polygon matching.

### 5. ⚡ GEWI Index Computation
- **GEWI v1**: Basic sentiment-volume score:  
  `GEWI = s̄it × log(1 + nit)`
- **GEWI v2**: Positive vs. Negative polarity decomposition:  
  `GEWI⁺, GEWI⁻`
- **GEWI v3**: Influence-weighted index using follower count:  
  `GEWI = weighted_mean(score × log(1 + followers)) × log(1 + n)`

### 6. 📊 Visualization
- Time series plots of GEWI v1, v2 and v3.
- Tweet volume and semantic drift over time.

---

## 📈 Next Steps (In Progress)

- ✅ Add consumer mobility data (via SafeGraph or Logan dataset)  
- ✅ Integrate Tramontina Eletrik sales data by sector censitário  
- 🧪 Fit spatial models (SLM, SEM) and tree-based regressors (XGBoost, Random Forest)  
- 🧠 Model asymmetric effects (positive vs negative e-WOM)

---

## ✍️ Authors

- **Rafael Pereira Albuquerque** — PPGA/UFRGS & Harvard University - Center for Geographic Analysis  
- **Vinícius Brei** — PPGA/UFRGS & MIT Media Lab 
- **Devika Kakkar** - Harvard University - Center for Geographic Analysis
  
> For contact: rafaelpereiraalbuquerque@fas.harvard.edu

---

## 🎁 Acknowledgments

Special thanks to the Harvard CGA for access to the *Geotweet Archive v2.0*  
and to the broader research team who helped refine this project.
