# AI-Powered Resume Ranking System

## Overview
This project calculates a **similarity index** between a candidate's resume and a job description and ranks resumes by relevance. The pipeline performs:

- **Text extraction** (PDF / DOCX → raw text)  
- **Tokenization** (break text into tokens/words)  
- **Vectorization** (convert text to numeric vectors using TF-IDF)  
- **Similarity calculation** (cosine similarity between vectors)

The final output is a numerical similarity score (0–1) that represents how closely a resume matches the job description.

---

## 🔍 How the Similarity Calculation Works

### 1. Text Extraction
The system extracts text from resumes and job descriptions using:
- **PyPDF2** (for PDF files)  
- **python-docx** (for DOCX files)

---

### 2. Tokenization
The extracted text is split into tokens (words) using **spaCy**, which also supports:
- stopword removal  
- lemmatization  
- normalization  

---

### 3. Vectorization (TF-IDF)
The tokenized text is converted into numerical feature vectors using `TfidfVectorizer` from **scikit-learn**.

```python
from sklearn.feature_extraction.text import TfidfVectorizer

vectorizer = TfidfVectorizer()
tfidf_matrix = vectorizer.fit_transform([resume_text, job_description])
