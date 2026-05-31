# Haseen | Arabic Phishing Detection

## Project Overview

**Haseen** is an Arabic phishing detection project that detects phishing messages in Arabic emails and SMS messages using Machine Learning and Deep Learning techniques.

The project compares a traditional machine learning model (**TF-IDF + SVM**) with an Arabic transformer-based model (**AraBERT**), and also evaluates two hybrid approaches to test whether combining models improves detection performance.

---

## Problem

Most phishing detection systems are designed mainly for English content. Arabic phishing detection is more challenging because Arabic has rich morphology, different dialects, informal writing styles, and mixed message structures.

This project addresses this gap by building and evaluating an Arabic phishing detection system for email and SMS messages.

---

## Dataset

The dataset was constructed for this project and contains Arabic email and SMS messages.

* **Total samples:** 11,543 Arabic messages
* **Data type:** Arabic emails and SMS messages
* **Classes:**

  * Phishing
  * Legitimate 
  
* **Dataset source:**

  * Manually collected Arabic messages
  * AI-generated Arabic messages

The dataset was split into:

| Split      | Percentage | Samples |
| ---------- | ---------: | ------: |
| Training   |      62.3% |   7,193 |
| Validation |      14.5% |   1,675 |
| Testing    |      23.2% |   2,675 |

The training set was used to train the models, the validation set was used to monitor performance and tune the models, and the testing set was used for final unbiased evaluation.

---

## Preprocessing

The following preprocessing steps were applied:

* Arabic text normalization
* Cleaning noisy text
* Removing duplicate and highly similar samples
* Replacing URLs, emails, and numbers with placeholder tokens
* Preparing TF-IDF features for the SVM model
* Applying AraBERT tokenization for the transformer-based model
* Preventing data leakage between training, validation, and testing sets

---

## Models

Four models were implemented and compared:

### 1. SVM + TF-IDF

A traditional machine learning baseline model using:

* TF-IDF vectorization
* Linear Support Vector Machine
* GridSearchCV
* 5-fold cross-validation
* Class balancing

### 2. AraBERT

A transformer-based Arabic language model using:

aubmindlab/bert-base-arabertv02

AraBERT was fine-tuned on the constructed Arabic phishing dataset.

### 3. Hybrid Ensemble

A weighted soft voting model combining:

* SVM
* AraBERT

The best configuration used:

SVM = 0.6
AraBERT = 0.4

### 4. Hybrid Stacking

A stacking model using:

* SVM predictions
* AraBERT predictions
* Logistic Regression as the meta-classifier

---

## Final Results

| Model           | Accuracy | Precision | Recall | F1-score |
| --------------- | -------: | --------: | -----: | -------: |
| SVM             |   92.08% |    82.31% | 91.67% |   86.74% |
| AraBERT         |   98.18% |    95.91% | 97.73% |   96.81% |
| Hybrid Ensemble |   98.39% |    96.98% | 97.35% |   97.16% |
| Hybrid Stacking |   98.07% |    95.90% | 97.35% |   96.62% |

---

## Key Findings

* AraBERT achieved the best standalone model performance.
* The Hybrid Ensemble achieved the highest overall accuracy.
* SVM provided a strong traditional baseline, but it was outperformed by AraBERT.
* Transformer-based models were more effective for Arabic phishing detection because they better capture contextual meaning and Arabic linguistic variations.

---

## Evaluation Metrics

The models were evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Classification report
* Confusion matrix

---

## How to Open the Notebook

GitHub may sometimes fail to preview `.ipynb` files directly. If that happens, open the notebook using Google Colab.

### GitHub Repository

https://github.com/saraabduallh-1/Arabic_Phishing_Detection.GP


### Open in Google Colab

https://colab.research.google.com/drive/1x6zuEr9wvoNfsgqFy-8wGkKgq4925Lw9?usp=sharing

---

## Requirements

Main Python libraries used in this project:

pandas
numpy
scikit-learn
matplotlib
torch
transformers


Install them using:

pip install pandas numpy scikit-learn matplotlib torch transformers


---

## Project Files


Arabic_Phishing_Detection.GP/
│
├── Arabic_Phishing_SVM_AraBERT_EnhancedHybrid_(Final)_(1).ipynb
├── 
└── README.md



---

## Conclusion

This project developed an Arabic phishing detection system for email and SMS messages. The results showed that AraBERT achieved strong standalone performance and outperformed the traditional SVM baseline. The Hybrid Ensemble model achieved the highest overall accuracy, while AraBERT remained highly effective as an independent solution for Arabic phishing detection.

---

## Future Work

Future improvements may include:

* Expanding the dataset with more real-world Arabic phishing messages
* Supporting more Arabic dialects
* Improving model interpretability
* Deploying the model as a real-time detection tool
* Integrating the model into a mobile application or browser extension

---

## Authors

* Sarah Abduallh Moubrad
* Sahab Abdulaziz Alkhayal
* Jory Fahad Altamimi

**Supervisor:** Dr. Fatmah Alanazi

Al Imam Muhammad ibn Saud Islamic University
College of Computer and Information Systems
Computer Science Department

---

## License

This project was developed for academic and educational purposes.
