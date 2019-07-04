#News-Classification

Dataset used from http://mlg.ucd.ie/datasets/bbc.html

Publication - D. Greene and P. Cunningham. "Practical Solutions to the Problem of Diagonal Dominance in Kernel Document Clustering", Proc. ICML 2006. [PDF] [BibTeX].

Dataset: BBC
All rights, including copyright, in the content of the original articles are owned by the BBC.

Consists of 2225 documents from the BBC news website corresponding to stories in five topical areas from 2004-2005.
Class Labels: 5 (business, entertainment, politics, sport, tech)

We use Natural Language Processing to read each story and identify the label to which the story belongs
Upon being provided with a news article, the predictive model we build is able to classify it into a single class label with a 97% accuracy

The 2225 text documents are separated into 5 labelled folders depending on which label they belong to as below:
Business – 510 files
Entertainment – 386 files
Politics – 417 files
Sport – 511 files
Tech – 401 files

We use the OS module in python  which provides a portable way of using operating system dependent functionality.
Using a for loop and the OS module, we iterate through each text file to read and append the text to a list variable X. Simultaneously, we append the subsequent folder name to a list variable Y

Using pandas, we create a data frame using created lists X and  Y, and write the data to a file, which will be used to build our model.

Upon exploring the data, we see that there are duplicate entries. We drop the duplicates to get 2127 unique columns
Upon examining the news length, we see that most news have about 2275 characters. The longest news has 25,600 characters which is labelled as politics and is about terrorism.

Upon plotting the length on a histogram. There appear to be differences in the length based on the type of news.

We first clean the string by passing it through a function, to remove any numbers and characters, and return the string in lower case.

We also remove stop words such as ‘is’, ‘are’, ‘of’ using the nltk module of stop words.

We use TFIDFVectorizer from scikit-learn to extract features from the text data.

TFIDF is an abbreviation for Term Frequency - Inverse Document Frequency. In simple terms, it gives a numerical value (weight) for each word, based on how many times it appears in all the documents.

We are able to extract 14,788 features from the dataset.

We split the data into the below sets:
1. Training set – 1,780 news articles
2. Test set – 445 news articles

We train the classification models below:
1. Naïve Bayes Classifier
2. Decision Tree Classifier
3. Random Forest Classifier


We evaluate the models based on the below metrics:
1. Confusion matrix
2 Classification report
3. Kappa
4. Accuracy

Of the 3 models trained, Naïve Bayes performed the best with a 0.97 accuracy and F1 Score, marginally better than the Random Forest Classifier.

The Naïve Bayes Classifier is our selection for the final model

The model is able to identify the type of news based on the content with a 97% accuracy.

The model can be retrained using K-Fold cross validation with by ensuring that the training data set is selected at random, and reduce the scope of overfitting the model. However, with an accuracy and precision as high as 97%, this will not be necessary in for this model.

