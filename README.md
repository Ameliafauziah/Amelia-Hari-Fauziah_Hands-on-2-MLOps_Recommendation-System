# Amelia-Hari-Fauziah_Hands-on-2-MLOps_Recommendation-System

# Job Listing Recommendation System

## Project Overview

This project aims to build a **content-based recommendation system** that helps users discover relevant job listings based on the **job description text**. By analyzing the textual content of job postings, the system can suggest positions that are most similar in nature to a given role — improving job search efficiency and experience.

Rather than relying on job titles alone (which can be ambiguous or inconsistent), this system uses **natural language processing (NLP)** to understand what each job truly entails and matches listings based on the actual **descriptions**.

---

##  Methodology/Workflow

### 1. Text Vectorization using TF-IDF
I use **TF-IDF (Term Frequency-Inverse Document Frequency)** to convert job descriptions into numerical vectors. TF-IDF is chosen because:

- It reflects the **importance of words** in a document relative to a collection.
- It downplays commonly used words (e.g., "team", "job") and emphasizes **meaningful keywords** (e.g., "Python", "data analysis", "clinical trials").
- It is lightweight and effective for **sparse textual data** like job postings.

### 2. Measuring Similarity using Cosine Similarity
After vectorizing the descriptions, we use **cosine similarity** to measure how similar one job description is to another. Cosine similarity is ideal here because:

- It measures the **angle between two vectors**, not their magnitude — perfect for comparing text-based vectors.
- It ranges from 0 (no similarity) to 1 (identical), allowing easy ranking of recommendations.

---

##  How It Works

1. The system takes a **job title** as input (e.g., "Data Scientist").
2. It finds the associated **job description** in the dataset.
3. Using TF-IDF and cosine similarity, it calculates how close that description is to others.
4. It returns the top 5–10 and/or most similar job postings — including the job title, company, location, salary, and cleaned description.

The recommendations are based purely on the **semantic similarity of job descriptions**, not on job titles or categories.

---

## Example Output

If the user searches for `"Data Scientist"`, the system might return similar listings such as:

- Machine Learning Engineer at ABC Ltd. (with 0.78 similarity)
- Data Analyst at ABC Corp (0.64 similarity)
- AI Researcher at Startup X (0.61 similarity)

Each result includes relevant job metadata and the similarity score, offering transparency on how close the jobs are.

---

##  Reflections & Challenges

### Challenges Faced:

- **Text Quality & Noise**: Job descriptions varied in structure and length. Some were very short or generic, which reduced model effectiveness.
- **Missing Values**: Some descriptions were null or poorly formatted, which required preprocessing and imputation (`fillna('')`).
- **Ambiguous Job Titles**: Many positions had the same or similar titles but very different responsibilities.

### How I Addressed Them:

- **Preprocessing**: Cleaned the text with normalization techniques and removed stopwords.
- **Vector Robustness**: Used TF-IDF for its ability to handle sparse, high-dimensional data.
- **Index Mapping**: Built a case-insensitive index mapping to ensure flexibility in job title search.

---

##  File Outputs

- `TFIDF_Vectorized.csv` – Matrix of TF-IDF features per job description.
- `cosine_similarity_matrix.json` *(optional)* – Pairwise similarity values between all job listings.
- `recommendations_output.csv` – Job listings recommended for a given query.

---

## Future Improvements

- Integrate user feedback to refine recommendations.
- Add filters by location, salary range, or industry.
- Combine with collaborative filtering or hybrid models for better personalization.

---

*Built with passion for data-driven career discovery.*
