## Automated Classification of Zambian Legal Judgments

### Project Overview

This project applies Data Mining & Machine Learning to automate the classification of Zambian legal judgments into categories such as Criminal, Civil, Constitutional, and Commercial.
Currently, judgments are manually sorted, which is time-consuming, inconsistent, and resource-intensive.
Our solution uses Natural Language Processing (NLP) and Machine Learning models to improve efficiency, consistency, and accessibility of legal information.

### CRISP-DM Workflow

1. Business Understanding
•	Problem: Manual classification of judgments is slow & inconsistent.
•	Objective: Build an automated model to classify judgments using descriptive text.
•	Success Criteria: ≥ 80% accuracy, balanced F1-score across classes, faster than manual sorting.

2. Data Understanding
•	Dataset: 249 legal cases collected from the Zambia Legal Information Institute (ZLII).
•	Attributes: Case Title, Case Number, Court, Judgment Date, Judges Presiding, Case Summary, Keywords.
•	Initial findings:
  o	Missing values in JudgesPresiding, CaseSummary, and Keywords.
  o	Imbalanced court distribution (High Court dominates).
  o	Text fields require preprocessing (tokenization, stopword removal, embeddings).

3. Data Preparation
•	Cleaned missing values.
•	Engineered features:
  o	Case summary length
  o	Presence of keywords
  o	Number of judges
•	Transformed text using TF-IDF vectorization 

4. Modeling
•	Models applied:
  o	Naive Bayes (MultinomialNB)
  o	Decision Tree Classifier
•	Features: Case Summaries (TF-IDF representation).
•	Results:
  o	Naive Bayes → Strong baseline, but lower accuracy.
  o	Decision Tree → Higher accuracy & more balanced performance.

5. Evaluation
•	Metrics: Accuracy, Precision, Recall, F1-score.
•	Decision Tree outperformed Naive Bayes overall.
•	Confusion matrices highlighted some overlap between Civil & Commercial cases.
•	Final Accuracy (Decision Tree): approximately 85%

6. Deployment
•	Final Model: Decision Tree Classifier.
•	Deployment Plan:
  o	Host via Python API (Flask/FastAPI).
  o	Web dashboard for users to paste/upload case summaries.
  o	Automatic categorization of new judgments.

