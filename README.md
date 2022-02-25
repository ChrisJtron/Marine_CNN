# Marine_CNN

Goal:  Develop a model to identify individual whales and dolphins by unique—but often subtle—characteristics of their natural markings

The data set started as 37.5 GB worth of jpg images. My Local machine has only 16 GB of RAM, so I needed to find a way to reduce the data size without losing any information. I created a function to resize, grayscale, and normalize the pixel values of each image. This both prepared the data for training and reduced the size of the data file. Then I created a dataframe combining the images with their labels. This uncovered the fact that about 9,000 of the 50,000 images were mislabeled. The jpg name of the image could not find a partner jpg name in the labels.csv provided.

Using the reduced data set, I split the data into stratified test and validation sets and saved them to disk as numpy arrays. My new reduced data set size, combined with the smaller image sizes, grayscale, and normalized pixels, brough the new training data set to about 9 GB. I could now load the data, but would run out of memory when trying to manipulate it further or fit it to a model. 

I explored AWS and Google Colab as possible solutions.  While AWS would undoubtedly work, the cost would be quite high. I chose to use Google Colab Pro, which provides me with 25 GB of RAM. This is still not enough to manipulate the data as much as I would like, but I have been working around it by making one change and saving it, then uploading that data to a new notebook with a fresh 25 GB. I may need to augment the images further through rotations and/or larger sizes to get more detail, but that will require even more RAM so I will start with the 9GB set.

I have created a base-line model to classify the species with 94% training accuracy but only 67% validation accuracy. The model is overfitting, but it gives me a starting point.

Changing leaky Relu to Relu improved validation accuracy to 70%

Dense layer neurons from 3,000 to 300 reduced validation accuracy to 69%

Reducing layers from 3 to 2 convolutional and pooling reduced validation accuracy to 65%

