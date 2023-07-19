# Sentiment Analysis Using Python

This Python code performs sentiment analysis using a rule-based method. It analyzes the sentiment of the text based on the presence of positive and negative words.

## Imports

```python
import pandas as pd
import nltk
from nltk.tokenize import word_tokenize
import string

nltk.download('punkt')

positive_words = ['good', 'great', 'excellent', 'awesome', 'happy']
negative_words = ['bad', 'terrible', 'horrible', 'awful', 'sad']
```

In this section, we import the required libraries: pandas for data manipulation, nltk (Natural Language Toolkit) for natural language processing, and specifically, word_tokenize from nltk.tokenize to tokenize the text into words. We also define two lists, positive_words and negative_words, which contain words associated with positive and negative sentiments, respectively.

## Sentiment Analysis Function

```python
def calculate_sentiment_score(text):
    tokens = word_tokenize(text.lower())
    sentiment_score = 0
    for token in tokens:
        token = token.strip(string.punctuation)
        if token in positive_words:
            sentiment_score += 1
        elif token in negative_words:
            sentiment_score -= 1
    return sentiment_score

def map_to_0_to_100(score):
    max_score = 5
    min_score = -5
    scaled_score = ((score - min_score) / (max_score - min_score)) * 100
    return min(max(scaled_score, 0), 100)
```

The sentiment_analysis function takes a text input as a parameter and performs sentiment analysis on that text. It first tokenizes the input text into individual words using word_tokenize from NLTK. Then, it calculates a sentiment score by counting the occurrences of positive and negative words. If a word is found in the positive_words list, the sentiment score is increased by 1, and if a word is found in the negative_words list, the sentiment score is decreased by 1. The function returns the sentiment label as 'Positive', 'Negative', or 'Neutral' based on the sentiment score.

## Performing Sentiment Analysis on Dataset

```python
# Assuming you have the dataset in a CSV file named 'file.csv'
df = pd.read_csv(r'C:\Users\akagr\OneDrive\Desktop\XtraLeap\Sentimental Analysis\dataset.csv')
df['Sentiment_Score'] = df['Text'].apply(calculate_sentiment_score)
df['Sentiment_Score'] = df['Sentiment_Score'].apply(map_to_0_to_100)
print(df)
```

This section assumes that you have the dataset in a CSV file named 'file.csv'. You should replace 'path/to/your/file.csv' with the actual file path where your dataset is located. The code reads the CSV file into a pandas DataFrame (df). Then, it applies the sentiment_analysis function to each text in the 'Text' column of the DataFrame and stores the sentiment analysis results in a new column named 'Sentiment'. Finally, the DataFrame with the added 'Sentiment' column is printed to display the results.

## How It Works

1. The code imports the required libraries: pandas, nltk, and nltk.tokenize.word_tokenize.
2. Two lists, `positive_words` and `negative_words`, are defined, which contain words associated with positive and negative sentiments, respectively.
3. The `sentiment_analysis` function is defined to perform sentiment analysis on the input text:
   - It tokenizes the text into individual words.
   - It calculates a sentiment score based on the occurrence of positive and negative words in the text.
   - The function returns the sentiment label as 'Positive', 'Negative', or 'Neutral' based on the sentiment score.
4. The code reads the dataset from a CSV file named 'file.csv' and stores it in a pandas DataFrame `df`.
5. The `sentiment_analysis` function is applied to each text in the 'Text' column of the DataFrame, and the sentiment analysis results are stored in a new column named 'Sentiment'.
6. Finally, the DataFrame with the added 'Sentiment' column is printed to display the results.

## How to Use

1. Make sure you have Python, pandas, and nltk installed.
2. Install the required libraries using pip:

```bash
pip install pandas nltk
```
## Example
Suppose you have a CSV file named data.csv with the following content:

```vbnet
Text
This is a good movie.
I feel terrible about the news.
The weather is great today.
```
After running the code, the DataFrame will be updated as follows:
```mathematica
                            Text    Sentiment_Score
0            This is a good movie.             60.0
1  I feel terrible about the news.             40.0
2      The weather is great today.             60.0
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

##License
This project is licensed under the MIT License.

```css
You can now save this content in the `README.md` file of your GitHub repository. This Markdown file includes explanations, code snippets, and an example to provide a clear understanding of the sentiment analysis code.
```
