# MNIST
Ran a deep learning model on the famous MNIST dataset. Models trained on the 60k training images and validated after each epoch on the 10k test images. The attached notebooks contain models which achieve ~99.5% test accuracy with less than 15k parameters and without the use of image augmentation.

## 1. Plain vanilla model
### Model features
* Number of parameters: 14,322
* 8 Convolution layers (3x3 convolution with relu activation)
* 1 Convolution layer (1x1) for reducing channels 
* 1 MaxPooling layer just after the 1x1 convolution
* Categorical cross-entropy loss function, Adam optimizer 
* No batch normalization, no dropout

### Results
#### After 40 epochs:
* validation accuracy peaked to 98.9%
* training accuracy hovered around 99.4%

#### After 80 epochs:
* validation accuracy remained at ~99%
* training accuracy peaked to 99.7%

**Case of overfitting. Next step: try dropout**

## 2. Model with BatchNormalization and Dropout
### Model features
* Convolution and MaxPooling layers same as above
* Added BatchNormalization after every 3x3 convolution
* Added Dropout(0.1) after every 3x3 convolution and MaxPooling

### Results
#### After 40 epochs
* Training accuracy peaks to 99.25%
* Validation accuracy touched 99.4%
Training accuracy isn't increasing much and validation accuracy is exceeding it. This suggests that there might be underfitting. Trying to reduce the number of dropout layers

**Training accuracies are not improving much so perhaps the learning rate is too high. Next step: To try varying learning rates with learning rate scheduler**

## 3. Model with LearningRate Scheduler and lesser Dropoouts
### Model features
* Retained dropouts for only 3x3 convolutions
* LearningRate scheduler added to reduce learning rate after each epoch
### Results
Trained for 40 epochs and reached validation accuracy of 99.42%


**To do: Add Image Augmentation to further improve accuracies.**

