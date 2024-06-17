# Lesson 1 - Softmax predicts mnist numbers

I could not download the data directly from dsets.MNIST but could download the images.

Created transform that gayscales the image and transforms it to tensor.

Then, very important, I shuffled the dataset. I tried to do it later where the training and testing patches but did not work. 

Then create the softmax classifier class. Define the input and output dimension.

Visualize the initial model parameters as images. Initially they look like random noise.

Define learning rate, optimizer, criterion. Create the data loaders. You define the batch size wich is the amount of data fed at a time to train the model. 

Train the model and keep track of loss and accuracy. Loss is given by the criterion while accuracy is the number of corrects / number of tested.

After training, the model parameters look like the numbers.



