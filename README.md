# Please note Read ME is incomplete.  I wanted to submit before deadline but will work on the readme over the weekend


# Analysis of Insurance Data - Beware the Young and the Old Guy in the Convertible
Author: David Burns <br>
Date: 11/17/2022

## Business Problem
The goal of this project is to explore car insurance data to determine the factors that will lead to insurance claims.

### Data
The initial data contained 10,000 rows of data and 18 columns of variables that could impact sales and 1 column of 'outcome', or claim data.   The original source of the data is on Kaggle.  The target of the data is whether or not person files a claim. The notes say "The outcome column indicates 1 if a customer has claimed his/her loan else 0" I take this to mean that a 1 is a total loss resulting in the person filing a claim to pay off the car loan.

## Methods
I first examined the data and cleaned up some obvious errors. Most of the data was categorical which I ordinal encoded.  I visually inspected the data and discovered missing data points in credit score and annual miles.  

We did exploratory data visualization analysis of: 

1)  HEAT MAP - I looked at a heat map and noted correlations. Accident outcome was negatively correlated with age and driving experience and not much else.  I inputed missing values by grouping by age which was correlated with the missing values.
2)  Some graphs of Age v. Claims, Driving Experience v. Claims, etc.


### Examples of the visualizations

![Screen Shot 2022-11-17 at 10 42 22 PM](https://user-images.githubusercontent.com/113855848/202638132-c86351c9-0937-4bd7-9678-6cb0e58e6aa3.png)

Age is negatively correlated with accidents.  It is also positively correlated with driving experience, DUIs, marriage, kids, and speeding tickets.  It looks like the data is cumulative over a drivers life.  I would recommend that these items sunset after a time.


![Screen Shot 2022-11-17 at 10 43 58 PM](https://user-images.githubusercontent.com/113855848/202638345-f496b2d8-265c-4648-a2f1-75a191fe612e.png)

Driving experience is also strongly negatively correlated with crashing ones car.  Of course, age and driving experience are also positively correlated.

These two factors were the most strongly (negatively) correlated with accidents.

## Model

I ran several (trained) classificaiton models and an (untrained) segmentation model.  I ran them all several times and varied parameters, dropped data, imputed it different ways. etc.  The classificaiton models I ran were logistic regression, random forest classifier, K N Neighbors, XGB Classifier, LGBM Classifier, Gradient Boosting Classifier.  

## Clustering Analysis

Age and driving experience are the driving factors in predicting whether or not someone will have an accident. That is, the older and more experience one has driving, the lower the probability that one will have an accident.

As I noted before, as you get older, your income, credit score, chance of being married, children, etc all go up. However, so does your number of speeding violations, DUIs, and past accidents. I would recommend that the insurance company limit these items to a limited look back - i.e. violations drop off your record after a certain amount of years.

Gender, race, and vehicle type seem to have little correlation with wrecking your car. However, I left them in the analysis due to a couple of interesting findings.

First, adding race functionally duplicated the clusters without adding much additional value. Cluster 1 and 4 are essentially young people, white and minority respectively. Both have little driving experience, don't own their car (maybe drive mom and dad's car?) low eduction and income, and considerably higher chance of wrecking their car.

Clusters 0 and 3 are both older, more responsible married people with higher income and lower chance of accidents and are white and people of color respectively.

The clusters I think are intersting are 2 and "unclustered." Both are older, higher income, and more driving experience. Interestingly, they both drive sports cars. However, they are very different. Cluster 2 are responsible, married, and have the lowest accident rates. These are "pride of ownership cluster."  I wonder if they are more likely to regularly wash their cars and perhsps use premium fuel.  

The 'Unclustered" are unmarried, have lots of DUIs, speeding tickets, and accidents. I call this the mid-life crisis "cluster."

## Limitation, Recommendations, and Next Steps

One of the best measured by accuracy and recall (and definitely the fastest) was logistic regression.  I ran logistic regression with PCA feature engineering but due to the dataset (mostly categorical data)  it didn't help much. It ran a little faster but slightly worse results.  I suggest logistic regression due to speed, accuracy, and recall scores.

The data itself could be improved.  The driving record, DUIs, etc should be subject to a shorter lookback.  There are more factors that may also be useful in determining if someone will crash their car. The most value may be found in parcing out why some young people get into accidents - grades, drivers' education, etc.  

### For Further Information

For any additional questions, please contact me at dmburns@gmail.com
