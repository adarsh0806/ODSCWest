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
* 