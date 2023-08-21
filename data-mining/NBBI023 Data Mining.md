Cluster Analysis
https://medium.com/analytics-vidhya/manual-step-by-step-complete-link-hierarchical-clustering-with-dendrogram-210c57b6afbf

https://www.datacamp.com/tutorial/introduction-hierarchical-clustering-python?utm_source=google&utm_medium=paid_search&utm_campaignid=19589720824&utm_adgroupid=143216588537&utm_device=c&utm_keyword=&utm_matchtype=&utm_network=g&utm_adpostion=&utm_creative=661628555495&utm_targetid=aud-299261629614:dsa-1947282172981&utm_loc_interest_ms=&utm_loc_physical_ms=9062902&utm_content=dsa~page~community-tuto&utm_campaign=230119_1-sea~dsa~tutorials_2-b2c_3-row-p2_4-prc_5-na_6-na_7-le_8-pdsh-go_9-na_10-na_11-na&gclid=Cj0KCQjw84anBhCtARIsAISI-xfNOdtDtBqkMLkqhSpEmAGG3FTqHVog3i3V_AROFcyHxY_yJ7NUdbYaAh09EALw_wcB

https://towardsdatascience.com/understanding-the-concept-of-hierarchical-clustering-technique-c6e8243758ec

_**Hierarchical clustering**,_ also known as _hierarchical cluster analysis,_ is an algorithm that groups similar objects into groups called _clusters_. The endpoint is a set of clusters_,_ where each cluster is distinct from each other cluster, and the objects within each cluster are broadly similar to each other.
Hierarchical clustering starts by treating each observation as a separate cluster. Then, it repeatedly executes the following two steps: (1) identify the two clusters that are closest together, and (2) merge the two most similar clusters. This iterative process continues until all the clusters are merged together. This is illustrated in the diagrams below.

![](images/Pasted%20image%2020230820133301.png)
▪ Divide the observed patterns into groups (clusters) of mutually similar patterns
Make an assumption that we can measure the distance between patterns
Distance between two patterns: 𝑥1 = (𝑥11, … , 𝑥1𝑚) and 𝑥2 = (𝑥21, … , 𝑥2m)
▪ Each pattern is characterized by m numerical quantities
![](images/Pasted%20image%2020230820132308.png)
The choice of the distance metrics depends on the involved quantities and their range (normalize the quantities (divide them by their mean, standard deviation)
![](images/Pasted%20image%2020230820132402.png)
![](images/Pasted%20image%2020230820132423.png)
Centroid ~ the center of the cluster
![](images/Pasted%20image%2020230820132502.png)
![](images/Pasted%20image%2020230820134736.png)
dendrogram  - ~ shows (from the left to the right) gradual merging of clusters

LVQ - Algorithm
![](images/Pasted%20image%2020230820151135.png)
![](images/Pasted%20image%2020230820151156.png)


111
<h2>Decision trees</h2>
**Definition:** 
![](images/Pasted%20image%2020230821093249.png)
A decision tree for D is a tree, where:
▪ Each inner node is labeled by an attribute Ai
▪ Each edge is labeled by a predicate (applicable to the attribute of the parent node) 
▪ Each leaf has a class label Cj

Solution of classification: 
- induct tree
- apply tree for each ti
+
▪ Easy to implement and interpret
▪ Efficient
▪ Extraction of simple rules
▪ Applicable also to big data sets
-
▪ Difficult to process continuous data (attribute categorization ~ divide the feature space into rectangular regions) → cannot be always used ▪ Example: Bank loans 
▪ Difficult to process for missing data 
▪ Over-fitting → PRUNING 
▪ Mutual correlations among the attributes are not considered

Node = Decision attributes for the division of the data set:
Predicate = label on edge
Stopping criterion = all patterns from the reduced set belong to the same class


**Induction of a decision tree – the algorithm:**
	INPUT: D // training data 
	OUTPUT: 
	T // decision tree 
	Building of a decision tree: 
	// a generic algorithm 
	T = {}; 
	determine the best criterion for division; 
	T = form a root node and label it by a decision attribute; 
	T = add an edge for each decision predicate and label it;
	FOR each edge DO 
			D´ = the data base formed due to the application of the decision predicate to D; 
			IF the stopping criterion is fulfilled for the given path 
				THEN 
						T´ = create a leaf and label it by the corresponding class; 
			 ELSE 
				 T´ = generate a decision tree ( D´);\
		     T = add T´ to the edge


**The algorithm TDIDT**  = "top down induction of decision trees". It's really a family of algorithms that covers CART, ID3, C4.5 and similar algorithms

1. Choose one attribute as a root of the partial (sub)tree 
2.  Divide the data arriving at this node into subsets according to the values of the chosen attribute and add a node for each subset
3. If there is a node such that the data arriving at it do not belong all to the same class, repeat the process for it starting from step 1; else stop

The choice of an attribute applicable to branch the tree:
- The objective: choose such an attribute, that would best divide the patterns from different classes
- Entropy
![](images/Pasted%20image%2020230821095354.png)
![](images/Pasted%20image%2020230821095433.png)
A transformation of a tree to a set of rules:
- Each path between the root and a leaf of a tree corresponds to a rule 
  - The non-leaf nodes (feature attributes) will appear (together with their value for the respective edge) on the left-hand side (in the body) of the rule 
 -  The leaf node (target class attribute) will represent the right-hand side (head) of the rule


![](images/Pasted%20image%2020230821095906.png)
![](images/Pasted%20image%2020230821100209.png)

**ID3 – Algorithm**
https://towardsdatascience.com/decision-trees-for-classification-id3-algorithm-explained-89df76e72df1
▪ Training of functions with Boolean values ▪ Greedy method ▪ Builds the tree in a top-down manner ▪ In each node, it chooses such an attribute that best classifies local training data → the best attribute has the biggest information gain ▪ The process continues until all the training data are classified correctly, or until all the attributes have been used

 ID3 Steps

1. Calculate the Information Gain of each feature.
2. Considering that all rows don’t belong to the same class, split the dataset **S** into subsets using the feature for which the Information Gain is maximum.
3. Make a decision tree node using the feature with the maximum Information gain.
4. If all rows belong to the same class, make the current node as a leaf node with the class as its label.
5. Repeat for the remaining features until we run out of all features, or the decision tree has all leaf nodes.
▪ Criterion for data division: information gain
![](images/Pasted%20image%2020230821114905.png)

**Algorithm C4.5**
https://towardsdatascience.com/what-is-the-c4-5-algorithm-and-how-does-it-work-2b971a9e7db0
A modification of the ID3-algorithm
Missing data - Ignored during tree construction (when evaluating the criterion for data division, only the known values of the given attribute will be considered)
During classification, the missing values will be estimated based on the values known for other patterns

Continuous data - The data is categorized according to the values of the respective attribute on the patterns from the training set

Pruning: 
- Validation: divide the training data into a training set (2/3) and a validation set (1/3)
- Replacement of subtrees (reduced – error pruning) by leaves labeled by the most frequent class in the respective training patterns -The new tree must not perform worse on the validation set than the original one! • Otherwise, the subtree will be not replaced
-  Subtree raising • A replacement of a subtree by its most frequently used subtree – this subtree will then be raised to a higher level

Rule post-pruning
- Inference of a decision tree based on the training set – over-training is allowed
- Prune (~ generalize) the rules by eliminating all possible assumptions if it does not impact a worse estimated classification accuracy

 Pseudocode
1. Check **for** the above **base** cases.
2. For each attribute a, find the normalised information gain ratio **from** splitting on a.
3. Let a_best be the attribute **with** the highest normalized information gain.
4. Create a decision node that splits on a_best.
5. Recur on the sublists obtained **by** splitting on a_best, **and** add those nodes **as** children of node.
![](images/Pasted%20image%2020230821134047.png)

**Algorithm C5.0:**
A commercial version of C4.5 for large databases

**Classification and regression trees – algorithm CART:**
![](images/Pasted%20image%2020230821135946.png)
![](images/Pasted%20image%2020230821140041.png)


Classification and regression trees (continued): 
      Characteristic properties of CART: 
• The order of the attributes corresponds to their impact during classification
• Missing data is ignored – and will be not counted towards the evaluation of the decision criteria 
      The stopping criterion: 
 No further division would improve classification accuracy 
  A high accuracy achieved on the training set does not have to reflect the accuracy on the test data


**Algorithm CHAID:**  Chi-square Automatic Interaction Detection

The criterion for branching: χ 2
1. Repeat, till there are just two groups of attribute values only
	a) Choose such a pair of attribute categories that are most similar one to the other from the point of view of χ2 and that can be merged 
	b) Consider the new attribute category to be a possible grouping to be performer at the given step 
2. For each of the possible groups of values, test their relevance to the predictor variable by means of the χ2 –test
3. Choose the grouping that yields the ´best´ grouping of attribute values with the most significant split 
4. Determine, if this grouping contributes in a statistically significant way to distinguishing the patterns from different classes

https://medium.com/towards-data-science/decision-tree-ensembles-bagging-and-boosting-266a8ba60fd9
Bagging ~ bootstrapped aggregating Attempts to reduce the variance of the classifier.
Here idea is to create several subsets of data from training sample chosen randomly _with replacement_. Now, each collection of subset data is used to train their decision trees. As a result, we end up with an ensemble of different models. Average of all the predictions from different trees are used which is more robust than a single decision tree

if the variance of a classifier is σ 2 , then the variance of the average of k independent and identically distributed (i.i.d.) classifiers reduces to σ 2/k

bagging does not reduce the model bias and for cases in which the bias is the primary source of error, it may even slightly worsen accuracy due to correlations between the ensemble components (and the failed i.i.d. assumption)

Random Forests
s an extension over bagging. It takes one extra step where in addition to taking the random subset of data, it also takes the random selection of features rather than using all features to grow trees. When you have many random trees.

▪ If the k different classifiers, each with variance σ 2 , have a positive pairwise correlation of ρ between them, then the variance of the averaged prediction can be shown to be ρ · σ2 + ( ( 1 − ρ ) · σ2 ) / k
▪ The term ρ · σ2 is invariant to the number of components k in the ensemble. This term limits the performance gains from bagging.

The main idea: ▪ if one tree is good, then many trees (a forest) should be better, if there is enough variety between the trees 

▪ Introduce randomness to the standard dataset – two options: 
	• Bagging - make the trees different by training them on slightly different data (bootstrap samples from the dataset for each tree) 
	• Limited number of features - at each node, a random subset of the features is given to the tree, and it can only pick from that subset rather than from the whole set. 
	This also speeds up training due to fewer features to search over at each stage and there is no need to prune the trees
 + Reduced variance does not negatively affect the bias ▪ Once the set of trees are trained, the output of the forest can be determined as the majority vote for classification.

The Basic Random Forest Training Algorithm: 
▪ For each of N trees: 
	• create a new bootstrap sample of the training set 
	• use this bootstrap sample to train a decision tree
	 • at each node of the decision tree, randomly select m features, and compute the information gain only on that set of features, selecting the optimal one
	  • repeat until the tree is complete

Parameters: 
• the number of features 
	• a subset size that is the square root of the number of features seems to be common (random forests are not too sensitive to this parameter)
 • the number of trees for the forest • 
		building trees can be continued until the error stops decreasing

**Boosting
![](images/Pasted%20image%2020230821144249.png)
![](images/Pasted%20image%2020230821144346.png)
![](images/Pasted%20image%2020230821144426.png)
