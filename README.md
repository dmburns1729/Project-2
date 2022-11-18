# Please note Read ME is incomplete.  I wanted to submit before deadline but will work in the readme over the weekend


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
