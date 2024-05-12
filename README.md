Customer sentiment Analysis
Import necessary libraries:
Make sure you have pandas and any additional libraries you need installed. If not, you can install them using pip install pandas and pip install whatever_library_you_need.

import pandas as pd
from textblob import TextBlob
Create or load the dataset:
# You can either create a dataset or load an existing one. For this example, let's create a simple dataset with a column containing customer reviews.
data={'CustomerID':[1,2,3,4],
      'Review':['The product is excellent! i love it.',
                'Not bad,but it could be better.',
                'Terrible experience. i want a refund.',
                'Amazing service and quick delivery']}
df=pd.DataFrame(data)
df
CustomerID	Review
0	1	The product is excellent! i love it.
1	2	Not bad,but it could be better.
2	3	Terrible experience. i want a refund.
3	4	Amazing service and quick delivery
#Perform sentiment analysis using TextBlob:
​
def analyze_sentiment(text):
    analysis = TextBlob(text)
    # Sentiment polarity ranges from -1 to 1 (-1: negative, 0: neutral, 1: positive)
    polarity = analysis.sentiment.polarity
    
    if polarity > 0:
        return 'Positive'
    elif polarity == 0:
        return 'Neutral'
    else:
        return 'Negative'
​
df['Sentiment'] = df['Review'].apply(analyze_sentiment)
​
# Inspect the results
print(df)
   CustomerID                                 Review Sentiment
0           1   The product is excellent! i love it.  Positive
1           2        Not bad,but it could be better.  Positive
2           3  Terrible experience. i want a refund.  Negative
3           4     Amazing service and quick delivery  Positive
