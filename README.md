# Paris_Housing_P3
Phase 3 Project 3 Classification- Paris Housing 
![Presentation Link](https://github.com/Dmvinedata/Paris_Housing_P3/blob/main/Phase3_Project_Presentation_DJackson.pdf) <br>

![Jupyter Notebook Link](https://github.com/Dmvinedata/Paris_Housing_P3/blob/main/p3_paris_notebook.pdf)  <br>

## Author: Deztany Jackson


# Overview

**Classification models will be built to best predict "Luxury" property for a Paris Real Estate investment agency to support leasing to potential clients.**

***
![City of Paris Buildings](https://github.com/Dmvinedata/Paris_Housing_P3/blob/main/images/paris_image.jpg)
***

# Business Understanding


Certain Paris Real Estate (RE) investment agencies are looking to invest in luxury properties (majority buildings) to lease out to Hotels, VIP guests of the city and companies for their events, employees and clients.

The primary stakeholders are real estate investment agengies because of their wide use cases, network, domain knowledge and easy access to available clients.

It is more important to correctly identify "Luxury" property as best as possible and minimize incorrectly identifying "Basic" property. This will cost having a long list of "Luxury" property but help the RE Investment agencies feel confident in the smaller set of listings.

# Data Understanding

This project uses dataset from kaggle and used for Educational Purposes "ParisHousing.csv". The intial dataset starts with 10,000 Rows of data and 18 Features (including "Category" the target value).

[Paris Kaggle Dataset, 2021](https://www.kaggle.com/datasets/mssmartypants/paris-housing-classification)

Due to data imbalance and business goal our main metrics  will be : ** Precision and F1 **

[F1 Score Metric, Joos Kortanje, 2021](https://towardsdatascience.com/the-f1-score-bec2bbc38aa6)

# Modeling

Modeling will be done interatively. As new information is learned new models, parameters and transformation techniques will be applied.

***
![Classificaiton Distribution](https://github.com/Dmvinedata/Paris_Housing_P3/blob/main/images/dist.png)
***

## Dummy Classifier

**The initial model will be a dummy model. This is a classifier predicting based on"most frequent" values and not specific patterns in the data. Therefore this should show an accuracy rate similar to someone manually randomly choosing.**

The precision average wAS .13 for the model<br>

## Simple Modeling

Logistic Regression, Decision Tree, and Random Forest are chosen as more sophisticated models compared to the Dummy classifier.  
For these models, the default parameters will be used and scored. These will establish a more credible set of baseline models.

Each model will scored on training and test data.

The primary metrics to view and evaluate models by are: Precision and f1.  Recall will be calculated too, but secondary for evaluation and used support the f1 score.


## GridSearch Pipeline w/ SMOTE and Scaling

**The next steps will be to try to apply SMOTE and scaling  to the data help with the imbalance. The scaling will best help with the Logistic Regression classifier. Scaling will not help or hurt the Decsion Tree and Random Forest classifiers.

Afterwards we will apply gridsearch to the same pipeline.

Gridsearch allows running various combinations of hyperparameters and viewing their performance. The gridsearch parameters were manually chosen. Because of resource limitations a small amount of parameter and hyperparameter options were chosen. There were attempts for hyperparamters options chosen on a spectrum. 

# Evaluation

***
![Classificaiton Distribution](***
![Best Estimator's Classification Matrix](https://github.com/Dmvinedata/Paris_Housing_P3/blob/main/images/BestEst.png)
***
## Best Estimator

- StandardScaker
- SMOTE (random_state=42, sampling_strategy=0.2)
- RandomForestClassifier (criterion='entropy',max_depth=5,min_samples_leaf=7,n_estimators=10,    random_state=42)
                                        
## Results

- Best Estimator Random Forest Average Precision: 0.52
- Best Estimator Random Forest Average F1_Score: 0.13

The precision score is similar to the best Simple models and models ran with the SMOTE & Scaled transformation from the Logistic Regression and Random Forest models classifier.

The f1_score drastically dropped around 300-400% compared the best models.

A general review of the statstics would not have made it clear GridSearch "Best Estimator" to be the best model.
However, it gives a low TP 24 (.1%), and also gives the lowest FP 20 (.1%) from the all the models. Others have higher TP and FP combined. The stakeholder has a larger "luxury" list to choose from, but introduces more chances of getting "Basic" property accidently. Therefore, this model still meets the expectations fo meeting the orginal goal. 

## Best Features 
The top 5 featureswere:

- Has_Yard
- Has_Pool
- Num_of_Guest_Rooms
- Num_of_Rooms
- Building_Size(m)

The top two features are still "Has_Yard" and "Has_Pool".  These were the same top two that were identified in the previous correlation matrix pre-modeling. 

# Conclusion

## Limitation

- Imbalanced data between "Basic" and “Luxury" properties
- Used synthetic data
- Limited computing resources
- Limited knowledge of stakeholders requirements
- No knowledge on the condition of property


## Reccomendation

- Recommend using the "best" model for a small  list of "Luxury" property listings
- Recommend looking any property that has a yard, pool and increased guess rooms.
- Recommend not using "best" model for initial, not all searches
- Recommend identifying criteria requirements for top features
- Recommend  new modeling with more than two classification values 

   

