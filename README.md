# Deep Learning Challenge: Charity Funding Predictor
## Solution
Solution to predict whether or not applicants for Charity Funding will be successful based the process of Deep Learning.

## Key Artifacts and Solution
* [Jupyter Notebook for Initial Model](Code_Base/Starter_Code.ipynb)
* [Jupyter Notebook for Optimized Model](Code_Base/CharityFundingPredictor_OptimizeModel.ipynb)
* [Jupyter Notebook crazy try Model](Code_Base/Starter_Code_Crazy_one.ipynb)
* [Final_Analysis and Report on the Neural Network Model](#Final-Report)

## Background

The non-profit foundation Alphabet Soup wants to create an algorithm to predict whether or not applicants for funding will be successful. With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that is capable of predicting whether applicants will be successful if funded by Alphabet Soup.

From Alphabet Soup’s business team, you have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as the following:

* **EIN** and **NAME**—Identification columns
* **APPLICATION_TYPE**—Alphabet Soup application type
* **AFFILIATION**—Affiliated sector of industry
* **CLASSIFICATION**—Government organization classification
* **USE_CASE**—Use case for funding
* **ORGANIZATION**—Organization type
* **STATUS**—Active status
* **INCOME_AMT**—Income classification
* **SPECIAL_CONSIDERATIONS**—Special consideration for application
* **ASK_AMT**—Funding amount requested
* **IS_SUCCESSFUL**—Was the money used effectively

## Instructions

### Step 1: Preprocess the data

Using the information provided in the starter code, following the instructions to complete the preprocessing steps.

1. Read in the charity_data.csv to a Pandas DataFrame, and be sure to identify the following in your dataset:
  * What variable(s) are considered the target(s) for your model?
  * What variable(s) are considered the feature(s) for your model?
2. Drop the `EIN` and `NAME` columns.
3. Determine the number of unique values for each column.
4. For those columns that have more than 10 unique values, determine the number of data points for each unique value.
6. Use the number of data points for each unique value to pick a cutoff point to bin "rare" categorical variables together in a new value, `Other`, and then check if the binning was successful.
7. Use `pd.get_dummies()` to encode categorical variables

### Step 2: Compile, Train, and Evaluate the Model

Design a neural network, or deep learning model, to create a binary classification model that can predict if an Alphabet Soup–funded organization will be successful based on the features in the dataset. 

1. Continue using the jupter notebook where you’ve already performed the preprocessing steps from Step 1.
2. Create a neural network model by assigning the number of input features and nodes for each layer using Tensorflow Keras.
3. Create the first hidden layer and choose an appropriate activation function.
4. If necessary, add a second hidden layer with an appropriate activation function.
5. Create an output layer with an appropriate activation function.
6. Check the structure of the model.
7. Compile and train the model.
8. Create a callback that saves the model's weights every 5 epochs.
9. Evaluate the model using the test data to determine the loss and accuracy.
10. Save and export your results to an HDF5 file, and name it `AlphabetSoupCharity.h5`.

### Step 3: Optimize the Model

TensorFlow: optimize your model in order to achieve a target predictive accuracy higher than 75%.
If you can't achieve an accuracy higher than 75%, you'll need to make at least three attempts to do so.

Optimize your model in order to achieve a target predictive accuracy higher than 75% by using any or all of the following:

----
## <a id="Final-Report"></a> Final Analysis and Report on the Neural Network Model

Given below is my Final Report and Analysis of the Neural Network Model along with answers to the questions posed in the assignment:

1. **Overview** of the analysis: Explain the purpose of this analysis. 
**ANSWER** - The purpose of the model was to create an algorithm to help Alphabet Soup, predict whether or not applicants for funding will be successful.
The model was a binary classifier that was able to predict with a fairly high degree of accuracy if the funding will be successful or not.

3. **Results**: Bulleted lists and images to support findings:

  * Data Preprocessing
    * What variable(s) are considered the target(s) for your model?
    **ANSWER** - The variable for the Target was identified as the column `IS_SUCCESSFUL`.
    * What variable(s) are considered to be the features for your model?
    **ANSWER** - The following columns were considered as features for the model:
        * `NAME`
        * `APPLICATION_TYPE`
        * `AFFILIATION`
        * `CLASSIFICATION`
        * `USE_CASE`
        * `ORGANIZATION`
        * `STATUS`
        * `INCOME_AMT`
        * `SPECIAL_CONSIDERATIONS`
        * `ASK_AMT`
    * What variable(s) are neither targets nor features, and should be removed from the input data?
    **ANSWER** - The column or variable that can be removed is `EIN` as it is an identifier for the applicant organization and has no impact on the behavior of the model.
    
  * Compiling, Training, and Evaluating the Model
    * How many neurons, layers, and activation functions did you select for your neural network model, and why?
    **ANSWER** In the Optimized version of the model, I used **3 hidden layers** each with multiple neurons which increased the accuracy to <75% to 79%. The Initial model had 
    only **2 layers**. Although the number of `epochs` did not change between the Initial and the Optimized Model, adding a 3rd Layer increased the accuracy of the model.
    
    * Were you able to achieve the target model performance?
    **ANSWER** - Yes by optimizing the model, I was able to increase the accuracy from **72%** a little over **79%**.
    
    * What steps did you take to try and increase model performance?
    **ANSWER** The following steps were taken to optimize and increase the performance of the model:
     * Instead of dropping both the `EIN` and `Name` columns, only the `EIN` column was dropped. However, only the names which appeared more than 5 times were considered.
     * Added a 3rd Activation Layer to the model in the following order to boost the accuracy to > 75% :
       * 1st Layer - `relu`
       * 2nd Layer - `tanh`
       * 3rd Layer - `sigmoid`
     * It was observed that instead of both the 2nd and 3rd Layer to be `sigmoid`, when I used the 2nd Layer as `tanh` and the 3rd Layer as `sigmoid` it boosted the performance to beyond **79%**.

3. **Summary**: Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and explain your recommendation.

    **Summary and Recommendation**
      * Overall, by optimizing the model we are able to increase the accuracy to 79% (Rounded).
      * This means we are able to correctly classify each of the points in the test data 79% of the time. In other words an applicant has a close to 80% chance of being 
        successful if they have the following:

         - The NAME of the applicant appears more than 5 times (they have applied more than 5 times)
         - The type of APPLICATION is one of the following: T3, T4, T5, T6 and T19   
         - The application has the following values for CLASSIFICATION: C1000, C1200, C2000,C2100 and C3000.

    **Alternative Method**
      *This model performed very well and delivered impressive accuracy. However, I recommend considering the `Random Forest` model as an alternative, as it is also well-suited for classification problems. Using the Random Forest model, we achieved a comparable accuracy of 78%.
   

