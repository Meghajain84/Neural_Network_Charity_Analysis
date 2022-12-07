# Neural_Network_Charity_Analysis

## Overview of the analysis: Explain the purpose of this analysis
Using mchine learning and neural networks, we'll use the features in the provided dataset to create a binary classifier that is capable of predicting whether applicants will be successful if funded by Alphabet Soup.

Our dataset contains more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as the following:
* EIN and NAME—Identification columns
* APPLICATION_TYPE—Alphabet Soup application type
* AFFILIATION—Affiliated sector of industry
* CLASSIFICATION—Government organization classification
* USE_CASE—Use case for funding
* ORGANIZATION—Organization type
* STATUS—Active status
* INCOME_AMT—Income classification
* SPECIAL_CONSIDERATIONS—Special consideration for application
* ASK_AMT—Funding amount requested
* IS_SUCCESSFUL—Was the money used effectively

## Results: Using bulleted lists and images to support your answers, address the following questions.

### Data Preprocessing
* What variable(s) are considered the target(s) for your model?
    * IS_SUCCESSFUL
* What variable(s) are considered to be the features for your model?
    * APPLICATION_TYPE_{unique_value/other}
    * AFFILIATION
    * CLASSIFICATION_{unique_value/other}
    * USE_CASE
    * ORGANIZATION
    * STATUS
    * INCOME_AMT
    * SPECIAL_CONSIDERATIONS
    * ASK_AMT/ASK_AMT_GRP

In optimation notebook, instead of using **ASK_AMT** , I created the **ASK_AMT_GRP** that will categorize the amount in range, this range was saved in this column. 

* What variable(s) are neither targets nor features, and should be removed from the input data?
    * EIN
    * NAME
    * ASK_AMT (In optimized notebook)

In optimation notebook, I removed  **ASK_AMT** ; instead I created the **ASK_AMT_GRP**

### Compiling, Training, and Evaluating the Model
* How many neurons, layers, and activation functions did you select for your neural network model, and why?
    * Initially I started with input relu layer having 80 nodes, hidden relu layer having 30 nodes and output layer of sigmoid with 1 node 
    * In optimized version, I thought with more nodes I may get better performance, therefore I played with two, three or four hidden layers with nodes ranging from 15 to 100 with more nodes in first layer and slowly decreasing nodes in subsequent layers. I was hoping that with more layers and nodes, model will learn faster.
* Were you able to achieve the target model performance?
    * No, I could not improve beyond 73%. I was able to improve the first run of the model(one without checkpoints) from 53% to 64%, but the later one(with checkpoints) stayed at 72/73% despite of my many attempts.
* What steps did you take to try and increase model performance?
    * In more than three attempts to improve performance I did the folllowing- 
        * I added two/three/four hidden layers with different combinations of neuron in addition to input layer
        * I changed the epochs from 100 to 40 to 25
        * Changing the value_counts cutover to replace values as 'other' for columns APPLICATION_TYPE and  CLASSIFICATION
        * I created new column ASK_GRP_AMT categorizing the values of ASK_AMT in range instead of integer. I deleted the original column ASK_GRP.
    
## Summary: 
### Summarize the overall results of the deep learning model. 
* Relu in hidden layer with Sigmoid in outer layer worked best for me.
* Overall results suggest that increasing layers did not made an impact on model performance. Infact with 1 hidden layer model I was getting 73% accuracy over model with more than 2 hidden layers

### Include a recommendation for how a different model could solve this classification problem, and explain your recommendation.
* Next step would be to remove some of the rows that were categorized to other, for e.g. the one with ASK_AMT over 8 billion dollars
* Random forest classifier may work better 

![Total](https://github.com/Meghajain84/MechaCar_Statistical_Analysis/blob/main/deliverable2_total_summary.PNG)
