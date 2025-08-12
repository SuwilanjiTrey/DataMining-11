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
   Evaluate multiple algorithms (e.g., Logistic Regression, BERT-based models, etc) to determine the
   best performing classifier.

  1.4 Initial Project Success Criteria
   The following are the measures put in place to consider this project a successful:
   
   Quantitative Criteria:
   1. The model achieves at least 80% accuracy on a held-out test set.
   2. The model maintains a macro F1-score above 0.75, ensuring balanced performance across all classes.
      
   Qualitative Criteria:
   1. The predicted categories are meaningful and consistent with expert legal classification.
   2. The classification process is significantly faster than manual sorting.
   3. The model generalizes well to new, unseen judgments.
