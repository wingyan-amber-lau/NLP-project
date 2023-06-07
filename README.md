# NLP-project
# Sentiment Analysis
This project is to do the sentiment analysis based on amazon reviews of products. We used 2 approach; one is the Lexicon approach and the other one is machine learning approach. The reviews are classified as three classes:<br>
- Positive
- Neutral
- Negative
## Lexicon
Two Lexicon models are tested:
- [VaderSentiment](https://github.com/cjhutto/vaderSentiment)
- [TextBlob](https://textblob.readthedocs.io/en/dev/quickstart.html)

## Machine Learning Approach
Two Machine Learning models are trained:
- Logistic Regression
- SVM
### Preprocessing Steps
The following pre-processing steps are carried out:
1.	Remove duplicate reviews
2.	Transform “overall” column to “rating_tag” column by the following rules
    a.	If value is larger than 3, consider as “pos” which means positive<br>
    b.	If value is equal to 3, consider as “neu” which means neutral<br>
    c.	If value is smaller than 3, consider as “neg” which means negative<br>
3.	Select column “reviewText” and “summary” as corpus to be analyzed
4.	Concatenate column “reviewText” and “summary”
5.	Convert corpus to lower case
6.	Remove stop words
7.	Remove punctuations and digits
8.	Stemming
9.	Remove the 1000 samples of phase 1 for testing from the dataset
10.	Oversampling and undersampling to training dataset

### Explanation
**Remove Duplicate**<br>
Duplicated reviews are found in the dataset. Before removal, there are 77071 reviews, after that, 72968 records left in dataset. There are 4103 rows of duplicated reviews.<br>
**Columns Selection**<br>
“reviewText” and “summary” columns are selected for analyzation. “reviewText” contains the most context of the review, and “summary” contains less context but can still be used for analysis. <br>
**Convert To Lower Case**<br>
This is a standardizing procedure of the text for computer to easier understand human input; thus give higher accuracy. Moreover, this step helps in removing the stop word set using stop word library for steps afterwards.<br>
**Remove Stop Words**<br>
There are common words that are used within sentences without any meaning. Those words are called stop words. As they do not have value to the dataset, they can be eliminated for cleaning purposes. In this sentiment analysis case, some of the negative words are removed from the stop word set such as “not” and “no” to preserve the negative context of the data.<br>
**Remove Punctuations and Digits**<br>
Experiments are carried out for keeping exclamation marks but there is no difference in the results so all punctuation as weel as digits will be removed. As only 1000 features are selected for tfidf vector, exclamation marks are not appeared in the first 1000 features.<br>
**Stemming**<br>
Compared to lemmatization, stemming performs faster. It is used when time and computing resources are limited. Moreover, it is usually used for sentiment analysis as, unlike applications such as chatbot and question-answering model, complete words with meaning are unnecessary.<br>
**Remove 1000 Samples**<br>
To be able to compare the result of Lexicon model and Machine Learning model, the same 1000 samples are used to test the accuracy of the models after training. The remaining dataset is used to train the machine learning model.<br>
**Oversampling and Undersampling**<br>
The classes of the data are highly imbalance. Therefore, to tackle the problem of bias dataset, the majority class is undersampled from 60000 to 15000; the minority classes are oversampled from 4000 to 15000. It is to reduce the size of the dataset to save time cost and also to balance the dataset.<br>
**Text Representation**<br>
TF/IDF is used as text representation before inputting the data to the model.<br>

## Dataset
https://nijianmo.github.io/amazon/index.html
