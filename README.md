# IRMaster

Information Retrieval System based on TF-IDF, Vector Space Model (VSM), Cosine Similarity, Query Expansion, Voice Search, and Multilingual Retrieval.

---

# Project Overview

This project implements an Information Retrieval System capable of retrieving relevant documents from large datasets using text or voice queries. The system supports multilingual retrieval and provides ranking based on cosine similarity over TF-IDF document representations.

---

# Datasets

## Antique

* Documents: 404K
* Queries: 2.4K
* Qrels: 27K

Structure:

* Document → (id, text)
* Query → (id, query)
* Qrel → (query_id, doc_id, relevance, iteration)

## Wikir/en1k

* Documents: 370K
* Queries: 48K
* Qrels: 48K

Structure:

* Document → (id, text)
* Query → (id, query)
* Qrel → (query_id, doc_id, relevance, iteration)

---

# Preprocessing Pipeline

The following preprocessing operations are applied to both documents and queries:

1. Contraction Expansion
2. Tokenization
3. Punctuation Removal
4. Text Normalization

   * Date normalization
   * Number normalization
   * Acronym expansion
   * British/American spelling normalization
   * Unicode to ASCII conversion
5. Stemming using PorterStemmer
6. POS Tagging
7. Lemmatization using WordNetLemmatizer
8. Stop Words Removal

---

# Data Representation & Indexing

The system uses a Vector Space Model (VSM) with TF-IDF weighting.

TF-IDF Parameters:

* sublinear_tf = True
* norm = "l2"
* max_df = 0.9

---

# Query Processing

Queries undergo the same preprocessing pipeline as documents before retrieval.

---

# Query Matching & Ranking

1. Convert documents into TF-IDF vectors.
2. Convert query into a TF-IDF vector.
3. Compute cosine similarity between the query and all documents.
4. Rank documents in descending order.
5. Return the Top-K most relevant documents.

---

# Evaluation Metrics

The following evaluation measures are used:

* Precision@10
* Recall@10
* Mean Average Precision (MAP)
* Mean Reciprocal Rank (MRR)

---

# Results

## Antique Dataset

| Metric       | Value  |
| ------------ | ------ |
| MAP          | 0.1473 |
| MRR          | 0.0812 |
| Precision@10 | 0.0304 |
| Recall@10    | 0.1177 |

## Antique Dataset (After Clustering)

| Metric       | Value  |
| ------------ | ------ |
| MAP          | 0.5787 |
| MRR          | 0.2409 |
| Precision@10 | 0.0706 |
| Recall@10    | 0.1177 |

### Observation

Applying clustering significantly improved retrieval performance, especially MAP and MRR.

## Wikir/en1k Dataset

| Metric | Value  |
| ------ | ------ |
| MAP    | 0.5404 |
| MRR    | 0.6094 |

---

# Additional Features

## Multilingual Retrieval

Arabic queries are translated into English before retrieval and translated back to Arabic after retrieving results.

Google Translator API is used for translation.

## Voice Search

Users can search using voice input.

## Dataset Switching

Users can switch between available datasets from the interface.

## Language Switching

Users can perform searches in Arabic or English using either text or voice input.

---

# System Architecture

1. Read documents from dataset files.
2. Apply preprocessing operations.
3. Perform stemming and lemmatization.
4. Normalize and standardize text.
5. Build the TF-IDF matrix.
6. Represent documents and queries as vectors.
7. Compute cosine similarity.
8. Rank and retrieve the most relevant documents.

---

# User Interface

Add screenshots inside the screenshots folder and display them here.

## Main Interface

![Home](screenshots/home.png)

## Search Results

![Results](screenshots/results.png)

---

# Technologies Used

* Python
* NLTK
* Scikit-Learn
* NumPy
* Pandas
* Contractions
* Num2Words
* DateUtil
* AnyAscii
* Google Translator

---

# Installation

```bash
pip install -r requirements.txt
```

---

# References

* GeeksForGeeks
* GitHub
* Real Python
* ChatGPT

---

# Project Report

The full project report is available in the docs folder.
