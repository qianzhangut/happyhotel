# Happy Hotel

## The Goal
You've just joined the data team at a large hotel chain. Your specific team is embedded in the customer experience division. Each day you receive hundreds of reviews of your 10 hotels from your customers. Each review consists of a free-form text review and a report of "happy" or "not happy". A product manager on your team wants to understand each hotel's performance at a more granular level; they want to build a product to identify topics within reviews. All of your reviews are unlabeled, and it's infeasible to label them by hand.
**Design and execute a method to identify topics within the reviews**. For each topic, **find a robust means of assigning a score to each hotel in that topic**. For each of the ten hotels, what recommendations would you make to their general managers?

## EDA

## Model
Topic modeling is the process of identifying topics in a set of documents. This can be useful for search engines, customer service automation, and any other instance where knowing the topics of documents is important. LDA model was built to find topics for the customer reviews. LDA is a popular algorithm for topic modeling with excellent implementations in the Python's Gensim package. The challenge, however, is how to extract good quality of topics that are clear, segregated and meaningful. This depends heavily on the quality of text preprocessing and the strategy of finding the optimal number of topics. 

Text was cleaned by 1) convert words to lowercase and remove non alphabetic characters, 2) remove stopwords and stem each word to the root.

The two main inputs to the LDA topic model are the dictionary (id2word) and the corpus. Gensim creates a unique id for each word in the document. It can also creat a bag of words corpus using tfidf. These two are used as input to fit the LDA model.

The LDA model is built with 20 different topics where each topic is a combination of keywords and each keyword contributes a certain weightage to the topic. The prelexity and coherence score for this model is -10.36 and 0.49, recpectively. They provide a convenient measure to judge how good a given topic model is

One way to find the optimal number of topics is to build many LDA models with different values of number of topics (k) and pick the one that gives the highest coherence value.

## Find the dominant topics
One of the practical application of topic modeling is to determine what topic a given document is about.

To find that, we find the topic number that has the highest percentage contribution in that document.

The format_topics_sentences() function below nicely aggregates this information in a presentable table.