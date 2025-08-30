# message-spam-classifier

## 📌 Project Overview
This project develops a **spam SMS detection model** to classify text messages as either **spam** or **ham (legitimate)**.  
The dataset used is the classic **SMSSpamCollection** dataset with 5,572 messages (4,825 ham and 747 spam).  

The problem is highly imbalanced (≈13% spam vs 87% ham), making it a realistic challenge for text classification.

---

## 📊 Exploratory Data Analysis
- **Class distribution**:  
  - Ham → 4,825 (86.6%)  
  - Spam → 747 (13.4%)  
- **Message length**:  
  - Ham: ~71 characters (short, conversational)  
  - Spam: ~138 characters (longer, promotional)  
- **Visual insights**:  
  - Count plots confirm imbalance  
  - Histograms show spam messages tend to be longer  

---

## 🔧 Methodology

### Preprocessing
- Text normalization (lowercasing, punctuation removal)  
- Stopword removal + lemmatization  
- Feature extraction with **TF-IDF**  

### Models
- **Naive Bayes** (GridSearchCV tuned, alpha=1.0)  
  - Strength → *zero false positives*  
- **Logistic Regression** (C=100, class_weight=balanced)  
  - Strength → *handles imbalance effectively*  

---

## 📈 Model Performance

| Metric            | Naive Bayes | Logistic Regression |
|-------------------|-------------|----------------------|
| **Accuracy**      | 97.40%      | 98.03%              |
| **Spam Recall**   | 83%         | 89%                 |
| **F1-Score**      | 90%         | 92%                 |
| **False Positives** | 0         | 5                   |
| **False Negatives** | 25        | 17                  |

**Key Takeaways:**  
- Logistic Regression achieves **higher accuracy & recall**, minimizing missed spam.  
- Naive Bayes is more conservative (no false positives) but misses more spam messages.  

---

## ⚠️ Challenges & Solutions
- **Imbalanced classes** → Stratified sampling + class weights  
- **Noisy text** → Regex cleaning + lemmatization  
- **Model tuning** → Grid Search CV for hyperparameter optimization  

---

## ✅ Conclusion
- **Logistic Regression** is recommended for deployment:  
  - Accuracy: **98.03%**  
  - Spam Recall: **89%**  
  - Only 5 false positives vs 17 false negatives  
- In practice, minimizing **missed spam** is more critical than a few false alarms.  
- Future work → Apply **SMOTE** to further reduce false negatives.  

---

## 🛠 Tech Stack
- Python 3.x  
- scikit-learn  
- NumPy, Pandas  
- Matplotlib, Seaborn  

---

## 📄 License
This project is for **academic purposes only**.  

✨ If you find it useful, feel free to star ⭐ or fork 🍴 the repo!
