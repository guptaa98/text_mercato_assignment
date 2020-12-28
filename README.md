## Model 1 - Predict AI based description for an image

## Objective
Design a model where it will take any fashion image URL and
generate an AI based description.

## Approach to build the model
1. Model is inspired from the image classification problem where unique description are stored in a list and label encoding is applied on this feature. 
2. After processing the image and text, keras library is used to build the model and predict the classes. The classes predicted for the description of the test data are stored in 'classes' list.
3. The description for each test image is the description present at the index = class predicted in the description list.

## Feature Processing
1. A description set is made where it stores all the unique Description which in our data we have 484 unique values.
2. Label Encoding is performed on Description feature of the dataset.

## Splitting the data
1. We create a numpy.ndarray 'y' and store our data.Description feature values. 
2. Using to_categorical from keras.utils.np_utils we perform one hot encoding on 'y' array.
3. Description feature is removed from the dataset and the path of the image file is modified according to the location of 'Images' folder in our machine.
4. We split our data into X_train, X_test, y_train, y_test using train_test_split from sklearn.

## Processing the image for the model
1. Create 2 list imgpath_test and imgpath_train which contain the path of image files from test and train data.
2. The images in both the data are converted into array form and are stored in x_train and x_test list.
3. These list are converted into an array x_im_train and x_im_test respectively. 
4. The values in array are normalised into a range of 0-1 by dividing all the values with maximum value in array.

## Building the model
1. Import the Sequential Model from keras.models.
2. Import the Dense, Convolutional 2D(since we have 2D images) layer, maxpooling layer (2D) and Flatten layer.
3. Then create the model by model = Sequential().
4. Add the convolutional layer. Specify the no of filters, input_size, kernel_size and activation function.
5. Add the pooling layer and specify the pool size.
6. Add a Flatten layer which converts 2D --> 1D
7. Add a dense layer, specify the number of neurons and activation function.
8. Add another dense layer which is the output layer also known as classifier, apply the softmax function.
9. Compile the model, specify the metrics, cost function and optimizer.
10. Fit the model and then evaluate and predict the class of Description and print them. 

## Model 2 - Predict the Material, pattern and neckline attribute for the same image URL input.

## Objective
Design a model where it will take any fashion image URL and generate Neckline, Material and Pattern.

## Approach to build the model
1. Model is inspired from the Image Classification problem where unique Neckline, Material and Pattern are stored in a list and then label encoding is applied on these feature.
2. Keras library is used to build the model and predict the classes. The classes predicted for the Neckline,material and pattern of the test data are stored in classes,classes_m and classes_p list.
3. The respective features for each test image is the value present at the index = class predicted in the respective feature's list.
4. Three models are built where each will predict a single feature.

## Feature Processing
1. 3 lists NL(neckline), Pt(pattern) and MT(material) are made to store the unique values. 
2. Label Encoding is performed on these feature of the dataset.

## Splitting the data
1. Three numpy.ndarray -  y(Neckline), y_m(Material), y_p(Pattern) are made and the features to be predicted are dropped from the main dataset. 
2. Using to_categorical from keras.utils.np_utils we perform one hot encoding on all the above three arrays.
3. The path of the image file is modified according to the location of 'Images' folder in our machine.
4. We split our data 3 times 1) X_train, X_test, y_train, y_test for predicting Neckline. 2) X_train_p, X_test_p, y_train_p, y_test_p for predicting pattern. 3) X_train_m, X_test_m, y_train_m, y_test_m for predicting material. 

## Processing the image for the model
1. Create 2 list imgpath_test and imgpath_train which contain the path of image files from test and train data.
2. The images in both the data are converted into array form and are stored in x_train and x_test list.
3. These list are converted into an array x_im_train and x_im_test respectively. 
4. The values in array are normalised into a range of 0-1 by dividing all the values with maximum value in array.
**NOTE - The above process is repeated for the other 2 features which are Pattern and Material** 

## Building the model
1. Import the Sequential Model from keras.models.
2. Import the Dense, Convolutional 2D(since we have 2D images) layer, maxpooling layer (2D) and Flatten layer.
3. Then create the model by model = Sequential().
4. Add the convolutional layer. Specify the no of filters, input_size, kernel_size and activation function.
5. Add the pooling layer and specify the pool size.
6. Add a Flatten layer which converts 2D --> 1D
7. Add a dense layer, specify the number of neurons and activation function.
8. Add another dense layer which is the output layer also known as classifier, apply the softmax function.
9. Compile the model, specify the metrics, cost function and optimizer.
10. Fit the model and then evaluate and predict the class of all three features and print them. 
