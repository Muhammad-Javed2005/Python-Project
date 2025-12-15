# Movie Recommendation System

![Project Status](https://img.shields.io/badge/Status-Completed-green)
![Python](https://img.shields.io/badge/Python-3.11-blue)
![Libraries](https://img.shields.io/badge/Libraries-Pandas,NumPy,Scikit--Learn-yellow)
![License](https://img.shields.io/badge/License-MIT-blue)

---

## **Project Overview**

**This project is developed by Engr. Muhammad Javed.**

A **content-based movie recommendation system** built using Python.  
The system predicts similar movies based on movie **metadata** such as genres, keywords, cast, crew, and overview.

Key Highlights:  

- **Data preprocessing:** Cleaning, selecting relevant columns, converting JSON text fields to lists
- **Feature Engineering:** Tags column combining overview, genres, keywords, cast, and crew
- **Text Vectorization:** Using `CountVectorizer` for feature extraction
- **Similarity Calculation:** Cosine similarity on vectorized tags
- **Movie Recommendation:** Function to fetch top 5 similar movies
- **Persistence:** `pickle` files to save processed dataset and similarity matrix for fast prediction

---

## **Dataset**

- `tmdb_5000_movies.csv` — Contains movie metadata  
- `tmdb_5000_credits.csv` — Contains cast and crew information  

### **Selected Columns Used in Model**

- `movie_id`  
- `title`  
- `overview`  
- `genres`  
- `keywords`  
- `cast`  
- `crew`  

---

## **Project Structure**

Movie-Recommendation/
│
├── tmdb_5000_movies.csv
├── tmdb_5000_credits.csv
├── movie_list.pkl
├── similarity.pkl
├── Movie_Prediction.ipynb
├── app.py
├── style.css
└── README.md



---

## **Core Functions**

| Function | Purpose |
|----------|---------|
| `convert(text)` | Converts JSON string to Python list |
| `convert3(text)` | Extracts top 3 items from list |
| `fetch_director(text)` | Extracts director names |
| `collapse(L)` | Removes spaces from strings in a list |
| `recommend(movie)` | Returns top 5 similar movies |
| `pickle.dump()` | Saves processed dataset and similarity matrix |

---

## **How It Works**

1. **Load dataset** and merge movies with credits on `title`.  
2. **Select relevant columns**: `movie_id`, `title`, `overview`, `genres`, `keywords`, `cast`, `crew`.  
3. **Convert JSON text columns** to lists (`genres`, `keywords`, `cast`, `crew`).  
4. **Clean data** by removing spaces and splitting overview text.  
5. **Create tags** column combining all features.  
6. **Vectorize tags** using `CountVectorizer` (max_features=5000, stop_words='english').  
7. **Compute cosine similarity** matrix from vectorized tags.  
8. **Recommend movies** using the `recommend()` function.  
9. **Save dataset and similarity matrix** using `pickle` for fast retrieval in the app.

---

## **Usage Example**

```python
import pickle

# Load dataset and similarity matrix
movies = pickle.load(open('movie_list.pkl','rb'))
similarity = pickle.load(open('similarity.pkl','rb'))


# Recommend movies
def recommend(movie):
    index = movies[movies['title'] == movie].index[0]
    distances = sorted(list(enumerate(similarity[index])), reverse=True, key=lambda x: x[1])
    for i in distances[1:6]:
        print(movies.iloc[i[0]].title)

recommend("Avatar")


```

## **Contact**
LinkedIn: [Muhammad Javed](https://www.linkedin.com/in/muhammad-javed-24b262369/)
Email: muhammadjaved.tech5@gmail.com
GitHub: [Muhammad-Javed2005](https://github.com/Muhammad-Javed2005)

