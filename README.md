# Facial Emotion Recognition using Facial Expressions
This repository contains all the code relevant to Facial Expressions Recognition project under Brain and Cognitive Society. The goal of the project is to correctly identify 7 fundamental expressions (anger, disgust, happiness, surprise, sadness, fear and neutral).
## Dataset
JAFFE and CK+ datasets have been used.
## Image Detection & Landmark Identification
Detector and Predictor variables from the dlib library were used to identify frontal faces and plot 68 landmarks on the faces respectively.
## Face Alignment and Data Augmentation
The eye landmark features were then used to align the faces horizontally for easy cropping. The images in the training set are randomly flipped and rotated to increase the data set.
## Normalization
Normalization is performed on the cropped and rotated images to equalize the intensities. We have used the z-score normalization method here. The formula for the same is:
[(value - mean)/standard deviation]
## Downsampling
The images are downsampled to 32x32 pixels
## CNN Model (Keras implementation)
2 convolutional layers with ReLU activation and 2 max pooling layers are used. The output is then flattened into a 1600x1 vector and connected to an ANN, the output layer of which uses a softmax activation.
## Discrete Hyperparameters
We have used momentum optimiser, binary cross entropy function and accuracy as metrics. We have used ten cross validation method for evaluation of our model.
## Continuous Hyperparameters
Batch size is 16, learning rate (eta) is 0.001 and no. of epochs are 80 to 100.

