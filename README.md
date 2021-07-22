# Neural_Network_Charity_Analysis

## Overview of the analysis: Explain the purpose of this analysis.
The purpose of this analysis was to use a deep learning model to solve a binary classification problem. The data set that we used contained information on whether or not organizations were successful with the donations they recieved, and information about their application. We preprocessed the data by loading it into a pandas dataframe and dropped unneeded columns, binning data in columns to reduce the number of unique values, encoded object datatypes, split our data into features and target arrays, then fit and scaled the data.

## Results: 
### Data Preprocessing
 - Our `IS_SUCCESSFUL` column was our target for our model.
 - Before encoding the columns that were object datatypes, our features used were: `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`, `STATUS`, `INCOME_AMT`, `SPECIAL_CONSIDERATIONS`, and `ASK_AMT`. For the columns that were `object` datatypes, we encoded these columns using the OneHotEncoder() function.
 - The columns that were neither targets nor features were dropped. These were the `EIN`, `NAME`, and the original columns that were encoded.

### Compiling, Training, and Evaluating the Model
 - For our neaural network, we used two hidden layers with 80 and 30 neurons, respectively. The activation function for the hidden layers used was ReLU, and Sigmoid for the output layer. ReLU is computationally efficient, and other activation functions did not improve the accuracy and Sigmoid works well for binary classification problems.
 - The target accuracy was 75%, and our initial neural network was only able to achieve 72.6% accuracy.
 - To try to reach 75% accuracy, we removed noisy variables from features, added additional neurons and layers and tested different activation functions and optimizers. After this, we were still unable to reach 75% accuracy, so we used the KerasTuner to try to get a set of hyperparameters that would reach 75% accuracy. This also could not reach our target accuracy, so we instead attempted to intentially overfit the model. Using two layers with 300 and 250 neurons, respectively, and training on 99% of the dataset we were able to achieve 76.7% accuracy. Although this model is overfit, learning how to overfit using dataset will help to avoid overfitting in the future.

 Shown below is the accuracy and loss of the model before and after overfitting, respectively.

<img width="400" alt="before overfitting" src="Images\beforeOverfitting.png">
<img width="400" alt="after overfitting" src="Images\afterOverfitting.png">

## Summary: Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and explain your recommendation.
The results of the deep learning model imply that it was most likely not the best solution for this problem. Even after intentionally overfitting, the accuracy of the model only slightly improved. However, there are different tools that can be used to solve a binary classification problem, such as logistic regression, support vector machiens, decision trees, and k-nearest neighbors. While each has their pros and cons, each can be quickly implemented and tested to see if they have better accuracy than our deep learning model.