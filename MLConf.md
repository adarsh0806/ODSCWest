## Deep Learning with Rajat Monga, Creator of TensorFlow

* Parameter server - parameters, updates on a different server
* Model runs on a worker
* Distribute parameter server
* Parallelize input batch
* Portability - DL runs on CPU,GPU,TPU, Android, iOS, Raspberry Pi
* ML gets complex quickly - Heterogenous systems, Distributed systems, Modeling complexity
* TensorFlow - abstracts Heterogenous systems, Distributed systems, Modeling complexity
* Parallelism in Op  - DataFlow graphs, MatMul
* Matrix -> Split -> Matmul
* [Tutorial](https://www.tensorflow.org/versions/r0.11/tutorials/index.html)

## Neural Turing Machines, DANIEL SHANK, DATA SCIENTIST, TALLA

* Neural Turing Machine - NN controller that learns from sequence had has persistent memory
* Similar to RNN - can be fed continuous input 
* NTM are differentiable Turing Machines
* NTM smooth functions - Smooth analogs
* NTM can - generalize, language modeling(autocomplete, guessing a word from a sentence), does well at bAbI dataset from Facebook
* bAbI - series of stories followed by questions that need reasoning to answer [bAbI](research.facebook.com/research/babi)
* Need to make logical inferences + relevancy 
* Problems - Architecture dependent, large number of parameters, doesn't benefit much from GPU acceleration(because its sequential, hence its hard to parallelize), hard to train
* Hard to train - numerically unstable(they tend to make large mistakes and not small mistakes, because the error is made in the algorithm set up)
* Using memory is hard - need to know what to forget when using RNN
* Gradient clipping - limit the degree to which we change a parameter in a model that doesn't seem to work
* Loss clipping - put a cap on how much we can change the loss function. Used in addition to gradient clipping
* Graves' RMSprop - extension of backpropagation - it smooths out gradients - instead of taking an average it takes a running estimate of the variance - extreme values of loss don't decay the parameters much
* Adam optimizer - smooths gradients 
* Attention to initialization - poor init can prevent convergence - have to play close attention to starting value of memory
* Short sequences first - feed in short training data - when loss its target, increase size of input - repeat process. This is called curriculum learning

Dynamic Neural Computers addresses these concerns

* Similar to NTMs except - no index shift based addressing - can allocate and deallocate memory - remembers recent memory use(temporal memory, they can walk back the linked list)
* Logical inference + fuzzy reasoning

## Using Deep Reinforcement Learning for Dialogue Systems, Harm van Seijen

* Current chatbots -> user - nlp - state stracker(dialogue state) - policy manager (system act)- nlgeneration - user
* What is Reinforcement Learning - data driven approach towards learning behaviour 
* RL + DL
* RL vs SL: SL - hard so specify function, easy to identify correct output. example: recognizing cats
* RL: hard to specify function, hard to identify correct output, easy to specify behaviour goal. example: double inverted pendulum. 
* Advantages od RL: does not require knowledge of a good policy - does not require labelled data - online learning i.e. it adapts the changes in the environment in real time
* Challenges for RL - requires lots of data, sample distribution changes during learning(the policy changes during learning as well), samples are not IID(they are strongly related)

Solution strategies for RL:

* How to find a good policy for RL?
* RL is modelled as a Markov Decision Process
* RL bootstraps  - Temporal Difference Learning
* Deep RL: RL where you use DL to estimate Q values - based on 2015 Nature paper from DeepMind called DQN
* Uses 2 networks - target network updated slowly to slow the variance for better stability

Applying RL to Dialogue systems

* User simulator trained on offline data  - to mitigate the 'lots of data needed to train' issue
* Exact state is not observed - belief state is used
* Belief state spaces are discretized to summary state space - needs domain knowledge
* Deep RL can generalize and hence we dont need the summary state space.
* Summary - can be used for online learning - does not need knowledge of good policy

## Netflix asset optimization, Netflix

* Discrete explore-exploit
* Continuous explore-exploit

## Before the model, Elena Grewal, AirBnb

* Partial mapping
* Data process -> Sizing oppurtunity and scope - model architecture - data pipelines and processing - model optimization - product implementation & evaluation
* This talk is about Sizing oppurtunity and scope - model architecture
* Step 1: Need the right target metric that needs to move
* OKR - the metric you are trying to move
* Pricing recommendations - example of focused right target metric
* Step 1: make the case for the metric - highlight all the ways the metric matters - price filter usage, variations by market. Project can take 6 months
* Find the most important features for that target metric - for airbnb it was 'value' of listing
* Step 2: Model architecture - before - use location, listing characteristics, recency - this mimicked host behaviour
* Step 2: Model architecture - after - new metric is bookings - lets use price as a feature to predict booking - price suggestion based on prob of being booked on agiven day - added model layer for adoption of prices
* Learnings - target metric - up front analysis of potential impact of ML product - study user behaviour

## Amazon Search, Daria Sorokina

* 200 trees - 150 features(only 20 used) - 100 ML models - Gradient booted trees with pairwise ranking
* Training labels - collected from user logs - positive labels are clicked, added to cart, purchased - negative labels are idnored results(product shown, but no action), random sample from whole match set(the model needs to see what the customer has not seen)
* What targets to use? - probably not purchases
* Training targets - mixing click and purchase targets 
* Fast Feature selection - 2 stage feature selection: a. choose al features that scored better than random b. use backward elimination and forward selection
* Scroing features in ensemble of trees 
* Continuous features provide more possible splits - tree is likely to choose the continuous feature over the binary feauture even if its useless
* Fix for this problem - [Code](github.com/dariasor/TreeExtra)

All product search:

* Query category score
* Hunger score
* In-category relevance score for each product

Match set

* Behavioral matches - using online behavioral features
* How do non text matches happen - using behavioral features
* Cold start problem - day 0 has all behavorial features at 0 - day 7 behavioral features are picking up too slow

Non Relevance Sort

* Search tv - sort by average customer review - results for tv cloths show up
* Solution - calculate {query, product type} score - filter the match set by top product types

## Personalized Content Blending In The Pinterest Homefeed, Pinterest

* 10 billion pins a day - 150 million monthly users
* New content  - source recommendations - ranking model
* New content - social recommendations - ranking model
* 2 different ranking models - why? - to parallelize model development - different content types have different important features - different content types might have different objective functions - easy to add new types of content

The Blending problem

* Combine results from pools into one sorted feed
* Constraints - scores arent comparable across the pools - must maintain ranking for each pool - 
* Desired traits of a good solution - users with significant history should see more of the content types they prefer - we should be able to train new users and tune from there

Which model for the Blending problem?

* Fixed ratio model - take the top ranking results from the pools 
* Calibrate ranking models 
* Multi armed bandit model -each arm of the bandit represents each pool 
* Sampling technique - we dont get feedback after sample - sample content in batches - use Thompson sampling technique - map pool affinities onto an integer ratio
* Data - positice actions, negattive actions, views of item
* Beta distribution - good for binary outcomes - positive action, negative action
* Response distribution - each action type has its own beta distribution and is weighted by the rewards
* How do we deal with new users - prior distribution - for new users they see some of each of the types of content in every page
* Sampling technique - take the expected value of the pool utilities on the integer ratio

## A General Framework for Communication-Efficient Distributed Optimization, UCBerkeley

Distributed Optimization

* Mini Batch - convergence gurantee - tunable communication
* Mini batch limitations - one off methods - stale updates - average over batch size
* CoCoA-v1 - primal dual framework - immediately apply local updates - average over K(strictly less than the batch size)
* Primal dual framework - default in liblinear package
* Immediately apply updates - change in for loop to apply update before end
* CoCoA-v1 limitations - can we avoid having to average the partial solutions - L1 regularized objectives not covered in initial framework, L1 encourages sparse solutions(works well when the feature space is large), includes Lasso, sparse logistic regression, elastic net - beneficial to distribute by framework
* Solution - solve primal directly - default software package is glmnet
* [CoCoA](gingsmith.github.io/cocoa)

## Interpreting Black-Box Models with Applications to Healthcare 

* [Repo](https://github.com/numeristical/introspective)
* [Docs](http://ml-insights.readthedocs.io/en/latest/)

## Personalization and Scalable Deep Learning with MXNET , ALEX SMOLA, MACHINE LEARNING DIRECTOR, AMAZON

* Latent Variable Models:
	- Temporal sequence of observations - purchases, likes, ad clicks, queries
* Latent state to explain behavior	
	- Clusters(navigational, informational queries in search)
	- Topics(interest distributions for users over time)
	- Kalman Filter(trajectory and location modeling)
* LSTM for survival analysis

## A Friendly Introduction To Causality, ALEX DIMAKIS, ASSOCIATE PROFESSOR, DEPT. OF ELECTRICAL AND COMPUTER ENGINEERING, UNIVERSITY OF TEXAS AT AUSTIN

* [Tetrad Project](http://www.phil.cmu.edu/projects/tetrad/)

## Using Bayesian Optimization to Tune Machine Learning Models SCOTT CLARK, CO-FOUNDER & CEO, SIGOPT

Why is tuning ML Models hard?

* neon.optimizers.optimizer.RMSProp()
* scikit-learn optimizers - gridsearch, randomsearch - takes a time consuming problem and does a brute force exhaustive search
* Bayesian optimization - efficiently find a global optima
* Optimize objective function - loss, accuracy, likelihood
* Given parameters - hyperparameters
* Find the best parameters - sample function as few times as possible

How does it work?

* Gaussian Process - stochastic regression function

Evaluating the optimizer

* Area under curve
* Benchmark suite - optimization functions (Branin, Ackeley, Rosenbrock), ML Datasets (LIBSVM)
* Infrastructure - AWS cluters
* Viz tool - Best Seen Traces
* Metrics - stochasticity - Mann-Whitney test for significance
* First Mann-Whitney U tests using BEST_FOUND - AUC

[Slides](http://www.slideshare.net/SigOpt/mlconf-2016-sigopt-talk-by-scott-clark)

##  Several People Are Tuning: Data and Machine Learning at Slack JOSH WILLS, HEAD OF DATA ENGINEERING, SLACK

* Prod - MySQL, Solr, Redis
* Data warehouse - S3, Hive, Spark, Presto, MySQL
* WebApp - Apache, PHP
* Logs via kafka sent from the webapp to the data warehouses
* Prod communicates with the warehouse through Sqooper
* MLE - MLE who enjoy working on ML problems, people who haven't done ML and who don't know how terrible the job is
* Airflow
* OODA - observe, orient(come up with metrics), decide, act(build models, optimize, hyperparameter tune)
* Searchable log of all knowledge and communication - slack
* Hulk model - build a giant batch model and serve it statically - refresh every 24 hours
* Parquet, airflow, caravel, quiver(key value serving model) - useful tools

## Why Machine Learning Algorithms Fall Short (And What You Can Do About It) JEAN-FRANÇOIS PUGET, DISTINGUISHED ENGINEER, MACHINE LEARNING AND OPTIMIZATION, IBM

* Data - Data Scientist - ML algorithm(R, GBM(XGBOOST), Spark ML) - Model - $$$$$
* Data - data prep - ML algo - model - deploy - predict - $$$$$
* [IBM Data Science Experience](http://datascience.ibm.com/)
* ML models with mathematical optimization(picture)
	- Linear Model
	- SVMs
	- Decision Trees
	- Multi label classification
	- Alternating least squares
* ML models that use mathematical optimization need to mathematical techniques.

## Sentiment Analysis, Walmart

* VADER - Valence Aware Dictionary and Sentiment Reasoner - [Repo](https://github.com/cjhutto/vaderSentiment)
* VADER is sensitive to adverbs, punctuation, emoticons, nuances
