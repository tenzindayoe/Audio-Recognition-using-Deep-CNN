# Audio-Recognition-using-Deep-CNN


The data used was obtained through google speech datasets which consists of 16000 labelled wav files. 

Data Processing : 

Each .wav file was converted into spectogram using scipy. The numpy matrix was reshaped to 400x400 to reduce input space for the network. A sample spectogram from the data processor is shown below. 
![Spectogram](https://user-images.githubusercontent.com/60317553/223284765-438a51a1-3464-45d8-bdfa-8e1e4f4e0e3a.png)


Train-Test Split: 

For the 16000 labelled image, training data = 0.9 , test = 0.1, validation set = training_data(0.1) 

One hot encoders used to represent the multiclass labels. 

1. Custom Deep CNN Network. 

Consists of 4 convolutional layers attached with max pooling and dropout to prevent overfitting. The padding on each convolution was kept to "same" to allow for deeper networks. 

Dense network has 4096 nodes to capture all the features from the flattened convolution data. Dense network also has a dropout layer. 

Results : 
      This network hardly encountered overfitting. Dropout of 0.2 on all the layers produced higher test accuracy with less epochs. 
      ![CustomCNN](https://user-images.githubusercontent.com/60317553/223285418-06d4827d-b2fb-4c4e-9b31-6f65f78629c8.png)


2. Resnet CNN Network 

Unlike the custom CNN, the kernel size of the first convolutional layer is (11,11) and the kernel size drops out as we go through the layers. This allows compression of features as the image passes through the network. This network also produced high validation accuracy with lower epochs and also used less GPU power.
![download](https://user-images.githubusercontent.com/60317553/223285702-9f8b286b-5b12-4531-87e0-a8b7dca82d1b.png)

Setup : 
  For using this network, create a txt file with with the names of images and path. Put image labelled image into a folder with the name set to the label. Run the data processing code, which creates .npy file of the processed data. Run the data initializing code, and then the network. 
  
 
