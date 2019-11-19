print(score) output
* [0.03342232405357299, 0.9912]


Definitons:

* Convolution: The operation in which we overlay an given image and derive the significant features of the same in a reduced dimension.
* Filters/Kernels: The mask we apply on the image to identify the features
* Epochs: Each epoch is one complete run over which the algorithm sees all the training inputs and learns. We train the algorithm over multiple such runs known as epochs.
* 1x1 Convolution: This results in reducing the number features and hence speed up the computation.
* 3x3 Convolution: This is used to identify the basic features
* Feature Maps: Each layer in a CNN results in a collection of features. This is called a feature map.
* Activation Function: A function which helps in either enhancing or supressing the pixel (neuron).
* Receptive Field: As we add more layers each nueron in a layer has visibility to a higher number of nurons(pixels) of the lower layer. This is what we term as receptive field.
