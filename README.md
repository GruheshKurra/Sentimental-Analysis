# Sentiment Analysis Using Python

This code performs sentiment analysis using a rule-based method in Python.

## Imports

```python
import pandas as pd
import nltk
from nltk.tokenize import word_tokenize
positive_words = ['good', 'great', 'excellent', 'awesome', 'happy']
negative_words = ['bad', 'terrible', 'horrible', 'awful', 'sad']
def sentiment_analysis(text):
    tokens = word_tokenize(text)
    sentiment_score = 0
    for token in tokens:
        if token in positive_words:
            sentiment_score += 1
        elif token in negative_words:
            sentiment_score -= 1

    if sentiment_score > 0:
        return 'Positive'
    elif sentiment_score < 0:
        return 'Negative'
    else:
        return 'Neutral'
# Assuming you have the dataset in a CSV file named 'file.csv'
df = pd.read_csv('path/to/your/file.csv')
df['Sentiment'] = df['Text'].apply(sentiment_analysis)
print(df)
