# GAN Project

## Overview

This project implements a Generative Adversarial Network (GAN) with the MNIST dataset. The GAN consists of two main components: the generator and the discriminator. The goal of the GAN is to generate realistic images from random noise and to distinguish between real and fake images.

## Dataset

- **MNIST Dataset:** Contains 60,000 images for training and 10,000 images for testing.

## Parameters

- **Image Channel:** All images in MNIST have `IMAGE_CHANNEL = 1`.
- **Z_DIM:** Size of the input to the generator.
- **G_HIDDEN:** Size of the feature maps in the generator.
- **X_DIM:** The original size of MNIST is 28x28, but we convert it to 64x64 for the model.
- **D_HIDDEN:** Size of the feature maps inside the discriminator.
- **REAL_LABEL, FAKE_LABEL:** Labels used to count losses in the generator and discriminator.

## Transformations

- **`transforms.Resize`:** Changes the size of images from 28x28 to 64x64 (`X_DIM`).
- **`transforms.ToTensor`:** Converts a PIL image to a tensor.
- **`transforms.Normalize`:** Used for normalizing the tensor images.

## Training

### Discriminator

The discriminator is trained to correctly classify between real and fake images using the sigmoid activation function. Its objective is to maximize the probability of correct classification, represented by:

\[ \text{Objective} = \log(D(x)) + \log(1 - D(G(z))) \]

### Generator

The generator is trained to minimize the discriminator's ability to distinguish between real and fake images. Its objective is to minimize:

\[ \text{Objective} = \log(1 - D(G(z))) \]

which is equivalent to maximizing:

\[ \text{Objective} = \log(D(G(z))) \]

## DataLoader

The `dataloader` creates an iterable within the dataset for easier access to samples. The `num_workers` parameter specifies the number of subprocesses used.

## Getting Started

1. Clone the repository.
2. Install the required dependencies.
3. Run the training script to start training the GAN.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
