# Marine_CNN

Goal:  Develop a model to identify individual whales and dolphins by unique—but often subtle—characteristics of their natural markings

I have augmented the images that I will be classifying. I created a function to resize, grayscale, and normalize the pixel values of each image. Then I created a dataframe combining the images with their labels. This uncovered the fact that about 9,000 of the 50,000 images were mislabeled. The jpg name of the image could not find a partner jpg name in the labels csv provided.

Using the reduced data set, I split the data into stratified test and validation sets and saved them to disk as numpy arrays. The data started at over 11 Gbs in size which caused RAM issues on my local machine of only 16 Gb RAM. I could load the data but would run out of memory when trying to manipulate it. I solved this by using Google Colab Pro, which provides me with 25 GB of RAM. This is still not enough to manipulate the data as much as I would like, but I have been working around it by making one change and saving it, then uploading that data to a new notebook with a fresh 25 GB to start. My final training data is about 9 GB in size. I may need to augment the images further through rotations and/or larger sizes to get more detail, but that will require even more RAM so I will start with the 9GB set.

I have created a base model with 94% training accuracy but only 67% validation accuracy. The model is overfitting, but it gives me a starting point.

Changing leaky Relu to Relu improved validation accuracy to 70%

Dense layer neurons from 3,000 to 300 reduced validation accuracy to 69%

Reducing layers from 3 to 2 convolutional and pooling reduced validation accuracy to 65%

