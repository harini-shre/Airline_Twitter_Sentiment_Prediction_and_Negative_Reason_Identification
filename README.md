# Airline Twitter Sentimental Prediction and Negative Reason Identification
#

Twitter is one of the widely used social media platform across the world, where an individual can express his/her thoughts. The tweets posted by a person may be related to a scenario, person, product or service. We can use these tweets to identify the customer's opinion on the product/service. This helps in finding out the ratio of satisfaction or disappointment customers. We can also use the same tweets to identify the reason for the satisfaction or disappointment in the product/service.
###
## Dataset
The Dataset used is "Twitter US Airline Sentiment". It is obtained from Kaggle. The dataset contains the scapped tweets of US Airline Companies of February 2015. It contains 15 columns including text(tweet), the sentiment of tweet, reason for negative text, airline name, tweet posted location, retweet count, etc...
###
## Objective
To Create two Machine Learning Models using Python. 
- First model to predict if a Tweet has "Positive", "Negative" or "Neutral" sentiment.
- Second model to predict the reason for disappointment of the customer, if the Tweet is a "Negative" tweet. This helps the airline company to identify the services in which they lack, so that it can be focused and improved.
###
## Text Preprocessing Steps performed on a Tweet
- Identify all the negative stopwords and remove them from the stopwords list.
- The text is split into words
- Words which are **stop words** or twitter account name ( starting with '@' ) or website links ( starting with 'http') or ampersand are removed
- Words are converted to Lower case
- All negative stopwords are replaced with 'not'
- Only the English alphabets in the word are retained.
- The POS tag (Part of Speech tag) of the word is identified and passed to **Lemmatizer** to obtain root word. If Error is thrown, then word is passed to Lemmarizer without the POS tag. In this case the POS tag is defaultly considered as a noun.
- All the cleaned words are concatinated as a string 
###
## Steps for training models
#### Steps for training Airline Sentiment Prediction Models:
- Drop the rows which have **"airline_sentiment_confidence" less than 1.**
- Retain only the **"text"** as independent feature and **"airline_sentiment"** as dependent feature.
- For each Tweet, Text Preprocessing Steps mentioned above is followed
- Create **Unigram Bag of Words** seperately and **Bigram Bag of Words** seperately
    - Split Each Bag of Words into train and test ratio - 0.8 and 0.2
    - Try fitting models
- The Dataset is imbalanced, so Accuracy Score cannot be used as metric. Here both Precision and Recall are Important. So F1-Score is considered as a metric.
#### Steps for training Reason Prediction For Negative Tweet Models:
- Drop the rows which have **"negativereason_confidence" less than 1.**
- Retain only the **"text"** as independent feature and **"negativereason"** as dependent feature.
- For each Tweet, Text Preprocessing Steps mentioned above is followed
- Create Unigram Bag of Words
- Split Bag of Words into train and test ratio - 0.8 and 0.2
- Try fitting models
- The Dataset is imbalanced, so Accuracy Score cannot be used as metric. Here both Precision and Recall are Important. So F1-Score is considered as a metric.
###
###
## Machine Learning Approaches Used:
- MultinomialNB
- LinearSVM
- Random Forest

The above models are used for **Airline Sentiment Prediction** for both **Unigram** and **Bigram** Bag of Words.
The above models are used for **Reason Prediction For Negative Tweet** for the **Unigram** Bag of Words.



## Output:
For **Airline Sentiment Prediction**, the **LinearSVC model of UNIGRAM** is finalized, it has 
- **F1-Score of 80.74%**
- **average accuracy of 87.00%.**

For **Reason Prediction For Negative Tweet**, the **LinearSVC model of UNIGRAM** is finalized, it has 
- **F1-Score of 65.40%**
- **average accuracy of 82.45%.**

Finally created a function called "Sentiment_Prediction", which includes the both finalized LinearSVC Unigram models to predict the sentiment of the tweet and if sentiment is negative then predict the reason.








`


