# KModes-and-Working-with-Mixed-Datasets

Categorical Data
If all of our data is categorical, can we replace the categories with
dummy variables and then use the above metrics?
◦ model.matrix() will do this, but remember dummy variables have a base
case – we do not get a variable for every category, and we may need
this
Use acm.disjonctif() in package ade4
◦ Gives a binary variable for all factors
◦ But need all data to be categorical

K Modes
There is an algorithm called “Kmodes” which works with strictly
categorical data …
Invented by Huang in 1997
Implemented in the klaR package in R
Very similar to K-Means; set number of centroids, computes distance
differently

Mixed Data – Gower Metric
What if our data has a mix of numeric and categorical variables?
There is a distance metric called “Gower” that is designed to handle this
It is implemented in a couple of packages:
◦ vegdist() in the vegan package – also does other metrics
◦ daisy() in the cluster package
For each variable type, a particular distance metric that works well for that type
is used and scaled to fall between 0 and 1.
Then, a linear combination using user-specified weights (most simply an
average) is calculated to create the final distance matrix

More Metrics
Jaccard is similar to binary – can be done using the vegdist() function
in vegan package
For string data, can use an “edit distance” function
◦ The function in R is called adist(x,y) – give it two strings
◦ Can be useful for creating dissimilarity matrix for data with char values
◦ But all data would need to be chars
Also possible to do a correlation dissimilarity
◦ The function is corDist(), and is in the MKmisc package
◦ Note correlation can be negative, so need to be careful with linkage
(Ward)


Clustering: Summary
Know your data: numeric, categorical, mix?
If all numeric, can do K-means of Hclust
◦ Can use dist() to create distance matrix with different metrics
All categorical?
◦ Use ade4 to convert to binary
◦ Use dist(), vegdist(), daisy() to create dissimilarity matrix
◦ Kmeans or Hclust will work
◦ Can also do K-modes
Mixture?
◦ Use Gower metric 
