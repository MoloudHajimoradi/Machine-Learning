# Machine-Learning

## Basis of Clustering
Become confident at using different clustering algorithms for different types of data  
Describe which algorithm you believe has the highest potential to correctly identify the clusters and why.


## Text Categorization with Decision Trees
Train and test your algorithm with the provided datasets in trainData.txt and testData.txt. These datasets contain a
subset of Reddit posts sourced from https://files.pushshift.io/reddit/ and processed using Google
BigQuery. The dataset includes the first 1500 comments of August 2019 of each of the r/books and r/atheism subreddits,
cleaned by removing punctuation and some offensive language, and limiting the words to only those used
more than 3 times among all posts. These 3000 comments are split evenly into training and testing sets (with 1500
documents in each). To simplify your implementation, these posts have been pre-processed and converted to the bag
of words model. More precisely, each post is converted to a vector of binary values such that each entry indicates
whether the document contains a specific word or not.
Each line of the files trainData.txt and testData.txt are formatted “docId wordId” which indicates that word wordId
is present in document docId. The files trainLabel.txt and testLabel.txt indicate the label/category (1=atheism or
2=books) for each document (docId = line#). The file words.txt indicates which word corresponds to each wordId
(denoted by the line#). Your code will need to read this information from the provided files.
Implement a decision tree learning algorithm. Here, each decision node corresponds to a word feature, and the leaf
nodes correspond to a prediction of what subreddit the article belongs in. You will experiment with two feature
selection mechanisms as follows:
1. average information gain (evenly weighted across the leaves)
IG = I(E) 􀀀 [
1
2
 I(E1) +
1
2
 I(E2)]
2. information gain weighted by the fraction of documents on each side of the split, as we discussed in class
IG = I(E) 􀀀 [
N1
N
I(E1) +
N2
N
I(E2)]
where I(E) is the information content in the N examples before the split, and I(Ei) is the information content of
the Ni examples in the ith leaf after the split. Method (1) does not deal well with splits that put a lot of examples on
one side, and very few on the other. For example, suppose you have evenly distributed data across the target class (so
I(E) = 1), N examples, and 2 features. Suppose the first feature splits one example off from the other N 􀀀 1, so
Method (2) gives:
I(E1) = 0;
I(E2)  1;
IG  1 􀀀 [
1
N
 0 +
N 􀀀 1
N
 1] =
1
N
Using Method (2), IG is a small value. On the other hand, Method (1) will make IG look better than it should be, since
it will compute:
IG  1 􀀀 [
1
2
 0 +
1
2
 1] =
1
2
:
Use I(fg) = 1 (the entropy of the empty set is maximal).
As discussed in class, build each decision tree by maintaining a priority queue of leaves, sorted by the maximum value
of the feature (the information gain of the best performing next feature to split on). At each iteration, split the leaf where the split will give the largest information gain (according to each of the measures above), and do the split on the
word feature that gives that highest gain. Grow the tree one node at a time, up to 100 internal nodes, by training with
the training set only. The point estimate should be the majority class at the leaf (not a probability).
Plot the training and testing accuracy (i.e., percentage of correctly classified articles) after adding each new node.
Generate two graphs (one for each method of feature selection) and plot two curves on each (one for training accuracy
and one for test accuracy). These graphs should have accuracy as a percentage on the y-axis and number of nodes
(1-100) on the x-axis. You may generate them however you wish (e.g. Matplotlib for Python).



you must use the iterative priority queue model.
