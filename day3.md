## FizzBuzz for TensorFlow, Joel Grus ##

 [Blog post](http://joelgrus.com/2016/05/23/fizz-buzz-in-tensorflow/)
 
 [Code](https://github.com/adarsh0806/fizz-buzz-tensorflow)
 
 
 * Dense layer in Keras is linear regression.
 * Logistic regression in Keras is a Dense layer with the 'softmax' activation function. 
 * Relu - puts in non linearity in to the model. 
 
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
 
 * Knowledge based - search based - i search for an object - it gets logged - objects that are similar to that searched term are used. Pros: Excellent matches, no cold start issues. Cons: Static, manual tagging, will not work well with randomly changing inventories. For example: Amazons basic search
 * 