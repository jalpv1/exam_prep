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
