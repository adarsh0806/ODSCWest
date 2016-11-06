## Machine Learning Fundamentals through the Lens of TensorFlow, Kirk Borne Principal Data Scientist at Booz Allen Hamilton ##

Machine Learning

* Finding the algorithm that learns from experience to model your data
* Experience comes from bad judgement
* Fail-fast mentality - data ops - fast iterable cycle - find out fast if this will work
* Least squares - to find a good line
* Goldilocks fit - not under/overfitting
* Use case: Find wildfires in earth satellite images using ANNs

## Ensemble Learning, ThoughtWorks ##

How to prevent overfitting?

* Define a max tree depth risking lower accuracy

Evaluation

* Confusion matrix
* F1 score = 2 * (P * R)/(P + R)

Ensemble Learning

* Bagged DTrees: split the training data into samples and create Dtrees on each.
* Ask each Dtree about a test sample - take the majority vote as the final answer that test sample
* Random forest - Each Dtree is trained on a sub set of features - majority vote on test sample
* Boosted DTree - higher weights on samples that were misclassified - adaptive boosting - weights decrease with number of iterations. The algorithm puts higher weights on misclassified data points such that in the next iteration they have to be correctly classified



