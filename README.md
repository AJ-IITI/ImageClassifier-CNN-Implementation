# ImageClassifier-CNN-Implementation

This repository provides an end-to-end implementation of an image classification project using Convolutional Neural Networks (CNN). The model is trained on a custom dataset of images and is capable of predicting the labels of test images with high accuracy.

**Project Structure**

Training Data: The training data is located in the Data/Train directory, organized into subfolders where each folder represents a class label.

Test Data: The test images are located in the Data/Test directory. Each image is assigned a unique ID for prediction.

**Model Architecture**

The CNN model was designed to classify images into two categories. The model includes several convolutional layers followed by max-pooling, flattening, and dense layers. Here's a quick breakdown of the architecture:

1. Four convolutional layers with ReLU activations, each followed by max-pooling to reduce the spatial dimensions.

2. A dense fully-connected layer with 1024 units and dropout to prevent overfitting.

3. Another dense layer with 2048 units.

4. A final softmax layer for classification into two categories.



The model uses the Adam optimizer and categorical cross-entropy loss function to optimize performance.

**Layers**

Conv2D: Extracts features from images.

MaxPooling2D: Reduces the size of feature maps to control overfitting and computational load.

Flatten: Converts 2D matrices into a 1D vector before feeding into dense layers.

Dense: Fully connected layers for classification.

Dropout: Reduces overfitting by randomly ignoring some of the neurons during training.


**Data Preprocessing**

Before training, the images are preprocessed as follows:

Images are resized to 236x236.

The pixel values are normalized by dividing by 255 to bring them into the range [0, 1].

Labels are one-hot encoded using LabelEncoder to transform categorical labels into a format suitable for model training.


**Model Training**

To train the model, run the following code:

model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])
model.fit(x_train, y_train, batch_size=25, epochs=20, verbose=2)

During training, the model learns to recognize patterns in the training data, minimizing the error through the backpropagation of the loss function.

**Testing the Model**

You can use the test_on_1_img() function to test individual images from the test set. Here's an example:

test_on_1_img('example_image')

For batch testing, use the test() function, which will generate predictions for all the images in the Data/Test directory:

image_name, predicted_labels, exc_img = test(TEST_DIR)

**Output**

The results of the predictions are stored in a Pandas DataFrame, which is then saved as a CSV file:

predicted_data.to_csv('final_prediction_sorted.csv', index=False)

This CSV file contains the IDs of the test images and their corresponding predicted labels.

**Handling Errors**

There is a known issue with one test image (image_62.jpg), which throws an exception during prediction. To avoid disrupting the process, error handling has been implemented to skip over this image.

**How to Use This Repository**

1. Clone the repository:

git clone https://github.com/AJ-IITI/ImageClassifier-CNN-Implementation


2. To Download the Testing and Training Data, go through the given link https://www.kaggle.com/competitions/induction-task/data


3. Place your training and test data in the appropriate directories (Data/Train and Data/Test).


4. Run the first cell code to train the CNN model on the dataset.


5. Use the test() function to predict labels for your test images.


6. Save the results to a CSV file for further analysis.


# Generative Adversarial Network (GAN) for MNIST

This project implements a Generative Adversarial Network (GAN) to generate realistic handwritten digits using the MNIST dataset. The GAN comprises a Generator and a Discriminator, implemented in PyTorch.

**Features**

Generator: Creates realistic images from random noise.

Discriminator: Classifies images as real or fake.

Training Loop: Adversarial training for the Generator and Discriminator.

Visualization: Displays real and generated images during training.

Installation

Clone this repository:

git clone https://github.com/AJ-IITI/ImageClassifier-CNN-Implementation

Install dependencies:

pip install -r requirements.txt

Dependencies

Python 3.7+

PyTorch

torchvision

numpy

matplotlib

tqdm

Install all dependencies using requirements.txt:

numpy
matplotlib
torch
torchvision
tqdm

Usage


The script periodically displays:

Real images from the dataset.

Fake images generated by the Generator.

Loss values for both Generator and Discriminator.

**Overview**

Data: MNIST images are resized to 28x28 and normalized to [-1, 1].

Generator: Maps random noise to 28x28 images using fully connected layers.

Discriminator: Differentiates real from fake images using fully connected layers.

Training:

Discriminator learns to classify real vs. fake images.

Generator learns to create images that fool the Discriminator.

Parameters

z_dim: Latent space size (default: 100).

lr: Learning rate (default: 0.0002).

batch_size: Batch size (default: 128).

epoch: Training epochs (default: 50).

**Results**

During training, real and generated images are visualized, and the Generator improves over time.






