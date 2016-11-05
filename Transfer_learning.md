## Transfer Learning ##
Building re usable deep NN in Azure.

Traditional ML vs DL

* TML needs manual feature extraction/engineering - DL automatically learns features
* Feature extraction for unstructured data is hard - DL is a black box technique
* DL developed in 1980 *Fukushima*, LeCun(1989) - CNN
* DL gre because of big data and powerful GPUs.
* Non deep feed forward NN(1-2 hidden layers) are not DNNs. 
* Deep CNNs - to extract representation from images.
* RNNs - to extract representation from sequential data.
* Deep Belief Network - gives you hierarchial representation of data. Eg: creating music, deep hear project at MIT. Play a piano note, music generteda roudn it. 

ConvNets

* Google photo search, OCR(extract text from image), traffic signals, face recognition
* Convolution Layer - taking a magnifying glass on image - blows up the features - filter over the image to find the activation areas.
* Pooling layer - For eg: find a fork in a image - find the activation layers in the image for the fork - 
* Max pooling - divides the slides into subregions - gets max from each sub region
* Dropout layer - randomly dropout pixels - for backpropagation to re learn new features
* Fully connected layer - helps get the labels out

ImageNet

* 1 mil natural images
* 1k labels(categories)
* How do we modify the learned weights for a specific domain. 

Common ConvNets:

AlexNet

* 8 hidden layers
* Uses Data augmentation(whitening, flips/rotations/ increases the dataset by 4 times(4 90 degree rotations on the images)), dropouts to learn new features and not overfit
* 16% error rate

VGGNet

* 19 hidden layers. Deeper the NN, better the accuracy.
* Deeper the NN, needs more data
* 7% error rate

GoogleNet

* 22 hidden layers
* Not all convolutions need be to sequential - inception model(convolutions in parallel)
* Overcomes overfitting
* Saves memory
* Saves computation costs
* 6.7% error rate

Microsoft ResNet

* 152 hidden layers
* Computationaly efficient
* 3.7% error rate

Other DLNN

* RNNs have loops, and can save the state of the prior sequence, gather knowledge
* LSTM - reserves all prior layers before it
* DBN(Deep belief network) - RBMs can be stacked to give hierarchial representations of data.
* Region Based CNN - input image - extract focus areas - RNNs applied only on focus areas - labels extracted only on focus areas
* CNN-RNN model - generates tags,captions for images 

Transfer Learning

* Lots of training data - lots of training time - learn weights from each layer - use these weights on new input
* Train on imagenet(on cats,dogs, trucks, cars) - now use this trained model to find only cats and dogs on a new dataset 

DLL frameworks

* Non symbolic - Torch, Caffe (manual and heavy)
* Symbolic - Theano, TensorFlow

GPUs in Azure

* NC6, NC12, NC24(4 NVIDIA Tesla K80 GPUs)







