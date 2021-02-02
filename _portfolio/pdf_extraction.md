---
title: "NLP on PDF Data "
excerpt: "School violence pdfs clustering "
header:
  teaser: /assets/images/documents.jpg
gallery:
  - url: assets/images/all.png
    image_path: assets/images/all.png
    alt: "School Violence PDFs"
  - url: assets/images/topic1.png
    image_path: assets/images/topic1.png
    alt: "PDF files that clustered into court record category"
tags: 
  - PDF extraction
  - NLP
  - SpaCy
  - Text Clean
  - Tokenization
  - LDA
---

## Overview

- This is a series of works on analyze PDF files, each module and its function are listed below.
- All modules are integrated into streamlit app, which provide some selectable options
- **Local run**

    1. Clone repository to local doc
    
    2. Intall all the dependencies
        ```powershell
        pip install -r requirements.txt 
        ```
    3. Run streamlit app
        ```powershell
        streamlit run app.py
        ```
       
## 1. Import Data 
- Import from folder: using pypdf2 to conduct text extraction, might not be accurate but quite fast.
- Import from file: read csv/pickle type files that have include text data inside.
 
## 2. Data Preparation
- Including clean puncatuation, remove stop word, and lemmatization.
- Tokenization(considering bigrams).
- Using spaCy to do POS filteration.(e.g. NOUN, ADJ, VERB...etc)

## 3. Topic Clustering 
- 1.Using bag of words to conduct LDA
- 2.Using Tf-idf to conduct LDA

## 4. Visualize 🚧 
- 1.Coherence value
- 2.Wordcloud

{% include gallery caption="Left: word cloud of all PDF (hard to interpret), Right: 1st cluster's word cloud (can be interpret as court record)" %}

## Links
[Github](https://github.com/scleeza/pdf_clustering)