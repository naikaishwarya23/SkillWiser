# SkillWiser: Job Posting Skill Analysis with SpaCy and TF-IDF

## Overview
`SkillWiser.ipynb` is a data science project designed to analyze job postings, extract skills using SpaCy's Named Entity Recognition (NER), cluster job roles based on skill similarity using TF-IDF and KMeans, and visualize insights. This notebook processes job data from `Postings.csv`, cleans job titles, identifies key skills, and provides clustering-based analysis and visualizations.

- **Original Colab File**: [Google Colab Link](https://colab.research.google.com/drive/1lG-EzWqxYcfslN4jj5Sc7Y2MYO8PT_So)
- **Generated**: Automatically by Colab on March 06, 2025 (based on current date).

## Poster
![SkillWiser Poster](https://images.unsplash.com/photo-1516321318423-f06f85e504b3?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80)  
*Replace this placeholder with your own poster link (e.g., hosted on Google Drive or GitHub).*

## Key Components

### 1. Setup
- **Libraries Installed**:
  - `spacy`: For NER and text processing.
  - `en_core_web_md`: SpaCy’s medium English model.
  - `squarify`: (Unused in this version but installed).
- **Dependencies**: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `wordcloud`.

### 2. Data Loading
- **Source**: `Postings.csv` (expected columns: `job_title`, `company`, `job_summary`).
- **Preprocessing**: 
  - Missing `job_summary` values filled with "EDA".
  - Job titles cleaned to remove numbers, special characters, and unnecessary words (e.g., "senior", "remote").

### 3. Skill Extraction
- **Method**: SpaCy NER extracts entities labeled `ORG`, `PRODUCT`, `LANGUAGE`, or `SKILL`.
- **Filtering**: 
  - Excludes job titles and irrelevant terms (e.g., "data scientist", "manager").
  - Replaces "microsoft" with "Azure" and "bi" with "Power BI".
  - Keeps skills appearing >15 times; removes stopwords from `ExplicitStopWords.txt`.

### 4. Clustering
- **Vectorization**: TF-IDF on skill strings (max 10 features).
- **Algorithm**: KMeans with 5 clusters.
- **Evaluation**: Silhouette Score and Calinski-Harabasz Index.

### 5. Visualizations
- **Bar Chart**: Top 10 companies by job postings.
- **Word Cloud**: Top 30 skills.
- **t-SNE**: 2D cluster visualization.
- **Lollipop Chart**: Top 5 job titles by frequency.
- **Radar Charts**: Skill profiles for top 5 job titles.

### 6. Analysis Functions
- **`get_top_skills_for_job`**: Returns top skills for a job title based on TF-IDF scores within its cluster.
- **`get_similar_job_titles`**: Identifies similar job titles in the same cluster.

## Getting Started

### Prerequisites
- **Environment**: Google Colab (recommended) or local Python setup.
- **Files**:
  - `Postings.csv`: Job postings dataset.
  - `ExplicitStopWords.txt`: Custom stopword list.
