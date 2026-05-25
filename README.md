# 🧠 Text Mood Predictor – Mental Stress Detection System

A powerful machine learning-based system that analyzes text data to predict mental stress levels with high accuracy. Whether you're analyzing journal entries, social media posts, survey responses, or other written content, this tool identifies stress patterns using advanced NLP and multiple classification algorithms.

---

## 📌 Overview

**Text Mood Predictor** is an end-to-end machine learning pipeline designed to:
- Process raw text data and extract meaningful features
- Train multiple classification models simultaneously
- Automatically identify the best-performing model
- Make real-time stress level predictions on new text inputs

The system classifies stress into three categories:
- 🟢 **Low Stress**
- 🟡 **Medium Stress**  
- 🔴 **High Stress**

---

## ✨ Key Features

### Data Processing
- **📥 CSV Data Loading** – Seamlessly read and process training data from CSV files
- **🧹 Intelligent Text Preprocessing** – Tokenization, lowercasing, punctuation removal, and stopword elimination
- **📚 Lemmatization** – Normalize words to their base forms for better pattern recognition

### Feature Engineering
- **🔠 TF-IDF Vectorization** – Convert text into numerical features weighted by importance
- **📊 Scalable Feature Extraction** – Handles variable-length documents efficiently

### Machine Learning Models
Trained and evaluated models include:
- 🌲 **Random Forest** – Ensemble-based classification
- 📈 **Logistic Regression** – Probabilistic linear classifier
- 🎯 **Support Vector Machine (SVM)** – Kernel-based classifier
- 🧮 **Naive Bayes** – Probabilistic classifier
- 🚀 **Gradient Boosting** – Iterative ensemble method

### Model Evaluation & Selection
- **🏆 Automatic Best Model Selection** – Compares all models and picks the highest performer
- **📊 Confusion Matrix** – Visualize true/false positives and negatives
- **📋 Classification Report** – Precision, recall, F1-score, and support metrics
- **🔍 Feature Importance Analysis** – Identify which text patterns matter most

### Real-Time Predictions
- **💬 On-the-Fly Inference** – Predict stress levels for any input text instantly
- **🎯 Confidence Scores** – Understand prediction confidence levels

---

## 🛠️ Technical Stack

| Component | Technology |
|-----------|-----------|
| **Language** | Python 3.x |
| **NLP Processing** | NLTK |
| **Machine Learning** | Scikit-learn |
| **Data Handling** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |

---

## 📂 Project Structure

```
textmoodpredictor/
├── README.md                    # This file
├── data/
│   └── stress_data.csv         # Training dataset
├── models/
│   └── best_model.pkl          # Saved trained model
├── src/
│   ├── preprocessing.py        # Text cleaning & preprocessing
│   ├── feature_extraction.py   # TF-IDF vectorization
│   ├── model_training.py       # Model training & evaluation
│   └── prediction.py           # Real-time prediction functions
└── notebooks/
    └── analysis.ipynb          # Exploratory data analysis
```

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy scikit-learn nltk matplotlib seaborn
```

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/omkorde13/textmoodpredictor.git
   cd textmoodpredictor
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Download NLTK data** (required for lemmatization)
   ```python
   import nltk
   nltk.download('punkt')
   nltk.download('wordnet')
   nltk.download('stopwords')
   ```

### Quick Start

#### Training the Model
```python
from src.model_training import train_and_evaluate

# Load your dataset
df = pd.read_csv('data/stress_data.csv')

# Train all models and automatically select the best one
best_model, results = train_and_evaluate(df)
```

#### Making Predictions
```python
from src.prediction import predict_stress

# Predict stress level for a single text
text = "I feel overwhelmed with all the deadlines"
stress_level, confidence = predict_stress(text, best_model)

print(f"Stress Level: {stress_level}")
print(f"Confidence: {confidence:.2%}")
```

---

## 📊 Model Performance

After training on your dataset, the system provides:
- **Overall Accuracy** across all stress categories
- **Precision & Recall** per stress level
- **F1-Score** balancing precision and recall
- **Confusion Matrix** showing prediction patterns

Example output:
```
                precision    recall  f1-score   support
    Low Stress       0.92      0.88      0.90       120
Medium Stress       0.85      0.87      0.86       150
  High Stress       0.89      0.92      0.91       130

    accuracy                           0.89       400
   macro avg        0.89      0.89      0.89       400
weighted avg        0.89      0.89      0.89       400
```

---

## 📈 Feature Importance

The system identifies which words and phrases are most indicative of stress:
- Visualizes top features by TF-IDF weight
- Helps understand stress patterns in your data
- Enables domain-specific insights

---

## 📋 Data Format

Your training CSV should have at least these columns:

| Column | Description | Example |
|--------|-------------|---------|
| `text` | Input text for analysis | "I can't handle this pressure" |
| `stress_level` | Target label | "High" |

```csv
text,stress_level
"I feel great today",Low
"Feeling a bit overwhelmed",Medium
"This is unbearable",High
```

---

## 🔧 Configuration

Key hyperparameters can be adjusted in the training script:
- **TF-IDF max_features**: Number of features to extract
- **Test split ratio**: Proportion of data for testing
- **Model hyperparameters**: Adjust individual model parameters
- **Random seed**: For reproducible results

---

## 📚 How It Works

1. **Data Preprocessing**
   - Clean and normalize text
   - Remove noise (punctuation, numbers)
   - Apply lemmatization for word standardization

2. **Feature Extraction**
   - Convert text to TF-IDF numerical vectors
   - Each dimension represents word importance

3. **Model Training**
   - Train 5 different ML algorithms simultaneously
   - Evaluate each on held-out test data

4. **Model Selection**
   - Compare accuracy across all models
   - Automatically select the best performer

5. **Prediction**
   - Apply same preprocessing to new text
   - Use selected model for stress classification

---

## 📝 Example Usage

```python
import pandas as pd
from src.preprocessing import preprocess_text
from src.model_training import train_and_evaluate
from src.prediction import predict_stress

# Load data
df = pd.read_csv('data/stress_data.csv')

# Train models
best_model, metrics = train_and_evaluate(df)

# Make predictions
sample_texts = [
    "I'm excited about the upcoming project",
    "The workload is getting out of hand",
    "Just another regular day"
]

for text in sample_texts:
    level, confidence = predict_stress(text, best_model)
    print(f"Text: {text}")
    print(f"Prediction: {level} ({confidence:.1%})\n")
```

---

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report issues and bugs
- Suggest improvements or new features
- Submit pull requests with enhancements
- Help improve documentation

---

## 📄 License

This project is open source and available under the MIT License.

---

## 👤 Author

**Omkar Korde** – [GitHub Profile](https://github.com/omkorde13)

---

## 💡 Future Enhancements

- [ ] Support for multiple languages
- [ ] Deep learning models (LSTM, BERT)
- [ ] Real-time web application interface
- [ ] Fine-tuning with custom datasets
- [ ] Confidence calibration
- [ ] API deployment options

---

## ❓ FAQ

**Q: What's the minimum dataset size?**  
A: Ideally 200+ samples per stress category for reliable training.

**Q: Can I use this for other text classification tasks?**  
A: Yes! The pipeline is general-purpose and works with any text classification problem.

**Q: How accurate is the model?**  
A: Accuracy depends on your dataset quality. Typically achieves 85-95% accuracy on balanced datasets.

**Q: Can I deploy this in production?**  
A: Yes! Save the trained model and use it with your application backend.

---

## 📞 Support & Questions

For questions or issues, please [open a GitHub issue](https://github.com/omkorde13/textmoodpredictor/issues).

---

**Happy predicting! 🚀**
