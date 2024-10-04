# Mnist_Dataset
Implementing Algorithms on Mnist Dataset

#### Introduction
I have used MNIST dataset in this project. The MNIST 
dataset (Modified National Institute of Standards and Technology database) is a 
large database of handwritten digits that is commonly used 
for training various image processing systems. This dataset is also widely used for 
training and testing in the field of machine learning. It has a training set which has 
60,000 examples and a test set of 10,000 examples.

#### Models Used
The machine learning models we considered are CNN with activation functions relu,
softmax, sigmoid and Decision Trees, Principal Component Analysis (PCA) and K-Nearest 
Neighbors (KNN) with both ball tree and kd-tree algorithms. These models were 
selected to explore a range of approaches from linear to non-linear classification 
boundaries.

#### Data Processing
The MNIST dataset, consisting of 28x28 pixel grayscale images of handwritten digits, requires preprocessing to improve model performance:
1.Normalization: Pixel values were scaled to the range [0, 1] to aid in faster convergence during training.
2.Flattening: Images were reshaped from 28x28 matrices to 784-dimensional vectors to create feature sets suitable for model input.
-	This code visualizes random samples from the MNIST dataset, which consists of grayscale images of handwritten digits. The script defines a list of class names representing digits 0 through 9, confirms there are ten classes.

![image](https://github.com/user-attachments/assets/3cfbc990-4214-479b-a6ab-b7da4bea72ce)

-	The images displayed in the subplots are samples of handwritten digits from the MNIST dataset, showing a variety of digits in different handwriting styles. This visualization can be useful for getting a quick understanding of the data one is working with, ensuring that the data is loaded correctly and verifying that the images and labels correspond as expected.
![image](https://github.com/user-attachments/assets/72b1cf18-9ed3-4712-b513-02a8d105e9a4)

#### DECISION TREE USING PCA
The performance of a Decision Tree classifier on the MNIST dataset using PCA consists of handwritten digit images. The dataset is preprocessed using Principal Component Analysis to reduce dimensionality while retaining 95% of the data variance. The key objective is to understand the implications of PCA on the classification accuracy of a Decision Tree and to assess its effectiveness.
Data Preprocessing: The MNIST data was loaded, with training and test splits. Images were flattened from 2D to 1D arrays. Data normalization was performed using StandardScaler to ensure each feature contributed equally to the distance calculations.
PCA for Dimensionality Reduction:PCA was applied to the normalized data to reduce the number of features while preserving 95% of the variance.
Decision Tree Classifier:A Decision Tree classifier with default hyperparameters was trained on the PCA-transformed training data.
![image](https://github.com/user-attachments/assets/09cc67e2-306f-4c0b-a5b2-4b88f01fc583)

The Decision Tree classifier achieved an accuracy of 82.56% on the PCA-reduced MNIST test set. This result is significantly lower than the performances achieved by more complex models like CNNs on the same dataset. Decision Trees may not capture the complexity of image data as effectively as other algorithms. However, it serves as a baseline and showcases the trade-off between model simplicity and accuracy.

#### KNN(K-Nearest Neighbors)
KNN stands out for its simplicity and effectiveness, especially in tasks where the decision boundary is not linear. Our exploration involved tuning various hyperparameters of the KNN algorithm, such as the number of neighbors, the weight function, and the algorithm used for neighbors search (ball_tree and kd_tree). The choice to vary these parameters is made to understand their impact on model performance and to determine the optimal configuration for our classification task.

Ball Tree: A Ball Tree is a binary tree in which every node defines a D-dimensional hypersphere, or "ball", containing a subset of the points to be searched. Each internal node of the tree partitions the data into two non-overlapping subsets which are associated with different balls. 
KD Tree - also a binary tree used for organizing points in a K-dimensional space. KD trees are effective for low to moderate dimensional spaces. Each non-leaf node in a KD Tree generates a splitting hyperplane that divides the space into two parts.

##### •	KNN for algorithm= ball_tree and leaf size=30
![image](https://github.com/user-attachments/assets/fff9ab16-07c6-4e27-9d6b-ab6e36f6b908)

According to the output, the best parameters found are n_neighbors=3, weights=distance, algorithm=ball_tree, and leaf_size=30. This combination yields the best accuracy of 0.9717.The ball_tree algorithm used in set_params is a space-partitioning data structure for organizing points in a multi-dimensional space, which is useful for efficient neighbor searches. The leaf_size is a parameter that affects the speed of the construction and query, as well as the memory required to store the tree; the optimal size depends on the nature of the problem.

##### •	KNN for algorithm= kd_tree and leaf size=30
![image](https://github.com/user-attachments/assets/c9fb4288-ab08-41c2-936f-189cc82991e4)

Based on the output,the combination of n_neighbors=3, weights='distance', and algorithm='kd_tree' with a leaf_size of 30 gives the best accuracy of  97.17%.
This indicates that the model with these parameters is the most accurate one among the tested combinations for the given dataset. The KNN algorithm is particularly sensitive to the choice of neighbors and the weighting function. A lower number of neighbors with weights based on distance can lead to a model that is sensitive to local structure and may perform better on certain datasets, which seems to be the case here. The use of 'kd_tree' is for efficient querying of nearest neighbors, especially when the dataset is large or when the dimensionality is not too high.


#### CNN-Convolution Neural Networks.
I implemented CNN using Keras, a high-level neural networks API. This particular CNN is structured for image classification and is likely applied to the MNIST dataset, a large database of handwritten digits commonly used for training various image processing systems. The activation function used are Relu, Sigmoid and Hyperbolic tangent (tanh). CNNs have become a staple for modern image recognition and classification tasks, providing an excellent example of how machine learning can be effectively utilized.

##### •	CNN with Activation function= Relu
![image](https://github.com/user-attachments/assets/da23abff-6340-4625-86a1-b9acc71e9d59)
The output indicates the training process across epochs, showing the training loss (loss), training accuracy (acc), validation loss (val_loss), and validation accuracy (val_acc) for each epoch.The model is improving over time, as indicated by the decreasing loss and increasing accuracy.The final line of the output shows the highest validation accuracy achieved, which is approximately 99.34%. This is typical of CNNs on the MNIST dataset, which are known to achieve very high accuracies.

##### •	CNN with Activation function= Sigmoid
![image](https://github.com/user-attachments/assets/ec9ff81d-381c-4f2d-8c43-41bd5a6fb3bc)
The output logs for each epoch display the training and validation accuracy and loss.We can observe that the training accuracy improves over the epochs, starting from about 93.96% and reaching approximately 98.94% by the end of the 10th epoch.The validation accuracy is consistently high, starting at about 95.77% and reaching about 98.97%, suggesting the model is generalizing well and not overfitting significantly.After training, the model is evaluated on the test set, which results in an accuracy of approximately 98.16%. This is consistent with the high validation accuracy observed during training, indicating that the model performs well on unseen data.

###### •	CNN with Activation function=Tanh
 ![image](https://github.com/user-attachments/assets/8fc89a89-f049-4e50-93c8-ceb2e63e54a3)
The training process is logged with accuracy and loss metrics for both training (accuracy, loss) and validation (val_accuracy, val_loss) after each epoch.The final validation accuracy at the end of the training is around 99.88%, and the validation loss is approximately 0.0378, indicating a high level of performance on the validation set .A final evaluation on the test set shows an accuracy of roughly 98.79%.
	
#### CROSS-VALIDATION
I performed Cross validation for the model that has given highest accuracy and improved it.
From the results of the Cross Validation we found that the 4th fold has given good accuracy score, which is 0.9896000027656555Hence that part of data can used as our improved model.


