CRISP-DM Phase: Business Understanding — This stage defines the scope, objectives, and success criteria for the project before proceeding to Data Understanding

1. Business Understanding

  1.1 Problem Statement
   The Zambian judiciary produces a large number of legal judgments each year, each accompanied by
   descriptive information such as the case title, case number, court, judgment date, judges presiding,
   a brief case summary, and relevant keywords. Currently, classification of judgments by type (e.g.,
   criminal, civil, constitutional, commercial) is often done manually, which is time-consuming,
   inconsistent, and resource-intensive. This lack of automation makes it difficult for legal
   practitioners, researchers, and the public to quickly locate relevant cases, reducing the efficiency
   of legal research and limiting access to timely legal information.
   
  1.2 Business Objectives
   From a practical, real-world perspective, success means developing an automated solution that:
   Classifies judgments into correct categories using only their descriptive information. Reduces the
   time required to find relevant judgments for legal professionals, students, and researchers. Improves
   consistency and accuracy in classification compared to manual methods.Enhances public access to
   categorized legal information, supporting civic education and transparency.

  1.3 Data Mining Goals
   To achieve these business objectives, we will:
   Build a supervised machine learning classification model that predicts the type of judgment based on
   descriptive information fields:
   1. Case Title
   2. Case Number
   3. Court
   4. Judgment Date
   5. Judges presiding
   6. Case summary
   7. Keywords
   Preprocess and encode the descriptive text to extract meaningful features for classification.
   Evaluate multiple algorithms to determine the best performing classifier.

  1.4 Initial Project Success Criteria
   The following are the measures put in place to consider this project a successful:
   
   Quantitative Criteria:
   1. The model achieves at least 80% accuracy on a held-out test set.
   2. The model maintains a macro F1-score above 0.75, ensuring balanced performance across all classes.
      
   Qualitative Criteria:
   1. The predicted categories are meaningful and consistent with expert legal classification.
   2. The classification process is significantly faster than manual sorting.
   3. The model generalizes well to new, unseen judgments.

2. Data Understanding
1.Load your datasets into a pandas dataframe

[ ]
from google.colab import drive
drive.mount('/content/drive/')
Mounted at /content/drive/

[ ]
import pandas as pd
file_path = "/content/drive/MyDrive/Colab Notebooks/misc-unza25-csc4792-project_team11/Group_11_classification_of_judgements - Group_11_Classification_of_type.csv"
df = pd.read_csv(file_path)
2. Perform initial data exploration using commands like .head(), .info(), .describe(), and .shape

[ ]
df.head()


[ ]
df.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 19 entries, 0 to 18
Data columns (total 7 columns):
 #   Column           Non-Null Count  Dtype 
---  ------           --------------  ----- 
 0   CaseTitle        17 non-null     object
 1   CaseNumber       17 non-null     object
 2   Court            17 non-null     object
 3   JudgementDate    17 non-null     object
 4   JudgesPresiding  16 non-null     object
 5   CaseSummary      17 non-null     object
 6   Keywords         5 non-null      object
dtypes: object(7)
memory usage: 1.2+ KB

[ ]
df.describe()


[ ]
df.shape
(19, 7)
3. Create initial visualizations (e.g., histograms for numerical columns, bar charts for categorical columns) to understand the distributions of key attributes

[ ]
import matplotlib.pyplot as plt
var_court_counts = df['Court'].value_counts()
plt.barh(var_court_counts.index,var_court_counts.values,color="purple")
plt.title("Courts by Number of Judgments")
plt.xlabel("Count of cases")
plt.ylabel("Court Name")
plt.show()

4. Write a brief summary of your initial findings
Our initial findings for this are:
For now the dataset contains 19 rows and 7 columns
The columns include Case Title, Case Number, Court, Judgement Date, Judges Presiding, Case Summary, Keywords
Some fields contain missing values that may need cleaning
The distribution of judgement types is imbalanced, with High court cases being the most and court of appeal having the fewest
Zambia legal information institute (Z.L.I.I.) was our main source of data
Text-based fields will require preprocessing, possibly the following:
Tokenization
Stopword removal
embeddings

##Data Preparation Summary

The data preparation phase focuses on cleaning, transforming, and structuring the dataset to ensure it is ready for modeling. This involves addressing missing values and duplicates, creating new features to enhance predictive power, and transforming variables into forms suitable for analysis. This what we did in each stage:

Data Cleaning

Checked for missing values and duplicates.
Filled numeric missing values with median.
Filled categorical missing values with mode.
Removed duplicate records.

Feature Engineering

Created CaseTitleLength to measure title complexity.
Created NumJudges to count judges presiding over the case.
Created CaseSummaryLength to measure detail in case summaries.
Created HasKeywords as a binary indicator for presence of keywords.
Extracted Year from JudgementDate for temporal analysis

Data Transformation

Encoded categorical variables (Court, JudgesPresiding) into numeric form.
Standardized numerical variables (CaseTitleLength, CaseSummaryLength) for scale-sensitive algorithm
