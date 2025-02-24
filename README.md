# Machine-Learning

## Basis of Clustering
Become confident in using different clustering algorithms for different types of data  
Describe which algorithm you believe has the highest potential to correctly identify the clusters and why.


## Text Categorization with Decision Trees
Implement a Decision Tree (DT) from scratch  
Build each decision tree by maintaining a priority queue of leaves, sorted by the maximum value of the feature   
Grow the tree one node at a time, up to 100 internal nodes  
Train and test an algorithm with the provided datasets in trainData.txt and testData.txt.   
These datasets contain a subset of Reddit posts sourced from https://files.pushshift.io/reddit/ and processed using Google BigQuery. The dataset includes the first 1500 comments of August 2019 of each of the r/books and r/atheism subreddits, cleaned by removing punctuation and some offensive language and limiting the words to only those used more than 3 times among all posts. These 3000 comments are split evenly into training and testing sets (with 1500 documents in each) and converted to the bag of words model. Each line of the files trainData.txt and testData.txt are formatted “docId wordId” which indicates that word wordId is present in document docId. The files trainLabel.txt and testLabel.txt indicate the label/category (1=atheism or 2=books) for each document (docId = line#). The file words.txt indicates which word corresponds to each wordId (denoted by the line#). 
I used two feature selection mechanisms as follows:
1. average information gain (evenly weighted across the leaves)
2. information gain weighted by the fraction of documents on each side of the split, as we discussed in class
  (the information gain of the best performing next feature to split on). At each iteration, split the leaf where the split will give the largest information gain (according   
Plot the training and testing accuracy (i.e., percentage of correctly classified articles) after adding each new node.
Plot two curves on each (one for training accuracy and one for test accuracy). 
