# 🎬 Movie Recommender System

A **Content-Based Movie Recommendation System** built using **Machine Learning, Python, Streamlit, and the TMDB API**.

The application allows users to select a movie and get **5 similar movie recommendations** along with their posters.

---

## 🚀 Live Demo

🔗 **Live Application:**  
https://movies-recommender-system0.streamlit.app/

🔗 **GitHub Repository:**  
https://github.com/AmanSheikh7867/Movies-Recommender-system

---

## 📌 Project Overview

This project is an end-to-end **Machine Learning based Movie Recommendation System**.

The user selects a movie from the dropdown, and the system analyzes the movie's content features to find other movies that are most similar to it.

The similarity between movies is calculated using **Cosine Similarity** on numerical movie feature vectors.

After finding the most similar movies, the application uses the **TMDB API** to fetch their posters and displays the top 5 recommendations through a Streamlit web interface.

---

## 🎯 Objective

The main objective of this project was to understand how a Machine Learning recommendation system can be built from movie data and converted into a functional, interactive, and deployed web application.

The project follows an end-to-end workflow:

```text
Movie Dataset
      ↓
Data Preprocessing
      ↓
Feature Engineering
      ↓
Text Representation
      ↓
CountVectorizer
      ↓
Movie Feature Vectors
      ↓
Cosine Similarity
      ↓
Similarity Ranking
      ↓
Top 5 Recommendations
      ↓
TMDB API
      ↓
Movie Posters
      ↓
Streamlit Web App
      ↓
Deployment
```

---

## 🧠 Recommendation Approach

This project uses a **Content-Based Recommendation System**.

A content-based recommender recommends items based on the similarity of their features.

Relevant movie information is combined to represent each movie. Examples include:

- Genres
- Keywords
- Cast
- Crew
- Other relevant movie-related features

The combined information is transformed into numerical vectors and compared mathematically.

---

## ⚙️ How It Works

### 1. Data Preprocessing

The movie dataset is cleaned and prepared for the recommendation system.

Relevant movie information is selected and prepared for feature engineering.

### 2. Feature Engineering

Important movie features are combined into a single text-based representation.

For example, a movie can be represented using information such as:

```text
Action Adventure Crime Actor_Name Director_Name ...
```

This creates a combined representation of the movie's characteristics.

### 3. Text Vectorization

`CountVectorizer` from Scikit-learn converts the combined text representation into numerical vectors.

Conceptually:

```text
Movie A → [1, 0, 1, 0, 1, ...]
Movie B → [1, 1, 0, 0, 1, ...]
Movie C → [0, 1, 1, 1, 0, ...]
```

Each movie is represented as a numerical feature vector based on the vocabulary created from the movie data.

### 4. Cosine Similarity

Cosine Similarity is used to measure how similar two movie vectors are.

Conceptually:

```text
Selected Movie
      ↓
Feature Vector
      ↓
Compare with all movie vectors
      ↓
Cosine Similarity
      ↓
Similarity Scores
      ↓
Sort by Similarity
```

Movies with higher similarity scores are considered more similar according to the chosen feature representation.

### 5. Recommendation

The similarity scores are sorted in descending order.

The selected movie itself is skipped, and the next **5 most similar movies** are returned.

### 6. TMDB API Integration

The recommended movies are associated with their movie IDs.

The **TMDB API** is used to retrieve movie information and poster paths.

The poster URL is then constructed and displayed in the Streamlit application.

### 7. Streamlit Application

The recommendation system is wrapped inside a Streamlit web application.

The user can:

1. Select a movie.
2. Click **Show Recommendation**.
3. View 5 similar movies.
4. View their posters.

---

## ✨ Features

- 🎬 Interactive movie selection
- 🤖 Content-based movie recommendations
- 🧠 Machine Learning based similarity calculation
- 📊 Cosine Similarity based ranking
- 🎞️ Top 5 movie recommendations
- 🖼️ Dynamic movie posters using TMDB API
- ⚡ Interactive Streamlit interface
- 🌐 Publicly deployed web application
- 🔐 API key managed using Streamlit Secrets
- 📦 Large similarity matrix managed using Git LFS

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data manipulation and preprocessing |
| NumPy | Numerical operations |
| Scikit-learn | Machine Learning and text vectorization |
| CountVectorizer | Converting movie text into numerical vectors |
| Cosine Similarity | Measuring movie similarity |
| Streamlit | Building the web application |
| Requests | Sending API requests |
| TMDB API | Fetching movie information and posters |
| Pickle | Saving and loading processed data and similarity matrix |
| Git | Version control |
| GitHub | Source code hosting |
| Git LFS | Managing the large similarity matrix |

---

## 📂 Project Structure

```text
Movies-Recommender-system/
│
├── .streamlit/
│   └── secrets.toml          # Local API secret - not uploaded to GitHub
│
├── app.py                    # Main Streamlit application
├── movies.pkl                # Processed movie dataset
├── similarity.pkl            # Precomputed movie similarity matrix
├── requirements.txt          # Python dependencies
├── .gitignore                # Ignored files and secrets
├── .gitattributes            # Git LFS configuration
└── README.md                 # Project documentation
```

---

## 💻 Run the Project Locally

### 1. Clone the repository

```bash
git clone https://github.com/AmanSheikh7867/Movies-Recommender-system.git
```

### 2. Move into the project directory

```bash
cd Movies-Recommender-system
```

### 3. Create a virtual environment

```bash
python -m venv .venv
```

### 4. Activate the virtual environment

For Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

### 5. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 6. Configure the TMDB API key

Create:

```text
.streamlit/secrets.toml
```

Add:

```toml
TMDB_API_KEY = "YOUR_TMDB_API_KEY"
```

Do **not** upload `secrets.toml` or your API key to GitHub.

### 7. Run the application

```bash
streamlit run app.py
```

The application will be available at:

```text
http://localhost:8501
```

---

## 🔐 API Key Security

The TMDB API key is not hard-coded into the application.

The application accesses the key using Streamlit Secrets:

```python
st.secrets["TMDB_API_KEY"]
```

For local development, the key is stored in:

```text
.streamlit/secrets.toml
```

The secret file is excluded from Git using `.gitignore`.

For Streamlit Community Cloud, the secret is added through the application's **Secrets** settings instead of being committed to GitHub.

---

## 🌐 Deployment

This application is deployed using **Streamlit Community Cloud**.

Deployment workflow:

```text
Local Development
       ↓
Git
       ↓
GitHub
       ↓
Streamlit Community Cloud
       ↓
Live Application
```

The project uses **Git LFS** to manage `similarity.pkl`, which is a large model artifact.

---

## 📦 Git LFS

The `similarity.pkl` file contains the precomputed similarity matrix used by the recommendation system.

Because the file is larger than GitHub's regular file-size limit, it is managed using **Git Large File Storage (Git LFS)**.

Git LFS allows the large model artifact to remain part of the project while being stored and transferred separately from normal Git objects.

---

## 🔍 Core Machine Learning Concepts

### CountVectorizer

`CountVectorizer` converts text into a numerical representation based on the words/features present in the movie data.

For example:

```text
Movie A → Action Adventure Hero
Movie B → Action Hero Crime
```

These text representations can be converted into numerical vectors, making mathematical comparison possible.

### Cosine Similarity

Cosine Similarity measures the similarity between two vectors by comparing the angle between them.

In this project:

```text
Movie Feature Vectors
        ↓
Cosine Similarity
        ↓
Similarity Scores
        ↓
Highest Similarity
        ↓
Top Recommendations
```

This provides the ranking used by the recommendation function.

---

## 🧪 What I Practiced

This project helped me apply and understand:

- Data preprocessing
- Feature engineering
- Text preprocessing
- Text vectorization
- CountVectorizer
- Numerical vector representations
- Cosine Similarity
- Similarity matrices
- Content-Based Recommendation Systems
- Sorting and ranking recommendations
- Model/data serialization using Pickle
- API integration
- Streamlit application development
- API secret management
- Git and GitHub
- Git Large File Storage (Git LFS)
- Machine Learning deployment

---

## 🎓 What I Learned

Building this project helped me move from studying individual Machine Learning concepts to building a complete working application.

I learned how to:

- Work with real-world movie data
- Prepare and combine features for recommendation
- Convert text features into numerical vectors
- Measure similarity between items
- Build recommendation logic
- Integrate an external API
- Build an interactive web application
- Protect API credentials
- Manage a large ML artifact with Git LFS
- Push an ML project to GitHub
- Deploy a Machine Learning application

---

## 🎯 Project Goal

The goal of this project was to understand the complete lifecycle of a small Machine Learning product:

```text
Data
 ↓
Preprocessing
 ↓
Feature Engineering
 ↓
Machine Learning
 ↓
Recommendation Logic
 ↓
API Integration
 ↓
Application
 ↓
Deployment
```

This project focuses not only on building the recommendation logic, but also on turning it into a usable application that can be accessed through the web.

---

## 🔮 Future Improvements

Possible improvements for future versions include:

- Add movie descriptions
- Add ratings and release dates
- Add genre filters
- Add search functionality
- Add more movie information
- Improve the user interface
- Add recommendation explanations
- Add personalized recommendations
- Add multiple recommendation strategies
- Improve recommendation quality

---

## 🚀 Future Learning Direction

This project is part of my ongoing AI/ML learning journey.

My future projects will move toward:

```text
Machine Learning
      ↓
Deep Learning
      ↓
AI Applications
      ↓
LLM Applications
      ↓
RAG Systems
      ↓
Agentic AI
      ↓
End-to-End AI/ML Engineering
```

---

## 🙏 Acknowledgements

Movie information and poster images are obtained using the **TMDB API**.

This product uses the TMDB API but is not endorsed or certified by TMDB.

🔗 TMDB:  
https://www.themoviedb.org/

---

## 👨‍💻 Author

### Aman Sheikh

**Engineering Student | AI/ML Enthusiast**

🔗 **GitHub:**  
https://github.com/AmanSheikh7867

🔗 **Project Repository:**  
https://github.com/AmanSheikh7867/Movies-Recommender-system

🔗 **Live Application:**  
https://movies-recommender-system0.streamlit.app/

---

## ⭐ Project Support

If you found this project interesting, feel free to explore the repository and give it a ⭐ on GitHub.

---

## 📌 Project Summary

**Movie Recommender System** is an end-to-end Machine Learning project that uses a **Content-Based Recommendation approach, CountVectorizer, and Cosine Similarity** to recommend 5 similar movies based on their features.

The system integrates the **TMDB API** to dynamically fetch movie posters and is deployed as a live **Streamlit web application**.

The project demonstrates the complete workflow from **Machine Learning development to API integration, application development, Git/GitHub version control, Git LFS, and deployment**.
