# SkillWiser

## Overview
SkillWiser is a Python-based data analysis and visualization project designed to extract and analyze job market trends, particularly focusing on in-demand skills. The project utilizes Natural Language Processing (NLP) techniques and machine learning to clean job titles, extract skills from job descriptions, and cluster job roles based on their required skills.

## Poster
https://github.com/naikaishwarya23/SkillWiser/blob/main/poster.jpeg

## Features
- **Data Cleaning:** Cleans job titles to ensure consistency and remove unnecessary words.
- **Skill Extraction:** Uses Named Entity Recognition (NER) with spaCy to extract skills from job descriptions.
- **Data Visualization:** Generates bar charts and word clouds to display trends in hiring and skill demand.
- **Clustering:** Groups job roles based on extracted skills using TF-IDF and K-Means clustering.

## Installation
To run this project, install the required dependencies:

```bash
pip install spacy squarify pandas scikit-learn matplotlib seaborn numpy wordcloud
python -m spacy download en_core_web_md
```

## Dataset
The project uses a CSV file named `Postings.csv`, which contains job postings with relevant columns such as `job_title`, `company`, `job_summary`, etc.

## Usage
1. **Load the dataset**  
   ```python
   import pandas as pd
   df = pd.read_csv('Postings.csv')
   ```

2. **Clean job titles**  
   ```python
   df['cleaned_job_title'] = df['job_title'].apply(clean_job_title)
   ```

3. **Extract skills using NLP**  
   ```python
   df['extracted_skills'] = df['job_summary'].apply(extract_skills)
   ```

4. **Filter out irrelevant words**  
   ```python
   df['extracted_skills'] = df['extracted_skills'].apply(remove_words)
   ```

5. **Visualize skill trends**  
   ```python
   wordcloud = WordCloud(width=800, height=400, background_color='white').generate_from_frequencies(word_frequencies)
   plt.imshow(wordcloud, interpolation='bilinear')
   plt.axis('off')
   plt.show()
   ```

6. **Cluster job roles based on skills**  
   ```python
   vectorizer = TfidfVectorizer()
   X = vectorizer.fit_transform(df['skills_string'])
   kmeans = KMeans(n_clusters=5, random_state=42)
   df['cluster'] = kmeans.fit_predict(X)
   ```

## Results
- **Top Hiring Companies:** Displays the top 10 companies hiring in the dataset.
- **Most In-Demand Skills:** Uses a word cloud to highlight the top 20 skills in job postings.
- **Clustered Job Titles:** Groups similar job roles based on their required skills.

## Future Enhancements
- Expand skill extraction to include domain-specific terminologies.
- Integrate a job recommendation system based on extracted skills.
- Improve clustering with advanced NLP techniques like BERT embeddings.

## Contributors
- **Aishwarya Naik**


