```python
# Import libraries
import pandas as pd
import numpy as np
import re
import nltk

# Read Excel file
df = pd.read_excel('PhoneReviews.xlsx')
df
```
![alt text](https://github.com/emilyngx/SocialMedia_TextMining/blob/main/Normalize%20corpus%20using%20NLTK/images/0.png)
```python
# Define 5 categories for Rating column
categories = {5: 'very happy', 4: 'happy', 3: 'neutral', 2: 'unhappy', 1: 'very unhappy'}

# Assign category
labels = []
for i in df['Rating']:
    for key, value in categories.items():
        if key == i:
            labels.append(value)
labels
```
![alt text](https://github.com/emilyngx/SocialMedia_TextMining/blob/main/Normalize%20corpus%20using%20NLTK/images/1.png)
```python
# Drop non-text columns and replace Rating column with its assigned labels
non_text = []
for col in df:
    if df[col].dtypes != "object":
        non_text.append(col)
Phonereviews_df = df.drop(columns = non_text)
Phonereviews_df['Rating'] = labels
Phonereviews_df
```
![alt text](https://github.com/emilyngx/SocialMedia_TextMining/blob/main/Normalize%20corpus%20using%20NLTK/images/2.png)
```python
corpus = np.array(Phonereviews_df['Reviews']) #convert from Dataframe to array
corpus = corpus.ravel() # Convert multi-dimensional array to 1 dimension

wpt=nltk.WordPunctTokenizer()
stop_words=nltk.corpus.stopwords.words('english')

# Function to normalize corpus
def normalize(text):
    #lowercase and remove special characters\whitespace
    text = re.sub(r'[^a-zA-Z\s]', '', text, re.I|re.A) #re.I ignore case sensitive, ASCII-only matching
    text = text.lower()
    text = text.strip()
    #tokenize document
    tokens = wpt.tokenize(text)
    #filter stopwords out of document
    filtered_tokens = [token for token in tokens if token not in stop_words]
    #re-create documenr from filtered tokens
    text = ' '.join(filtered_tokens)
    return text
    
normalize_corpus = np.vectorize(normalize)
normalized_corpus = normalize_corpus(corpus)
normalized_corpus

# Return the normalized corpus
normalized_corpus = pd.DataFrame(normalized_corpus)
normalized_corpus
```
![alt text](https://github.com/emilyngx/SocialMedia_TextMining/blob/main/Normalize%20corpus%20using%20NLTK/images/3.png)
