# Analysis of Insurance Data - Beware the Young and the Old Guy in the Convertible
Author: David Burns <br>
Date: 11/17/2022

## Business Problem
The goal of this project is to explore car insurance data to determine the factors that will lead to insurance claims.

### Data
The initial data contained 10,000 rows of data and 18 columns of variables that could impact sales and 1 column of 'outcome,' or claim data.   The original source of the data is on Kaggle.  The target of the data is whether or not person files a claim. The notes say "The outcome column indicates 1 if a customer has claimed his/her loan else 0" I take this to mean that a 1 is a total loss resulting in the person filing a claim to pay off the car loan.

## Methods
I first examined the data and cleaned up some obvious errors. Most of the data was categorical which I ordinal encoded.  I visually inspected the data and discovered missing data points in credit score and annual miles.  

We did exploratory data visualization analysis of: 

1)  HEAT MAP - I looked at a heat map and noted correlations. Accident outcome was negatively correlated with age and driving experience and not much else.  I inputed missing values by grouping by age which was correlated with the missing values.
2)  Some graphs of Age v. Claims, Driving Experience v. Claims, etc.


### Examples of the visualizations

![Screen Shot 2022-11-20 at 7 58 43 PM](https://user-images.githubusercontent.com/113855848/202962631-5356ec32-52a8-492b-b870-9ecaaf51b998.png)

A useful view of the data is percent claims by age groups.  Age is also positively correlated with driving experience, DUIs, marriage, kids, and speeding tickets.  It looks like the data is cumulative over a drivers life.  I would recommend that these items sunset after a time.

![Screen Shot 2022-11-20 at 8 02 26 PM](https://user-images.githubusercontent.com/113855848/202963016-be11d20e-19b0-4de3-8121-5b151f70abc5.png)

Driving experience is also strongly negatively correlated with crashing ones car.  Of course, age and driving experience are also positively correlated.

These two factors were the most strongly (negatively) correlated with accidents.

## Model

I ran several (trained) classificaiton models and an (untrained) segmentation model.  I ran them all several times and varied parameters, dropped data, imputed it different ways. etc.  The classificaiton models I ran were logistic regression, random forest classifier, K N Neighbors, XGB Classifier, LGBM Classifier, Gradient Boosting Classifier.  

The most important factor we were optimizing for was recall.  Not predicting an accident (false negative) is much more expensive than missing out on a potential customer.  Based on accuracy and recall, logistic regression (classification) and some of the gradient boosting models worked about equally at ~.84 accuracy and .15 false negative rate.  

I chose the logistic regression model due to its very competitive accuracy and recall and very quick processing time.


## Clustering Analysis

Age and driving experience are the driving factors in predicting whether or not someone will have an accident.  That is, the older and more experience one has driving, the lower the probability that one will have an accident.  

As I noted before, as you get older, your income, credit score, chance of being married, children, etc all go up. However, so does your number of speeding violations, DUIs, and past accidents. I would recommend that the insurance company limit these items to a limited look back - i.e. violations drop off your record after a certain amount of years. 

Gender, race, and vehicle type seem to have little correlation with wrecking your car.  However, I left them in the analysis due to a couple of interesting findings.  

First, adding race functionally duplicated certain clusters without adding much additional value. I ran this clustering several times and sometimes I got four columns, one older white people, one older minority, one young white people, one younger minority people.  

Here, all the young people are clustered in cluster 4.  They have little driving experience, don't own their car, and have alots of insurance claims. They also live in the same postal code as cluster 1 who I suspect are largely their parents!

The clusters I think are intersting are 3 and "unclustered."  Both are older, higher income, and more driving experience.  Interestingly, they both drive sports cars.  However, they are very different.  Cluster 3 are responsible, women, married, and have low accident rates. These are "pride of ownership cluster."  The 'unclustered" are unmarried, have lots of DUIs, speeding tickets, and accidents.  I call this the mid-life crisis "cluster."  

## Limitation, Recommendations, and Next Steps

One of the best measured by accuracy and recall (and definitely the fastest) was logistic regression.  I ran logistic regression with PCA feature engineering but due to the dataset (mostly categorical data)  it didn't help much. It ran a little faster but slightly worse results.  I suggest logistic regression due to speed, accuracy, and recall scores.

The data itself could be improved.  The driving record, DUIs, etc should be subject to a shorter lookback.  There are more factors that may also be useful in determining if someone will crash their car. The most value may be found in parcing out why some young people get into accidents - grades, drivers' education, etc.  

### For Further Information

For any additional questions, please contact me at dmburns@gmail.com
