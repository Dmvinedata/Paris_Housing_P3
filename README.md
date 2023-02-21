# Paris_Housing_P3
Phase 3 Project 3 Classification- Paris Housing 
![Presentation Link]() <br>

![Jupyter Notebook Link]()  <br>

## Author: Deztany Jackson


# Overview

**Classification models will be built to best predict "Luxury" property for a Paris RE investment agency to support leasing to potential clients.**

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
![Classificaiton Distribution](https://github.com/Dmvinedata/)
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
![Classificaiton Distribution](https://github.com/Dmvinedata/)
***


## Best Estimator

Pipeline(steps=[('ct', StandardScaler()),
                ('sm', SMOTE(random_state=42, sampling_strategy=0.2)),
                ('rf',
                 RandomForestClassifier(criterion='entropy', max_depth=5,
                                        min_samples_leaf=7, n_estimators=10,
                                        random_state=42))])
                                        
## Results

Best Estimator Random Forest Average Precision: 0.52
Best Estimator Random Forest Average F1_Score: 0.13

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

- Imbalanced data between "Basic" and "Luxury" limits accurate and useful metrics
- With data amount and imbalance, synthetic data was created. It only is a limited representation of the real data.
- Limited computing resources, limit parameter and model combination computations 
- Limited knowledge of stakeholders specific requerements
- No knowledge on the condition and grade of the proper. Especially since "Basic" and "Luxury" property has many overlapping similarilys

## Reccomendation

- Recommend using the "best" model if satisfied with a small list of "Luxury" property listings, which includes a small error chance
- Recommend looking into predicted "Basic" and "Luxury" property that has a yard, pool and increased guess rooms.
- Recommend not using the chosen model to base final searches on, better for initial. The distribution is too small. 
- Recommend identifying criteria requirements for top features and increasing the chances/error of a "Basic" property being chosen. 
- Recommend changing classification from binary of "Basic and Luxury" to multi-classification  with more than 3 gradients
   

