## Recommendation Engines, Rumman Chowdhary, Metis##
 
 What is a RE?
 
 * Descriptive: Explains post event or during
 * Predictive: Uses past behavior or behavior of others to make predictions - RandomFroest
 * Prescriptive: Informed decisions on how actions should be taken based on data. 
 
 How to pick the best Recommender System for my data?
 
 * What is the existing data?
 * How quickly does the inventory change?
 * How mch information can we get(Explicit and Implicit)? Cookies are really useful
 * Does the model need to scale? The more matrix factorization, the more time we need. 
 
 Kinds of RE
 
 * Knowledge based - search based - i search for an object - it gets logged - objects that are similar to that searched term are used. 

	Pros: Excellent matches, no cold start issues. 
 
 	Cons: Static, manual tagging, will not work well with randomly changing inventories. Cannot asses tengentially related things. For example: a cordless vacuum search - relates to a mop. If you search for peanut better - should  recommend jelly. For example: Amazons basic search
 * Content based - items mappes to item-feature space an recommendations are based on specified characteristics - cordless vaccum falls under home cleaning
 	
 	Pros: good with tangential relations
 	
 	Cons: cold start problem, need good descriptions, need item ratings
 	
 	For example: Search for ai vs AI(ai is the japanese word for love), mit vs MIT. Document searches(jstore) are usually content based. 
 	
 * Collaberative filtering: based on user and item similarity. 
 
 	Pros: can provide less obvious matches. 
 	
 	Cons: cold start problem for new users and new items, requires a feedback rating system
 	
 	For example: given that you are similar to a user, return results that use that information.
 	
 Limitations
 
 * Recommendation systems have to update immediately
 * You have more information than you think using - existing item popularity, geography based in ip address, cookies
 

### How does Content Based RE work: ####
 
 * NYTimes - each article has tags assigned - they use the tags of the articles you have read to suggest new articles
 * Users and Items are represented by vectors in a feature space:
 * Map users and items in the same feature space and compute distance between them
 
 Example: Features: big box office movies, aimed at kids, famous actors
 
 Finding nemo = 5,5,2
 Jiro Dreams of sushi = -4,-5, -5
 
  Ratings for user: 
 
	(-3, 2, 2)
 
 Predicted ratings:
 
 	(-3 * 5 + 2 * 5 + 2 * 2) = -9
 	(3 * 4  - 2 * 5 + 2 * 5) = +12
 
* Create feattues form user+item pairs and use an algorithm(classifier) to predict like and dislike
* Each user/item pair has a labeled outcome such as purhcased/not purchased. You can train a model to predict purchase behaviour. 


### How does Collaberative Based RE work: ####

* Using item and user similarity
* Users(480k rows) by Movie(18k columns) matrix

Method 1: 

* Items/memory/neighborhood based: create item-item matrix - recommend items that are similar to what a user has rated
* Doesn't scale well
* Most people don't rate movies
* You need a fully populated item-item similarity matrix. We need to know how each of these movies relate to other movies.
* Doesn't work well with a dynamic inventory that changes a lot.

Method 2:

* Model based - use matrix decomposition via a SVD(singular value decomposition) to reduce dimensionality and extract latent variables
* We express users and items in terms of these variables.
* Scalable, felxible, accurate, domain independent, requires no explicit information
* Drawbacks - cold start, sparse data

Cold start

* Build an initial profile based on explicit feeddback
* Hybrid filtering - use content based information - how much do you like country/edm/classic rock music up front.

Sparsity of data

* Long tail problem - those movies that are rated are rated constantly
* No rating data for many users

Granularity

* Traditional CF methods work well for non binary data - not as well for binary(click/non click, buy did not buy)

Measurement

* Non binary rating - Pearson correlation coefficient, Euclidean, Manhattan
* Binary - Jaccard, cosine(good for text vector mapping)

Defining the model

* Normalization - Some items are higher rated(oscar winners) - some users are lower raters from the norm - ratings can change over time. Normalize based on user(some movies are oscar winners and everyone rates them high. cult movies have ratings shoot up over time) and based on item(some users are grumpy all the time, some are happy all the time). Create an offset per user and offset per item. Example - mean rating across all users for item x is some value - how does it differ from the mean rating across all items
* Capturing data trends - model the distributions - movie data is bimondal 
* Feature importance
* Feature generation - classify users base don demographi
* Temporal factors - seasonal shifts - anchoring(when v2 comes out, checking based on the previous rating of the same item.)

