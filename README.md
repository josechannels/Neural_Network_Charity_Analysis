# Neural_Network_Charity_Analysis
## Overview of Project

### Purpose

The purpose of this analysis was to use machine learning and neural networks to predict which applicants would be successful if funded by Alphabet Soup.
To make the prediction we used a CSV file that contained information on more than 34,000 organizations that received funding from Alphabet Soup in the past.

## Results

### Data Preprocessing

1. The target variable for our model was "IS_SUCCESSFUL'
2. The variables that were considered to be features in our model were
    - APPLICATION_TYPE
    - AFFILIATION (Affiliated sector of industry)
    - CLASSIFICATION (Government organization classification)
    - USE_CASE (Use case for funding)
    - ORGANIZATION (Organization Type)
    - STATUS (Active Status)
    - INCOME_AMT (Income Classification)
    - SPECIAL_CONSIDERATIONS (Special consideration for application)
    - ASK_AMT (Funding amount requested)
3. Two identification variables were considered not to be features or target and were dropped from the analysis: EIN and NAME.

### Compiling, Training, and Evaluating the Model

1. In the original model we used 2 hidden layers (the first with 80 neurons, and the second with 30 neurons) and the 'relu' activation function for the first and second hidden layers, and the 'sigmoid' activation function for the output layer.

    ![](/Resources/original-model.PNG)

    **The accuracy of this model was determined to be 0.7221**

    ![](/Resources/original-model-eval.PNG)

2. To attempt to improve this original model we tested 5 "optimized" models:
    - In optimized model 1, I initially tested the effect on the accuracy of dropping any of the features in the original model.  None of the models tested performed better than the original (data not shown).  We then chose to drop 3 additional features that we thought may not be good indicators of whether the organization would succeed:  ORGANIZATION, AFFILIATION AND USE_CASE.  Note that layers, neurons, and activation functions were the same as in the original model.

        ![](/Resources/Optimization1-model-eval.PNG)

        **The accuracy of this model was 0.6554 - significantly worse than the original model suggesting that the three features droped contain important information to make the prediction.**

    - In optimized model 2, I added an additional hidden layer (#3) with 80 neurons and also increased the number of neurons of hidden layer 2 to 80.  The activation function for this new layer was chosen to be "sigmoid".  All other activation functions were kept the same as in the original model.

        ![](/Resources/Optimization2-model.PNG)

    **The accuracy of this model was 0.7244 -approximately the same as the accuracy of the original model.**


    ![](/Resources/Optimization2-model-eval.PNG)

    - In optimized model 3, I reverted back to two hidden layers as in the original model and changed the activation functions of hidden layer 2 and that of the output layer to "tanh":

         ![](/Resources/Optimization3-model.PNG)

        **The accuracy of this model was 0.7263 -approximately the same as the accuracy of the original model.** 

        ![](/Resources/Optimization3-model-eval.PNG)

    - In optimized model 4, I went back to the 3 hidden layers model, all layers with 80 neurons, and chose 'Tanh" as the activation function of all hidden layers as well as of the output function:

         ![](/Resources/Optimization4-model.PNG)

        **The accuracy of this model was 0.7238 -approximately the same as the accuracy of the original model.** 

        ![](/Resources/Optimization4-model-eval.PNG)

    - In optimized model 5, I kept the 3 hidden layers model, all layers with 80 neurons, and chose 'Tanh" as the activation function of all layers: input,  3 hidden layers as well as of the output function:

         ![](/Resources/Optimization5-model.PNG)

        **The accuracy of this model was 0.7249 -approximately the same as the accuracy of the original model.** 

        ![](/Resources/Optimization5-model-eval.PNG)

3.  In conclusion, despite all the effort to optimize the original model, by increasing number of hidden layers, increasing number of neurons, and changing activation functions **I was unable to improve the accuracy of the original model.**

### Summary

All neural models performed equally well with an accuracy of ~ 72%.  This may be an acceptable model for the purpose but it leaves room for improvement.  

One way to possible improve the model is by adding additional features, such as the years of experience of the directors of the organizations, or information on success of loans for the same applicant from different funding agencies.

An additional way to try to improve the prediction is to try a random forest classifier model.