<div align="center">

# 🧠 Mental Health Score — Student Wellness Analytics

[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Python](https://img.shields.io/badge/Python_3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Render](https://img.shields.io/badge/Render-46E3B7?style=for-the-badge&logo=render&logoColor=white)](https://render.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

<p align="center">
  <b>An end-to-end Machine Learning web application predicting student mental wellness scores (0–10) based on digital habits, lifestyle factors, and perceived stress levels.</b>
</p>

[🚀 Live Web App](https://mental-health-score-1-ew8o.onrender.com) • [🌐 Backend API](https://mental-health-score-p8x8.onrender.com) • [📖 Swagger Docs](https://mental-health-score-p8x8.onrender.com/docs) • [✨ Report Bug](https://github.com/) • [💡 Request Feature](https://github.com/)

</div>

---

## 🌟 Key Features

- 🎯 **Machine Learning Pipeline**: Trained using a `RandomForestRegressor` with custom `ColumnTransformer` preprocessing (logarithmic transforms, scaling, and ordinal/one-hot encodings).
- ⚡ **High-Performance REST API**: Built on **FastAPI** with strict **Pydantic** schema validation.
- 🎨 **Modern Interactive UI**:
  - Semi-circular dynamic SVG gauge meter with smooth easing animations.
  - Granular error diagnostics with automatic field-level validation feedback.
  - Polished editorial aesthetic with glassmorphism effects and modern typography (*Fraunces* + *Inter*).
- ☁️ **Cloud Native**: Pre-configured for seamless cloud deployment on Render.

---

## 🛠️ Tech Stack

| Domain | Technologies |
|---|---|
| **Backend & API** | FastAPI, Uvicorn, Pydantic |
| **Machine Learning** | Scikit-Learn, Joblib, NumPy, Pandas |
| **Frontend** | Vanilla JavaScript (ES6+), HTML5, CSS3 Tokens |
| **Data Exploration** | Jupyter Notebook, Matplotlib, Seaborn |
| **Cloud Deployment** | Render |

---

## 🏗️ Architecture & Model Pipeline

The ML pipeline applies specialized preprocessing per feature category before regression:

```mermaid
graph LR
    A[Raw Input Data] --> B[ColumnTransformer]
    B -->|Skewed: Study Hours| C[log1p + StandardScaler]
    B -->|Numeric: Age, Sleep, Unlocks| D[StandardScaler]
    B -->|Ordinal: Stress Level| E[OrdinalEncoder]
    B -->|Categorical: Gender, Platform, Country| F[OneHotEncoder]
    C --> G[RandomForestRegressor]
    D --> G
    E --> G
    F --> G
    G --> H[Mental Health Score 0 - 10]
```

---

## 📁 Repository Structure

```plaintext
├── Mental_Health_Model.pkl   # Serialized trained scikit-learn pipeline
├── dataset.csv               # Dataset with student lifestyle & mental health metrics
├── experiment.ipynb          # EDA, feature engineering, model training & tuning
├── index.html                # Responsive web app interface
├── main.py                   # FastAPI backend server & prediction endpoint
├── requirements.txt          # Python dependencies
├── script.js                 # Frontend application logic & API integration
├── style.css                 # Custom design system, layout, and animations
└── .gitignore                # Git ignore configuration
```

---

## 🚀 Quick Start (Run Locally)

### 1. Clone the repository
```bash
git clone https://github.com/your-username/Mental-Health-Score.git
cd Mental-Health-Score
```

### 2. Set up a virtual environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the FastAPI server
```bash
uvicorn main:app --reload
```
The backend will start at: `http://127.0.0.1:8000`

### 5. Launch the Web Interface
Simply open `index.html` in your favorite web browser, or serve it via Live Server.

---

## 🔌 API Reference

### Health Check
```http
GET /
```
**Response (200 OK):**
```json
{
  "message": "Mental Health Score Prediction API is running"
}
```

### Predict Mental Health Score
```http
POST /predict
Content-Type: application/json
```

#### Request Payload
```json
{
  "age": 21,
  "gender": "Male",
  "country": "India",
  "academic_level": "Undergraduate",
  "most_used_platform": "Instagram",
  "purpose_of_use": "Entertainment",
  "avg_daily_usage_hours": 4.5,
  "daily_unlocks": 120,
  "study_hours": 3.0,
  "physical_activity_hours": 1.5,
  "sleep_hours_per_night": 7.0,
  "stress_level": "Medium"
}
```

#### Response (200 OK)
```json
{
  "predicted_mental_health_score": 6.85
}
```

Interactive OpenAPI Swagger documentation is available at `/docs`.

---

## 📊 Score Interpretation Guide

| Score Band | Signal Label | Description |
|---|---|---|
| **0.0 – 3.9** | 🔴 *Signal: Strained* | Suggests elevated stress; habits indicate recovery adjustments are beneficial. |
| **4.0 – 6.9** | 🟡 *Signal: Balanced* | Steady daily rhythm with moderate resilience and room to reset. |
| **7.0 – 10.0** | 🟢 *Signal: Strong* | Balanced lifestyle habits pointing to a healthy baseline. |

---

## ⚠️ Disclaimer

> [!NOTE]  
> This project is designed strictly for **educational and analytical demonstration purposes**. The generated predictions are based on statistical habits and pattern regression, not a clinical psychiatric diagnosis. If you or someone you know is undergoing mental distress, please consult a certified healthcare professional.

---

<div align="center">
  <sub>Built with ❤️ for student wellness and open-source learning.</sub>
</div>
