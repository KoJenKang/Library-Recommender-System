# 📚 Library Recommender System

This project builds a **content-based recommender system** for a library dataset.  
It recommends books to users based on the similarity of book content, metadata and user borrowing history.

---

## 🚀 Features
- **Content-based recommendations** using:
  - Book title + descriptions embedded with **Sentence-BERT** (`paraphrase-multilingual-MiniLM-L12-v2`)
  - Metadata features (author, publisher, category, published year, ratings)
- **Cosine similarity model** to compute book-to-book similarity
### Idea 1: 
- **User profile vectors** built from borrowing history (average of borrowed book vectors)
- Generates **personalized book recommendations** for each user 
### idea 2:
- Get each reader's most recent borrowed book(s), then use the most recent borrowed book to do cosine similarity with other book.
- Recommend the top 5 similar books based on recent borrow history.

---

## ⚙️ Workflow
1. **Data Preprocessing**
   - Clean book information (handle missing values, extract publish year).
   - Extract embeddings from book title + content using:
     ```python
     from sentence_transformers import SentenceTransformer
     model = SentenceTransformer("paraphrase-multilingual-MiniLM-L12-v2")
     ```
   - Encode categorical metadata (author, publisher, category) using One-hot encoding
   - Normalize numeric features (ratings, number of scores, published year).

2. **Feature Engineering**
   - Concatenate embeddings with metadata features per book.

3. **Construct Similarity Computation functions**
   ### idea 1: 
   - Function is using **cosine similarity** and able to take a book_id, then output the top k similar books.
   ### idea 2:
   - Function is using **cosine similarity** and able to take a vetor(get from user profile by averaing the vectors of books they borrowed), then output the top k similar books.  

5. **User Profiling**
   - Aggregate borrowed book vectors to build an **average user vector**.
   - Recommend new books that are most similar to the user’s profile vector, excluding already borrowed ones.

---

## 🛠️ Tech Stack
- **Python** (pandas, numpy, scikit-learn)
- **NLP**:
  - [Sentence-BERT](https://www.sbert.net/) for multilingual embeddings  
    (`paraphrase-multilingual-MiniLM-L12-v2`)
- **Environment**: Jupyter Notebook / Google Colab

## ⭐ Application
- **API**: I wrapped it as a RESTful API using Pythonanywhere to be able to embedded onto the website
https://karenkang.pythonanywhere.com/recommend?book_id=

