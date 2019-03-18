# kaggle-facial-expression-recognition
This repository contains code for **"Challenges in Representation Learning: Facial Expression Recognition Challenge"** on kaggle

# Dataset
The dataset can be downloaded from : https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge/data

The data consists of 48x48 pixel grayscale images of faces. The faces have been automatically registered so that the face is more or less centered and occupies about the same amount of space in each image. The task is to categorize each face based on the emotion shown in the facial expression in to one of seven categories (0=Angry, 1=Disgust, 2=Fear, 3=Happy, 4=Sad, 5=Surprise, 6=Neutral).

train.csv contains two columns, "emotion" and "pixels". The "emotion" column contains a numeric code ranging from 0 to 6, inclusive, for the emotion that is present in the image. The "pixels" column contains a string surrounded in quotes for each image. The contents of this string a space-separated pixel values in row major order. test.csv contains only the "pixels" column and your task is to predict the emotion column.

The training set consists of 28,709 examples. The public test set used for the leaderboard consists of 3,589 examples. The final test set, which was used to determine the winner of the competition, consists of another 3,589 examples.

# Model 

Layer (type)                 Output Shape              Param #   
=================================================================
conv2d_21 (Conv2D)           (None, 48, 48, 64)        640       
_________________________________________________________________
batch_normalization_29 (Batc (None, 48, 48, 64)        256       
_________________________________________________________________
activation_29 (Activation)   (None, 48, 48, 64)        0         
_________________________________________________________________
max_pooling2d_21 (MaxPooling (None, 24, 24, 64)        0         
_________________________________________________________________
dropout_28 (Dropout)         (None, 24, 24, 64)        0         
_________________________________________________________________
conv2d_22 (Conv2D)           (None, 24, 24, 128)       204928    
_________________________________________________________________
batch_normalization_30 (Batc (None, 24, 24, 128)       512       
_________________________________________________________________
activation_30 (Activation)   (None, 24, 24, 128)       0         
_________________________________________________________________
max_pooling2d_22 (MaxPooling (None, 12, 12, 128)       0         
_________________________________________________________________
dropout_29 (Dropout)         (None, 12, 12, 128)       0         
_________________________________________________________________
conv2d_23 (Conv2D)           (None, 12, 12, 512)       590336    
_________________________________________________________________
batch_normalization_31 (Batc (None, 12, 12, 512)       2048      
_________________________________________________________________
activation_31 (Activation)   (None, 12, 12, 512)       0         
_________________________________________________________________
max_pooling2d_23 (MaxPooling (None, 6, 6, 512)         0         
_________________________________________________________________
dropout_30 (Dropout)         (None, 6, 6, 512)         0         
_________________________________________________________________
conv2d_24 (Conv2D)           (None, 4, 4, 512)         2359808   
_________________________________________________________________
batch_normalization_32 (Batc (None, 4, 4, 512)         2048      
_________________________________________________________________
activation_32 (Activation)   (None, 4, 4, 512)         0         
_________________________________________________________________
max_pooling2d_24 (MaxPooling (None, 2, 2, 512)         0         
_________________________________________________________________
dropout_31 (Dropout)         (None, 2, 2, 512)         0         
_________________________________________________________________
flatten_5 (Flatten)          (None, 2048)              0         
_________________________________________________________________
dense_13 (Dense)             (None, 256)               524544    
_________________________________________________________________
batch_normalization_33 (Batc (None, 256)               1024      
_________________________________________________________________
activation_33 (Activation)   (None, 256)               0         
_________________________________________________________________
dropout_32 (Dropout)         (None, 256)               0         
_________________________________________________________________
dense_14 (Dense)             (None, 512)               131584    
_________________________________________________________________
batch_normalization_34 (Batc (None, 512)               2048      
_________________________________________________________________
activation_34 (Activation)   (None, 512)               0         
_________________________________________________________________
dropout_33 (Dropout)         (None, 512)               0         
_________________________________________________________________
dense_15 (Dense)             (None, 7)                 3591      
=================================================================
Total params: 3,823,367
Trainable params: 3,819,399
Non-trainable params: 3,968
_________________________________________________________________


# Results 
The model is the implementation of the paper **Convolutional Neural Networks for Facial Expression Recognition** : https://arxiv.org/pdf/1704.06756.pdf and has achieved a validation accuracy of 61% and test accuracy of 62% 
