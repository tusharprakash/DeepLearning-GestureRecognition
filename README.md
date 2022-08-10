# Problem Statement

###
Imagine you are working as a data scientist at a home electronics company which manufactures state of the art smart televisions. You want to develop a cool feature in the smart-TV that can recognise five different gestures performed by the user which will help users control the TV without using a remote. 

The gestures are continuously monitored by the webcam mounted on the TV. Each gesture corresponds to a specific command:

- Thumbs up:  Increase the volume
- Thumbs down: Decrease the volume
- Left swipe: 'Jump' backwards 10 seconds
- Right swipe: 'Jump' forward 10 seconds  
- Stop: Pause the movie
 
The training data consists of a few hundred videos categorised into one of the five classes. Each video (typically 2-3 seconds long) is divided into a sequence of 30 frames(images). These videos have been recorded by various people performing one of the five gestures in front of a webcam - similar to what the smart TV will use. 
###

# Dataset

###
The training data consists of a few hundred videos categorized into one of the five classes. Each video (typically 2-3 seconds long) is divided into a sequence of 30 frames (images). These videos have been recorded by various people performing one of the five gestures in front of a webcam - similar to what the smart TV will use!
###

# Objective: 

###
Our task is to train different models on the 'train' folder to predict the action performed in each sequence or video and which performs well on the 'val' folder as well. The final test folder for evaluation is withheld - final model's performance will be tested on the 'test' set.

The project objective suggests using two types of architectures:

•	3D CNN with relu activation
•	2D Convolution followed by RNN
###

# Important Elements of the Algorithm:

###
1.	Data Generator:  
This is one of the most important part of the code. In the generator, we are going to pre-process the images as we have images of 2 different dimensions as well as create a batch of video frames. The generator should be able to take a batch of videos as input without any error. Steps like cropping, resizing and normalization should be performed successfully.

2.	Data Pre-Processing: 

Resizing and cropping of the images. This was mainly done to ensure that the NN only recognizes the gestures effectively rather than focusing on the other background noise present in the image.

Normalization of the images. Normalizing the RGB values of an image can at times be a simple and effective way to get rid of distortions caused by lights and shadows in an image.

At the later stages for improving the model’s accuracy, we have also made use of data augmentation, where we have only slightly rotated the pre-processed images of the gestures in order to bring in more data for the model to train on and to make it more generalizable in nature as sometimes the positioning of the hand won’t necessarily be within the camera frame always. We took care to not use certain augmentations like horizontal flip as that might produce a different gestures than the video is actually showing. E.g. a horizontal flip can change a left swipe to right swipe and vice versa.
###

# Observations

###
•	It was observed that as the Number of trainable parameters increase, the model takes much more time for training.

•	Batch size vs. GPU Memory:  A large batch size can throw GPU Out of memory error, so we had to do hit and trial to find the optimal value of the batch size which our  Jarvis AI GPU could support.

•	Increasing the batch size greatly reduces the training time but this also has a negative impact on the model accuracy. 

•	Data Augmentation and Early stopping greatly helped in overcoming the problem of overfitting which our initial version of model was facing. 

•	CNN+LSTM based model with GRU cells had better performance than Conv3D. As per our understanding, this is something which depends on the kind of data we used, the architecture we developed and the hyper-parameters we chose.

•	Transfer learning boosted the overall accuracy of the model. We made use of the MobileNet Architecture due to it’s light weight design and high speed performance coupled with low maintenance as compared to other well-known architectures like VGG16, AlexNet, GoogleNet etc. 
###

# Conclusions

###
Model 5 (Conv 3D with multiple layers) and Model 14 (Transfer learning with GRU) have given the best validation accuracy. Model 14 achieved a 100% accuracy on validation data and 99.9% on test data. We conclude that using Transfer Learning with pre-trained mobile net model with GRU architecture has achieved a phenomenal validation accuracy of 100 percent.
###




