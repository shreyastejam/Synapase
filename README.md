# Synapase
Task for Synapse
Natural Language Processing

Twitter Sentiment Analysis using Python:-
Introducing Sentiment Analysis
Also known as “Opinion Mining”, Sentiment Analysis refers to the use of Natural Language Processing to determine the attitude, opinions and emotions of a speaker, writer, or other subject within an online mention.
Essentially, it is the process of determining whether a piece of writing is positive or negative. This is also called the Polarity of the content.
As humans, we are able to classify text into positive/negative subconsciously. For example, the sentence “The kid had a gorgeous smile on his face”, will most likely give us a positive sentiment. In layman’s terms, we kind of arrive to such conclusion by examining the words and averaging out the positives and the negatives. For instance, the words “gorgeous” and “smile” are more likely to be positive, while words like “the”, “kid” and “face” are really neutral. Therefore, the overall sentiment of the sentence is likely to be positive.
A common use for this technology comes from its deployment in the social media space to discover how people feel about certain topics, particularly through users’ word-of-mouth in textual posts, or in the context of Twitter, their tweets.

Reasons for using sentiment analysis:-
•	Business: In marketing field companies use it to develop their strategies, to understand customers’ feelings towards products or brand, how people respond to their campaigns or product launches and why consumers don’t buy some
products.

•	Politics: In political field, it is used to keep track of political view, to detect consistency and inconsistency between statements and actions at the government level. It can be used to predict election results as well!

•	Public Actions: Sentiment analysis also is used to monitor and analyse social phenomena, for the spotting of potentially dangerous situations and determining the general mood of the blogosphere.

Prerequisites:-
•	Basic programming knowledge
Although Python is highly involved in this mini-project, it is not required to have a deep knowledge in the language, as long as you have basic programming knowledge.
•	Installed tool 
For this program, we will need Python to be installed on the computer. We will be using the libraries twitter, nltk, re, csv, time, and json. You are likely to have to install the first two libraries. The rest already come with the Python interpreter. It doesn’t hurt to check that they’re up-to-date though.
•	Data set splitting concept
This is critical to fully understand the process pipeline. You only need to know the difference between Training and Test data sets, and in what context each one is used.
•	Basic RESTful API knowledge
This is not crucial, but it could help. We will be using the Twitter API here and there in the code, making normal calls to the API and dealing with the JSON objects it returns. 

So The Steps Are:-

Installation:



•	Tweepy: tweepy is the python client for the official Twitter API.
Install it using following pip command:
pip install tweepy

•	TextBlob: textblob is the python library for processing textual data.
Install it using following pip command:
pip install textblob
Also, we need to install some NLTK corpora using following command:
python -m textblob.download_corpora
(Corpora is nothing but a large and structured set of texts.)

Authentication:
In order to fetch tweets through Twitter API, one needs to register an App through their twitter account. Follow these steps for the same:
•	Open this https://developer.twitter.com/ and click the button: ‘Create New App’
•	Fill the application details.
•	Once the app is created, you will be redirected to the app page.
•	Open the ‘Keys and Access Tokens’ tab.
•	Copy ‘Consumer Key’, ‘Consumer Secret’, ‘Access token’ and ‘Access Token Secret’.

We follow these 3 major steps in our program:
•	Authorize twitter API client.
•	Make a GET request to Twitter API to fetch tweets for a particular query.
•	Parse the tweets. Classify each tweet as positive, negative or neutral.

Now, let us try to understand the above piece of code:
•	First of all, we create a TwitterClient class. This class contains all the methods to interact with Twitter API and parsing tweets. We use __init__ function to handle the authentication of API client.
•	In get_tweets function, we use:
fetched_tweets = self.api.search(q = query, count = count)
to call the Twitter API to fetch tweets.
•	In get_tweet_sentiment we use textblob module.
analysis = TextBlob(self.clean_tweet(tweet))

TextBlob is actually a high level library built over top of NLTK library. First we call clean_tweet method to remove links, special characters, etc. from the tweet using some simple regex.
Then, as we pass tweet to create a TextBlob object, following processing is done over text by textblob library:
•	Tokenize the tweet ,i.e split words from body of text.
•	Remove stopwords from the tokens.(stopwords are the commonly used words which are irrelevant in text analysis like I, am, you, are, etc.)
•	Do POS( part of speech) tagging of the tokens and select only significant features/tokens like adjectives, adverbs, etc.
•	Pass the tokens to a sentiment classifier which classifies the tweet sentiment as positive, negative or neutral by assigning it a polarity between -1.0 to 1.0 .
Here is how sentiment classifier is created:
•	TextBlob uses a Movies Reviews dataset in which reviews have already been labelled as positive or negative.
•	Positive and negative features are extracted from each positive and negative review respectively.
•	Training data now consists of labelled positive and negative features. This data is trained on a Naive Bayes Classifier.
Then, we use sentiment.polarity method of TextBlob class to get the polarity of tweet between -1 to 1.
Then, we classify polarity as:
if analysis.sentiment.polarity > 0:
       return 'positive'
elif analysis.sentiment.polarity == 0:
       return 'neutral'
else:
       return 'negative'
•	Finally, parsed tweets are returned. Then, we can do various type of statistical analysis on the tweets. For example, in above program, we tried to find the percentage of positive, negative and neutral tweets about a query.

Conclusion:-
Sentiment Analysis is an interesting way to think about the applicability of Natural Language Processing in making automated conclusions about text. It is being utilized in social media trend analysis and, sometimes, for marketing purposes. Making a Sentiment Analysis program in Python is not a difficult task, thanks to modern-day, ready-for-use libraries. This program is a simple explanation to how this kind of application works. This is only for academic purposes, as the program described here is by no means production-level.

