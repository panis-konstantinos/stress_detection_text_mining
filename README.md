# Stress Detection Text Mining
This project aims to detect stress from social media articles using machine learning and natural language processing (NLP) techniques. It is co-autored by **Panagiotis Makropoulos**. The dataset used is publicly available at Kaggle ([Stress Detection from Social Media Articles](https://www.kaggle.com/datasets/mexwell/stress-detection-from-social-media-articles)). We specifically used *"Twitter_Full.csv"* file that contains Tweeter posts from September 2019 to September 2021.

# 1. Data Preprocessing - Feature Extraction
After performing exploratory data analysis and data visualization, data preprocessing techinques for text data were used. Specifically, we removed duplicates and null values, removed text noise (urls, html tags, punctuation, stopwords) and performed lemmatization utilizing WordNet Lemmatizer. In order to extract features from text data we employed Word2Vec word embedding technique and experimented with two different approaches. The first approach was to train a Word2Vec model on the training dataset corpus, whil the second approach utilized the pre-trained Word2Vec model *"word2vec-google-news-300"* which was trained on an significantly larger corpus from Google News articles. In both cases, Principal Component Analysis was performed in order to reduce data dimensionality. Finally, the dataset was split on training and test sets in a 70% - 30% ratio.

# 2. Model Training and Evaluation
Regarding the text classification task we trained Logistic Regression and XGBoost models. Since we used two distinct Word2Vec embeddings, this resulted in a total of four trained models. For hyper-parameter tuning Grid Search Cross-Validation technique was employed. The evaluation of the models was based on the performance metrics accuracy, F1-score and AUC.

# 3. Results
The model results are shown on the table below

| Model               | Embedding              | Accuracy | F1-Score | AUC  |
|---------------------|----------------------|----------|----------|------|
| Logistic Regression | Custom Word2Vec       | 76.65%      | 0.7769     | 0.7664 |
| Logistic Regression | Pretrained Word2Vec   | 81.83%      | 0.8232    | 0.8182 |
| XGBoost            | Custom Word2Vec       | 77.76%      | 0.7854     | 0.7776 |
| XGBoost            | Pretrained Word2Vec   | 80.60%      | 0.8130    | 0.8060 |
