# Sentiment Analysis Using Python

This Python code performs sentiment analysis using a rule-based method. It analyzes the sentiment of the text based on the presence of positive and negative words.

## Imports

```python
import pandas as pd
import nltk
from nltk.tokenize import word_tokenize

positive_words = ['good', 'great', 'excellent', 'awesome', 'happy']
negative_words = ['bad', 'terrible', 'horrible', 'awful', 'sad']
```

In this section, we import the required libraries: pandas for data manipulation, nltk (Natural Language Toolkit) for natural language processing, and specifically, word_tokenize from nltk.tokenize to tokenize the text into words. We also define two lists, positive_words and negative_words, which contain words associated with positive and negative sentiments, respectively.
