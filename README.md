# Comparison of GAN and DCGAN on MNIST Dataset

### Summary
The goal of this project was to create a DCGAN architecture that could regularly be trained to generate new data for the MNIST dataset without suffering from severe mode collapse. I implemented two different DCGAN architectures, one with 2 hidden layers and one with 3 hidden layers. The DCGAN results were then compared to the generated images from a vanilla GAN that had no convolutions. The end result in both DCGAN cases is a model that will generate all 10 digits, achieving the central goal of this project. However, it is important to note that the distribution over the generated digits is uneven.

### Training
The training process has a few key features that help minimize mode collapse. The first most important detail is the initialization of the neural nets. The parameters of both neural nets were initialized from a Gaussian distribution. Without this initialization, there was usually severe mode collapse. The next important detail is the difference in the learning rates for the discriminator and the generator. During this project, I found that a learning rate of 0.0002 for the generator and a learning rate of 0.0001 seemed to work best for the Adam optimizer. The decreased learning rate of the discriminator meant that it was able to as easily overpower the generator. Lastly, as the goal of the project was to ultimatly train GAN's that produced all the modes, training was often stopped relatively early because as time goes on, it becomes more likely that certain modes were dropped from the generator. All of these findings are consistent with the general intuition surrounding GANs.

### Results
After training for 75 epochs, the three architectures could produce relatively high quality images. The images produced by the vanilla GAN often had small individual white pixels in areas that did not contain part of the number, which is to be expected from GANs without convolutions. This sort of behavior did not occur for the DCGAN's which is an improvement. The quality of the images for the deeper DCGAN was better than that of the shallower DCGAN. For the DCGANs especially, if we were less concerned about minimal mode collapse, we could have trained the models further. This would have resulted in higher quality images but this was not the central goal of this project.

### References
Vanilla GAN architecture:
lyeoni/pytorch-mnist-GAN (github): https://github.com/lyeoni/pytorch-mnist-GAN