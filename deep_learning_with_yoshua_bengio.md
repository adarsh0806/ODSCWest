## Deep Learning with Yoshua Bengio ##

* Geoff Hinton, Yann lecunn, Yoshua Bengio at CIFAR
* Started in 2006.
* In 2011, rectifiers was a major breakthrough.

5 Ingredients for ML towards AI:

* Lots of data
* Very flexible models
* Lots of computing power
* Powerful priors that can defeat the curse of dimensionality - if you want a learn a function in a high dimensional space we need to defeat the curse, so we need to make assumptions about the world(these are called priors). If the world is consistent with our assumptions we can defeat the curse of dimensionality. The main assumption is that the world has a compositional nature.
* Computationally efficient inference.

Bypassing the COD:

* Build compositionality into our ML models.
* Distributed represantations - different units in the NN can detect aspects of the world and we can get combinations of which units are active and which arent. Parallel way of combining features.
* Depth of the NN gives hierarchy to features.

Non distributed representations:

* Clustering, n-grams, Nearest neighbors, RBF SVMS, local non parametric density estimation and prediction, decision trees - all of these have this in common, they learn data by taking the input space and breaking it into regions(for eg, in d trees the regions are exis aligned). How do we know where to put the regions? We need parameters, examples, to define the regions(eg we use the centroid.) So we throw all of them algorithms out the window.
* Number of distinguishable regions is linear in number of parameters. There is no no non trivial generalization to regions without examples.

Distributed represantations:

* Factor models, PCA, Neural nets, Sparse codeing, Deep learning, RBMs
* We define regions based on feature detectors(binary classifiers). Take the 2d input space and output a feature space.
* Each parameter influences many regions, not just the local neighbors. 
* Number of distinguishable regions grows exponentially with number of parameters.
* Generalize non locally to never seen regions.
* Non mutually exclusive features create a large set of features.

Each feature can be discovered without the need for seeing the exponentially large number of configurations of other features:

* If each n feature required O(k) parameters, we need O(nk) examples.
* Non parametric methods would need O(n^d) examples.
* Hidden layers discover attributes that can be combined together.

Depth Prior

* Universal approximation theorem: neurons, logic gates
* Why do we need more layers? There are fxns that can be represented with a simple NN with k deep layers, but some need a very deep number of layers. 
* Deep NNs can represent fxns that 'look' complicated with a reasonable number of parameters.
* The deeoper the network, the more the pieces we get to combine. 

Local minima in Neural nets

* The training objective is not convex: the gradient methods can get stuck in local minima - MYTH.
* Yes there is an exponential number of local minima.
* Saddle points - Local minima dominate in low dimensions, but saddle points dominate in high dimensions. In some directions the cost goes down, in others it goes up.
* Most local minima are close to the global minima.
* Newtons method - zooms in on a critical point/saddle point nearby. Not  good for optimization because it is slow.

Advancements in recent years:

* 2010-12: speeach recognition error rates go from 20% to 5%
* 2012-15: GPUs can paralleize very well, 10x more data, 1000 object categories, and now in image recognition we have human level performance.
* ImageNet accuracy: 2012 it was 84.7%(started using deep learning), now it is at 96.4%. 
* Combining Natural language and computer vision: For example sees a picture of a dog near a tree and the algorithm outputs 'a dog near a tree.'

RNNs

* Selectively summarize an input sequence in a fixed-size state vector via a recursive update. 
* Take a neuron - unfold it.
* RNNs can read a sequence and convert into fixed size vector representation(compression) 
* Generative RNNs: RNN can represent a fully connected directive generative model: every variable is predicted from all the previous ones.
*  RNNs were hard to train in the 1990s.

Attention Mechanism for Deep Learning:

* Machine translation
* French to English translation - take a small NN, at each point in the genearting sequence, tells me where to look - the NN puts a score for every possible position - we take the position with the highest score - 
* 2 pointers - one in the input and one in ouput. 
* Google scale-NMT success:
* Phrase based machine translation has been around for 30 years. Google Neural Machine Translation improved on PBMT.

Deep learning: Beyond pattern recognition, towards AI:

* Recent progress: Reasoning - with extensions of RNNs. Eg: Memory networks. Combining sequential information to come to a conclusions is called reasong. For eg: Sam walks into kitchen. Sam picks up an apple. Sam walks into bedroom. Sam drops the apple. Where is the apple? Answer: Bedroom. For eg: Brian is a lion. Julius is a lion. Julius is white. Bernhard is green. What color is Brian? Answer: White. 
* The idea of searching combined with NNs gives rise to reinforcement learning.
* Planning and reinforcement learning - DeepMind, Atari, Go(game playing), Berkeley(Robotic control)

Challenge: Unsupervised learning and learning common sense autonomously

* Recent progress is mostly in supervised DL. The go player was beatedn by a machine that watched 160,000 games and learnt. Machine translations systems need trillions of data points to reach human level.
* Challenges lay in unsupervised DL.
* Benefits:
	- Exploit unlabeled data
	- Regularize - transfer learning - domain adaptation
	- Easier optimization(local training signal)
* Our current ML algorithms cheat by relying on surface statistical regularities. They are vulnerable to out of distribution examples.
* The causal relationsips between events is something ML doesn't do very well. 
* We need to learn how the world works.

Learning multiple levels of abstraction

* Higher level of abstractions disentangle the factors of variation which alloes much easier generalization and transfer.
* The abstractions are built on other abstractions. The abstractions are the underlying explanations of what is going on.

GAN: Generative Adversarial Networks

* Instead of learning a prob fxn(like RNNs) they learn directly.
* LAPGAN: Visual turing test. 
* Convolutional GANs: Strided covolutionas, batch normalization, Relu, leaky Relu












