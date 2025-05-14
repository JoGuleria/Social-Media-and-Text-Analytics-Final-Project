# Social-Media-and-Text-Analytics-Final-Project
Final Project For Social Media and Text Analytics: Craigslist Housing Listings: Smarter Search with NLP

## Overview

Craigslist is one of the most heavily used peer-to-peer classifieds platforms in the U.S., known for its minimalist interface and user-generated listings. However, this flexibility comes at the cost of structure, making search experiences inefficient—especially in high-traffic categories like **housing rentals**. Users searching for apartments often fail to find relevant results due to inconsistently phrased listings and a search system that relies purely on **literal keyword matching**.

Our project addresses this challenge by designing a **semantic search engine** powered by **Natural Language Processing (NLP)**, enabling Craigslist to retrieve results based on *meaning*, not just *exact wording*. This significantly improves discoverability, relevance, and overall user satisfaction in the housing section of the platform.

## Project Goals

* Bridge the gap between user queries and listing descriptions using **semantic modeling**
* Replace exact keyword matching with a **context-aware retrieval system**
* Improve the **precision and recall** of relevant listings without requiring changes to how listings are created
* Demonstrate scalability for deployment across other Craigslist categories (jobs, gigs, services)


## Dataset

We used the **Craigslist Housing Dataset (San Francisco Bay Area)** from Kaggle. After cleaning and preprocessing, we retained:

* **3,093 listings**
* Structured fields: `price`, `hood`, `brs`, `bath`, `sqft`
* Unstructured fields: `title`, `amenities`
* A new feature `full_text` was created by combining `title` and cleaned `amenities`

## Methodology

### 1. Data Preprocessing

* Filled missing values and removed malformed entries
* Applied regex cleaning to strip unwanted characters and symbols
* Lowercased all text and normalized formatting
* Combined `title` + `amenities` into a single searchable column: `full_text`

### 2. Baseline Model: TF-IDF + Cosine Similarity

* Implemented TF-IDF vectorization on the `full_text` column
* Compared user queries with listing vectors using cosine similarity
* Served as a benchmark for evaluating semantic search

### 3. Semantic Model: Sentence-BERT (SBERT)

* Used the `paraphrase-MiniLM-L6-v2` model from HuggingFace
* Transformed listings and user queries into 384-dimensional embeddings
* Retrieved top-N listings by computing cosine similarity between embeddings
* Outperformed TF-IDF in handling varied phrasing and conceptual matches

## Evaluation Strategy

To assess effectiveness, we compared three approaches:

| Method               | Precision\@5 |
| -------------------- | ------------ |
| Keyword Search       | 0.20         |
| TF-IDF + Cosine Sim. | 0.40         |
| Sentence-BERT        | **0.60**     |

### Key Findings:

* Sentence-BERT retrieved listings even when phrasing varied (e.g., "dogs allowed" vs. "pet-friendly")
* Semantic matching provided better context-awareness and result quality
* TF-IDF struggled with synonyms and alternate expressions

## Technical Stack

* **Languages**: Python
* **Libraries**: Pandas, Scikit-learn, Regex, Matplotlib, Seaborn
* **NLP Tools**: HuggingFace Transformers, Sentence-Transformers
* **Models Used**: `paraphrase-MiniLM-L6-v2`

## Results

* Successfully built a **context-aware search engine** for Craigslist housing listings
* Enabled users to search naturally using phrases like “2-bedroom near subway pet-friendly”
* Improved **discoverability** for listings that would otherwise be missed
* Preserved Craigslist’s minimalist, open-posting format while delivering smarter results

## Future Work

* **Dynamic Filters**: Enable filtering results by extracted attributes like budget, location, pet policies
* **Feedback Loop**: Use click-through rates or user votes to continuously improve ranking
* **Cross-Category Expansion**: Adapt semantic search for jobs, gigs, and services
* **Real-Time Deployment**: Pilot in beta cities like San Francisco or Seattle

## Impact & Value

This project demonstrates how **legacy platforms** like Craigslist can benefit from modern NLP techniques without overhauling their systems. By introducing **semantic search**, we:

* Improved user engagement and satisfaction
* Made better use of unstructured, user-generated content
* Built a scalable, low-maintenance architecture that can expand across domains


## Authors

**Team Group 3 — MSBA, University of Rochester**

* Harsh Joshi
* Jyotiraditya Guleria
* Shakyadeep Bhattacharya
* Diya Chouhan
* Esha Deo
* Parinita Soni


