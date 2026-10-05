# Dementia_GAN.ipynb
GAN-based synthetic image augmentation for dementia classification — compares CNN accuracy on real vs. real+synthetic training data"


**Dementia Prediction with GAN-Based Synthetic Data Augmentation**


MSc dissertation project (Bournemouth University, Distinction) exploring whether GAN-generated synthetic images can improve dementia classification performance when real clinical imaging data is limited.


**Overview**


Clinical imaging datasets for conditions like dementia are often small, due to privacy constraints and the cost of expert-labelled data. This project investigates whether a Generative Adversarial Network can synthesise additional training images to augment a limited real dataset, and whether that augmentation measurably improves a downstream classifier's performance.



**Method**


**Baseline CNN**


Built a baseline CNN classifier trained directly on the real dementia imaging dataset, to establish a performance benchmark before any augmentation



**GAN architecture**


Generator: takes a 100-dimensional latent noise vector, upsamples through a series of Conv2DTranspose and Conv2D layers to produce a synthetic 224x224 RGB image, with a tanh output activation

Discriminator: a CNN that classifies images as real or generated, using Conv2D + MaxPooling2D blocks, dropout for regularisation, and a sigmoid output

Combined into an adversarial training loop: the discriminator is trained on batches of real and generated images, then the generator is trained via the combined GAN model to better fool the discriminator




**Augmentation & evaluation**

Generated synthetic images using the trained generator

Combined synthetic images with the real training set

Retrained the CNN classifier on the combined (real + synthetic) dataset

Compared classifier accuracy: trained on real data only vs. trained on the real+synthetic combined dataset



**Tech Stack**


Python · TensorFlow / Keras · NumPy · matplotlib · Google Colab (GPU-accelerated training)



**Files**


dementia_gan.ipynb — full pipeline: baseline CNN, GAN architecture, adversarial training loop, synthetic data generation, comparative evaluation


**Notes**

This was iterative, exploratory research work, consistent with a dissertation prototype: later cells in the notebook build on and refine earlier experiments. Some early cells reflect debugging and architecture iteration (e.g. working through tensor shape mismatches) rather than final results, worth trimming before presenting this publicly.
