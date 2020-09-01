# DCGAN
Implementation of Deep Convolutional Generative Adversarial Network. The model is trained and tested on 2 datasets, MNIST and CIFAR-10. It is based on TensorFlow and uses Keras API for the different layers.

<p align="center">
  <img src="https://github.com/TanavShah/DCGAN/blob/master/MNIST/Result_GIF.gif" />
  <img src="https://github.com/TanavShah/DCGAN/blob/master/CIFAR10/Output_GIF.gif" />
</p>

## Generative Adversarial Network

Generative Adversarial Networks, or GANs for short, are an approach to generative modeling using deep learning methods, such as convolutional neural networks. Generative modeling is an unsupervised learning task in machine learning that involves automatically discovering and learning the regularities or patterns in input data in such a way that the model can be used to generate or output new examples that plausibly could have been drawn from the original dataset. GANs are a clever way of training a generative model by framing the problem as a supervised learning problem with two sub-models: the generator model that we train to generate new examples, and the discriminator model that tries to classify examples as either real (from the domain) or fake (generated). The two models are trained together in a zero-sum game, adversarial, until the discriminator model is fooled about half the time, meaning the generator model is generating plausible examples.

## Model Architecture

### 1. Generator Model

* The generator model takes input as 100 dimensional noise and produces an image of dimensions (28 x 28 x 1) for MNIST and (32 x 32 x 3) for CIFAR-10.
* It implements upsampling of the input by using Transpose Convolution, followed by Batch Normalization and Leaky Relu layers at each step.
* The last layer is a Transpose Convolution with tanh activation function.


<p align="center">
  <img src="https://github.com/TanavShah/DCGAN/blob/master/Model_Architecture/generator.png" />
</p>

### 2. Discriminator Model

* The discriminator model takes as input the image vector generated by the generator model and gives a single number as output. This number is an indicator for the classification of the image as fake or real.
* Each layer is a Conv2D layer, followed by LeakyRelu and Drouput Layers.

<p align="center">
  <img src="https://github.com/TanavShah/DCGAN/blob/master/Model_Architecture/discriminator.png" />
</p>

## Results

* Following is the output generated from the MNIST Dataset after 50 Epochs

<p align="center">
  <img src="https://github.com/TanavShah/DCGAN/blob/master/MNIST/Final_Output_Image.png" />
</p>

* Following is the output generated from the CIFAR-10 Dataset after 100 Epochs

<p align="center">
  <img src="https://github.com/TanavShah/DCGAN/blob/master/CIFAR10/Final_Output_Image.png" />
</p>

## Observations

### 1. MNIST

The model is trained for 50 epochs on Google Colab, which takes around 8-10 minutes to train. The images produced are quite sharp and can be classified by human eye. The model works pretty well and can generate real looking images. However, training the model for more number of epochs, does not seem to significantly improve the performance.

#### Parameters :
* Epochs - 50
* Adam Optimizer with learning rate 0.0001
* Batch Size - 256
* Output Size - (28 x 28 x 1)

### 2. CIFAR - 10

The model is trained for 100 epochs on Google Colab, which takes around 60-70 seconds/epoch to train. Some of the images produced tend to have significant amount of noise in it, while most of the images are good enough to be classified as similar to the dataset images.

The model can still be improved to produce more realistic images, by getting more data and training the model on particular labels at a time, rather than training all of them at the same time. However, this can partially deviate the use of the model from its actual expectations.

#### Parameters :
* Epochs - 100
* Adam Optimizer with learning rate 0.0002, beta_1 = 0.5
* Batch Size - 128
* Output Size - (32 x 32 x 3)

## References and Credits

* [Generative Adversarial Networks - Goodfellow et al. (2014)](https://arxiv.org/abs/1406.2661)
* [DCGANs - Radford et al. (2015)](https://arxiv.org/abs/1511.06434)
* [TensorFlow DCGAN tutorial](https://www.tensorflow.org/tutorials/generative/dcgan)
