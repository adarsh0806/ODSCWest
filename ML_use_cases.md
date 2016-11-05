## Machine Learning Modeling and Use Cases, Prasad Saripalli Vice President SaaS Ops at Edifecs [Linkedin](https://www.linkedin.com/in/prasad-saripalli-69b75574) ##

prasad.saripalli@edifecs.com

### Preamble ###

* Bridging the gap between structured and unstructured data
* Book recommendations: Machine Learning with R(Packt), Data Mining(Ian Witten, Eibe Frank, Mark Hall)
* Tools: Weka

### Agenda ###

* ML pipeline
* Algorithms(KNN, K Means clustering, Association rules, Outlier detection, Decision trees, Recommendation systems)
*  Using R: Introduction, Implementing use cases

** How is the machine learning **

* Predicting variable vs predicted variable
* [ML algorithms overivew](http://machinelearningmastery.com/a-tour-of-machine-learning-algorithms/)

### Kmeans algorithm ###

* K: number of clusters
* means: average value of the features
* Randomly select 2(seed) means. How do we know what to pick? Pick it randomly. It WILL eventually converge. 
* Find the mean that is the closest to a particular data point. Cluster the points accordingly.
* Repeat the process. 


### K nearest neighbor algorithm ###

Right off the bat, the two seek to accomplish different goals. K-nearest neighbors is a classification algorithm, which is a subset of supervised learning. K-means is a clustering algorithm, which is a subset of unsupervised learning.

* In k-nearest neighbors, the k represents the number of neighbors who have a vote in determining a new player's position. Take the example where k =3. If I have a new basketball player who needs a position, I take the 3 basketball players in my dataset with measurements closest to my new basketball player, and I have them vote on the position that I should assign the new player.
* The k in k-means means the number of clusters I want to have in the end. If k = 5, I will have 5 clusters, or distinct groups, of basketball players after I run the algorithm on my dataset.


### Associate Rule Mining as a Data Mining technique ###

* Apriori algorithm, FG algorithm
* Apriori means working on something just from theoritical data without any experimental or observation data.
* It is based on SUPPORT and CONFIDENCE to come up with association rules. 
* For eg: if climate is sunny, play. if climate is rainy, dont play.
* Support: the number of instances of the items
* Confidence: the percentage over which we say it is a valid association.

** Useful R packages - ff, dbi(allows you to directly connect to database) **

** Reservoir sampling [Quora link](https://www.quora.com/What-is-an-intuitive-explanation-of-reservoir-sampling) **

** [ID3](https://www.cise.ufl.edu/~ddd/cap6635/Fall-97/Short-papers/2.htm) **







