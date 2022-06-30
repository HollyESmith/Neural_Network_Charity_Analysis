# Neural_Network_Charity_Analysis

## Overview

In this exercise, I work for a nonprofit philanthropic organization that has raised and donated several billion dollars over the years. Not every donation that the foundation made was impactful, and the organization wants to make sure that future donations will be used effectively. I have been asked to predict which organizations are worth donating to and which are too high risk. This problem was determined to be too complex for statistical and machine learning models, so I will design and train a deep learning neural network model to evaluate input data and produce a clear decision-making result.

## Results

Note that the definition of the variables was given as:

![variable defs](https://user-images.githubusercontent.com/97558998/176720207-e1fc452e-4f27-457c-9da4-ae167acf0eef.png)

### Data Processing

- What variable(s) are considered the target(s) for your model? The IS_SUCCESSFUL variable was the target for this model.

- What variable(s) are considered to be the features for your model? The feature variables were APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, INCOME_AMT, and ASK_AMT.

- What variable(s) are neither targets nor features, and should be removed from the input data? Variables EIN and NAME were removed, as they do not substantially contribute to the model. STATUS and SPECIAL_CONSIDERATIONS were removed for the optimization attempts as these affected less than 1% of the dataset.

### Compiling, Training, and Evaluating the Model

-	How many neurons, layers, and activation functions did you select for your neural network model, and why? 

In the initial run, I had one layer with 30 nodes and a second layer with 20 nodes. I selected the number of nodes based on the rule of thumb that when building the initial model, you should use 2 to 3 times as many neurons as there are features. The initial model contained 9 features; 9 x 3 = 27, 9 x 2 = 18, thus I rounded up to 30 and 20 nodes. However, that yielded a lost rate of 0.78 and an abysmal 52% accuracy.

** Optimization **
Next, I made three attempts at optimization.

First, I dropped 2 more columns, “STATUS” and “SPECIAL CONSIDERATIONS.” When reviewing the .csv file I determined that these columns contained the same data for >99% of all records, thus not being very useful. Now, I have 7 features instead of 9. I also binned the ASK-AMT and USE_CASE features. 

** 1st attempt **
I ran the dataset, still using two layers, but now with fewer features. I changed the number of neurons, rounding to 20 (7x3=21) and 20 (7x2=14). This time the accuracy rate was 58%, a slight improvement over the initial model, but the loss rate increased to 1.9.

** 2nd attempt **
I kept the number of nodes at 20/20 and added a third layer with an arbitrarily chosen 10 nodes, which resulted in a slightly increased accuracy rate of 59% and a slightly decreased loss rate of 1.68.

** 3rd attempt **
Because the accuracy rate didn’t change much with the increased layer, I reverted to two layers, doubled the number of nodes to 60/40 and changed the activation function from “sigmoid” to “relu”. This resulted in the accuracy rate increased to 64%, but the loss rate increased to 4.7.

** Bonus attempt **
Out of curiosity I wondered how a larger number of nodes would result, so I made one more attempt using 2 layers of 120 and 80 nodes with a sigmoid activation. This was a total bust, as my loss rate almost doubled to 8.9, and the accuracy rate decreased to 60%.

-	Were you able to achieve the target model performance? I did not achieve the targeted model performance of 75%. Dropping 2 features increased the accuracy level to approximately 58%; changing the activation function to 'relu' increased accuracy at the expense of loss rate. I was unable to optimize any further.

-	What steps did you take to try and increase model performance? Steps taken to increase model performance included dropping features, adding layers and nodes, as well as using a different activation method.

## Summary

Here is a summary of the results. The most accurate model was Attempt #3, where I used the relu activation. However, the loss percentage is unacceptably high. Additional adjustments to future models may include increasing the number of layers while also experimenting with a larger number of neurons. I also recommend attempting different activation methods, such as tanh or Leaky ReLU.

![results](https://user-images.githubusercontent.com/97558998/176722804-a866c6bf-9cc3-42c7-ae70-af6f91710d1f.png)

