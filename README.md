# 📚 Library Recommender System

This project builds a **content-based recommender system** for a library dataset.  
It recommends books to users based on the similarity of book content, metadata and user borrowing history.

---

## 🚀 Features
- **Content-based recommendations** using:
  - Book title + descriptions embedded with **Sentence-BERT** (`paraphrase-multilingual-MiniLM-L12-v2`)
  - Metadata features (author, publisher, category, published year, ratings)
- **Cosine similarity model** to compute book-to-book similarity
Idea 1: 
- **User profile vectors** built from borrowing history (average of borrowed book vectors)
- Generates **personalized book recommendations** for each user
idea 2:
-

---

## 📂 Project Structure
