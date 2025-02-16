# Recipe Reviews Sentiment Analysis  

## Project Overview  
This project analyzes user feedback and reviews on recipes to uncover sentiment trends and user engagement patterns. By leveraging **Apache Spark**, **natural language processing (NLP)**, and **machine learning models**, the study aims to improve recipe recommendations and enhance customer satisfaction.  

## Dataset Overview  
- **Source**: UCI Machine Learning Repository  
- **File Size**: 5.8 MB  
- **Format**: CSV  
- **Instances**: 18,182  
- **Features**: 15  
- **Missing Values**: Present in the text column  

### Key Attributes  
- **Recipe Details**: Name, ranking, unique ID  
- **User Information**: ID, reputation score  
- **Review Data**: Comment ID, timestamp, replies, thumbs up/down, star rating (1-5 scale, 0 if not rated)  
- **Text Data**: Full review comment for NLP-based sentiment analysis  

## Business Context  
The dataset, sourced from an online platform, represents real-world user feedback on recipes. This data is useful for **sentiment analysis**, **user behavior modeling**, and **recommendation systems**. By understanding sentiment and engagement patterns, platforms can improve user experience and boost interaction.  

---

## Data Preparation and Preprocessing  
### Steps Taken  
1. **Initialize Spark Session** – Set up a distributed environment for large-scale processing.  
2. **Load Dataset** – Read and explore the CSV file using `pyspark.sql`.  
3. **Data Type Casting** – Convert numeric fields to appropriate data types (`IntegerType`, `TimestampType`).  
4. **Data Cleaning** – Handle missing values in text fields and remove redundant data.  
5. **Correlation Analysis** – Analyze relationships between user reputation, thumbs up, and ratings.  
6. **Feature Engineering** – Extract additional time-based features (year, month, day) for trend analysis.  

### Data Visualizations  
- **Top 20 Recipes by Rating**  
- **Top 20 Recipes by Thumbs Up**  
- **Review Length vs. Rating**  
- **Sentiment Trends Over Time**  

---

## Sentiment Analysis  
### Approach  
- **Tool Used**: `TextBlob` for sentiment polarity scoring.  
- **Processing Steps**:  
  - Tokenization, stopword removal, and lemmatization applied to review text.  
  - Polarity scores assigned to each review to classify sentiment as **positive, neutral, or negative**.  

### Key Findings  
- Positive reviews correlate with **higher engagement (thumbs up)**.  
- Long reviews tend to show **stronger sentiment** (either highly positive or negative).  

### NLP-Based Feature Extraction  
- **Noun and Adjective Analysis**: Identified frequent descriptive words in reviews.  
- **Word Cloud Visualization**: Generated insights into common themes in positive and negative reviews.  

---

## Machine Learning Models  
### Goal  
Develop sentiment classification models using textual and engagement data.  

### Models Implemented  
| Model | Precision | Recall | F1 Score |  
|---|---|---|---|  
| Random Forest | 73.5% | 85.7% | 79.1% |  
| Logistic Regression | 73.5% | 85.7% | 79.1% |  
| Decision Tree | **81.8%** | **85.9%** | **80.0%** |  

### Comparative Analysis  
- **Random Forest** provided robust generalization but had slightly lower precision.  
- **Logistic Regression** acted as a simple baseline model.  
- **Decision Tree** outperformed others, achieving **the highest precision and recall**.  

### Model Implementation Steps  
1. **Text Feature Extraction**: TF-IDF vectorization of review text.  
2. **User Engagement Features**: Integration of thumbs up, thumbs down, and star ratings.  
3. **Model Training and Evaluation**: Used `SparkML` pipelines for training, testing, and hyperparameter tuning.  
4. **Cross-Validation**: Optimized model parameters for improved accuracy.  

### Best Performing Model: Decision Tree  
- Achieved the highest **precision (81.8%)**, meaning fewer false positive classifications.  
- Maintained strong recall and F1-score, balancing accuracy and interpretability.  

---

## Business Implications  
### Improving Recipe Recommendations  
- **Promote High-Rated Recipes**: Recipes with high ratings and engagement should be prioritized.  
- **Flag Low-Rated Recipes**: Negative reviews can be analyzed for potential improvements.  

### Trend Analysis  
- **Seasonal Rating Trends**: Identifying fluctuations in user sentiment over time can inform content strategies.  
- **Keyword Analysis in Negative Reviews**: Helps in identifying **common complaints** and areas for improvement.  

### Future Applications  
- **Advanced NLP Models**: Implement **BERT or LSTM** for better contextual understanding.  
- **Real-Time Sentiment Analysis**: Deploy models for **live content moderation and recommendation systems**.  
- **User Segmentation**: Tailor recipe recommendations based on user preferences and past interactions.  
