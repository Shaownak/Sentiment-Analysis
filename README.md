# Sentiment-Analysis

# Introduction

Sentimental analysis is a huge sector of natural language processing which deals with the computational research of opinions , statements and emotions expressed in text. Sentimental analysis basically focuses on learning people’s opinion, attitude, view and emotion on a certain fact. This fact can be anything like individuals, events or topics. These sentiments can be extracted or identified by identifying the bold or capital letters, exclamations , question marks or quoted texts. The sentimental analysis differentiates between the positivity and negativity of a certain statement from the given text. The statements are utilized using natural language processing, text analysis and statistics in the form of sentimental analysis. These statements indicate the feelings or views of people focusing on the intention of people like why they are expressing those views, can be critical in business, politics, social media, e-commerce, food reviews etc.

We can find the reviews or sentiments of the people from different social media posts, news, reviews and learn about the sentiment of people. We can analyze these feelings with the help of computer algorithms or machine learning. People are continuously using social media and reviews to post their sentiments. But a huge amount of time is required to categorize those sentiments. So, a learning set is required to create a learning set with short categorization timing. We used Conv1D, Gated Recurrent Unit(GRU) and LSTM model training algorithms to train our model. 

In our research, we used food review sentimental statements and toxic statements for analysis. We can’t give computers the texts or strings directly for training our model. So, we categorized the negative sentiment as 0 and positive sentiments as 1. After preprocessing the dataset, we trained our model using above mentioned models and compared our results. The challenge was finding out which model is best for our case. The main advantage of our sentimental analysis is that it helps to analyze the consumer comments on foods and services or different actions that will help in the vast area of commercial sectors.


# Dataset Description
Datasets have binary notation except ctweet dataset (it has 3 labels). Food, sarcasm and stweet are pre-processed by making lower case and removing punctuations, hashtags, usernames and html tags. Reddit, ctweet and toxic datasets are still require pre-processing, so that is up to you. Their sentimental perspective and data structure are quite different. All binary datasets are labeled as 0 and 1, and ctweet has 0,1 and 2 under the 'Y' column. "ctweet, stweet, food" datasets are positive or negative analysis (sentiment) -> 0 negative -> 1 positive (ctweet has neutral 0, 1, 2) In "reddit and sarcasm" we ask for is there sarcasm or irony in the sentence? (sarcasm) -> 0 no -> 1 yes. In the "toxic" dataset we have sentences to detect, is there insulting? -> 0 no -> 1 yes. stweet and reddit are a million+ sentence datasets.food and toxic are medium size datasets. sarcasm and ctweet small datasets.


# Data Pre-Processing
Since raw data contains noise, duplication which is unsuitable for study, for that reason data pre-processing is a critical step in any type of data analysis.In our model, the final text-based data generated by websites, users have a diverse and unbalanced set of material.

In our model, the final text-based data generated by websites, users have a diverse and unbalanced set of material. To balance the final dataset, we are going to apply random undersampling to the train dataset. Since the test set has no labels and we need a way to evaluate our trained models, we'll split off some of the training data and create a validation set(2).In machine learning we work with numbers. So we have to convert the text into vectors. For this we use tokenization  technique. As we know while dealing with textual data, we need to convert it into numbers before feeding into any machine learning model, including neural networks. For this we will use an embedding layer. We use embedding because embedding  can be learned during training. This means rather than just being static (e.g. 1 = I, 2 = love, 3 = TensorFlow), a word's numeric representation can be improved as a model goes through data samples.

# Random Undersampling
Random undersampling involves randomly selecting examples from the majority class and deleting them from the training dataset. In the random under-sampling, the majority class instances are discarded at random until a more balanced distribution is reached.

# Split data into training and validation sets
We will convert our splits from pandas Series data types to lists of strings (for the text) and lists of ints (for the labels) for ease of use later.
To split our training dataset and create a validation dataset, we will use Scikit-Learn’s train_test_split() method and dedicate 10% of the training samples to the validation set. 


# Tokenization 
In machine learning we work with numbers. So we have to convert the text into numbers.For this we use tokenization  technique. Tokenization is the process of breaking up a string into tokens. Commonly, these tokens are words, numbers, and/or punctuation. Here first it makes the dataframe to sentences then makes these to words of list . To tokenize our words, we'll use the helpful preprocessing layer tf.keras.layers.experimental.preprocessing.TextVectorization.
The TextVectorization layer takes the following parameters:
max_tokens - The maximum number of words in your vocabulary (e.g. 20000 or the number of unique words in your text), includes a value for OOV (out of vocabulary) tokens.
standardize - Method for standardizing text. Default is "lower_and_strip_punctuation" which lowers text and removes all punctuation marks.
split - How to split text, default is "whitespace" which splits on spaces.
ngrams - How many words to contain per token split, for example, ngrams=2 splits tokens into continuous sequences of 2.
output_mode - How to output tokens, can be "int" (integer mapping), "binary" (one-hot encoding), "count" or "tf-idf". See documentation for more.
output_sequence_length - Length of tokenized sequence to output. For example, if output_sequence_length=150, all tokenized sequences will be 150 tokens long.
pad_to_max_tokens - Defaults to False, if True, the output feature axis will be padded to max_tokens even if the number of unique tokens in the vocabulary is less than max_tokens.


# Creating an Embedding using an Embedding Layer
Embedding layer enables us to convert each word into a fixed length vector of defined size. The resultant vector is a dense one with real values instead of just 0’s and 1’s. The fixed length of word vectors helps us to represent words in a better way along with reduced dimensions.
input_dim - The size of the vocabulary (e.g. len(text_vectorizer.get_vocabulary()).
output_dim - The size of the output embedding vector, for example, a value of 100 outputs a feature vector of size 100 for each word.
embeddings_initializer - How to initialize the embeddings matrix, default is "uniform" which randomly initializes embedding matrix with uniform distribution. This can be changed for using pre-learned embeddings.
input_length - Length of sequences being passed to the embedding layer.
Performance Evaluation
Predictive accuracy is commonly used as a criterion for evaluating machine learning algorithms. As a result, adopting the appropriate assessment metrics is critical for dealing with the data imbalance problem. Accuracy, precision, recall, and f1-score values are calculated from the confusion matrix for three class samples
Accuracy = (TP+TN)/(TP+TN+FP+FN)
Precision is the accurately anticipated average approximation of each class's labels.
Precision = TP/(TP+FP)

The recall value is the weighted average of properly stated points across all classes.
Recall = TP / ( TP + FN )

The F1 measure is specified in the equation below, and the F1 value is close to 1 for a good
measure.
F1 score = (2*Precision*Recall)/(Precision + Recall)

In the equations above, TP represents true positive, TN refers to true negative, FP and FN means false positive and false negative respectively.







