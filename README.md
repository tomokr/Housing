# How do we find a reasonable house? or luxury house?
This is the House price estimation project from kaggle contest.

<img src="https://user-images.githubusercontent.com/5339011/98837097-84249a00-2410-11eb-897f-f7851628cc1e.jpg" width="360">

What is the biggest decision in the life? Buying house is one of them.
Why? The price is so expensive. Also, the house is where we spend a lot of time in our life.
We all need a comfortable but reasonable house.
In this project, I'm going to decide the price of house from many features that the house has.

The features we have are below:
>'Id', 'MSSubClass', 'MSZoning', 'LotFrontage', 'LotArea', 'Street',
       'Alley', 'LotShape', 'LandContour', 'Utilities', 'LotConfig',
       'LandSlope', 'Neighborhood', 'Condition1', 'Condition2', 'BldgType',
       'HouseStyle', 'OverallQual', 'OverallCond', 'YearBuilt', 'YearRemodAdd',
       'RoofStyle', 'RoofMatl', 'Exterior1st', 'Exterior2nd', 'MasVnrType',
       'MasVnrArea', 'ExterQual', 'ExterCond', 'Foundation', 'BsmtQual',
       'BsmtCond', 'BsmtExposure', 'BsmtFinType1', 'BsmtFinSF1',
       'BsmtFinType2', 'BsmtFinSF2', 'BsmtUnfSF', 'TotalBsmtSF', 'Heating',
       'HeatingQC', 'CentralAir', 'Electrical', '1stFlrSF', '2ndFlrSF',
       'LowQualFinSF', 'GrLivArea', 'BsmtFullBath', 'BsmtHalfBath', 'FullBath',
       'HalfBath', 'BedroomAbvGr', 'KitchenAbvGr', 'KitchenQual',
       'TotRmsAbvGrd', 'Functional', 'Fireplaces', 'FireplaceQu', 'GarageType',
       'GarageYrBlt', 'GarageFinish', 'GarageCars', 'GarageArea', 'GarageQual',
       'GarageCond', 'PavedDrive', 'WoodDeckSF', 'OpenPorchSF',
       'EnclosedPorch', '3SsnPorch', 'ScreenPorch', 'PoolArea', 'PoolQC',
       'Fence', 'MiscFeature', 'MiscVal', 'MoSold', 'YrSold', 'SaleType',
       'SaleCondition', 'SalePrice'

The last one `SalePrice` is what we going to estimate. Other than the target, we have 80 features.

## EDA
I'm going to explore the training data, which is the 70% of the whole prepared test data set.
For EDA, we dropped the columns contains `NaN`.

The `SalePrice` is distributed as the graph below.

![saleprice](https://user-images.githubusercontent.com/5339011/99019561-909d1580-252a-11eb-9a6e-846bf06a148c.png)

Its mean is 180921. The max is 755000 and the minimum is 34900.

### Numerical Features
There are many numerical features and they are distribute like the scatter plot below.

![numerical](https://user-images.githubusercontent.com/5339011/99020172-ede59680-252b-11eb-8683-da96d61629a3.png)

The correlation between `SalePrice` and the numerical features are shown in the heatmap.
![corr](https://user-images.githubusercontent.com/5339011/99019855-4e280880-252b-11eb-9536-9bff520116eb.png)

`OverAllQual` and `GrLivArea` are correlated with `SalePrice` the best.

### Categorical features
Also, there are many categorical features. They are look like below.
![categorical](https://user-images.githubusercontent.com/5339011/99020171-ede59680-252b-11eb-9b3e-d07021c310fc.png)



## Modeling
This time, we use all the features except the categorical feature that has less than 10 kinds.
I did imputation with the mean for the numerical features and most frequent category for the categorical features.

I also attached two kind of regression model to estimate the price of the house.
One is `Random Forest` and the other is `Gradient Boosting`. The parameters for each model I used were default in `scikit-learn`.
The mean absolute error for these are `19383` for `Random Forest` and `16199` for `Gradient Boosting`.
Then I took the final model for `Gradient Boosting`.

With using this model, I won the top 10% of the ranking at kaggle competetion. (as of 11/12/20)

<img width="214" alt="kaggle 2020-11-12 22 07 37" src="https://user-images.githubusercontent.com/5339011/99023877-829fc280-2533-11eb-99cb-d07b0b37c475.png">
https://www.kaggle.com/tomoshimo

## Conclusion
This is the result of the regression. The data of the graph is from the valid set of the regression. 
The blue line means the prediction and the red dots are the real data.

![predict](https://user-images.githubusercontent.com/5339011/98957414-2c009d00-24cf-11eb-8a6b-f917b193da0f.png)

We could predict almost of the price of the houses.
And the point above the blue line represents the price of the house is rather expensive comparing with the normal price.
The house probably is a luxury house with other feature than we use for regression.
Also, the point below the blue line represents the price of the house is rather reasonable.
There are some reasons why those prices are so. We should investigate them when we buy the house.
We can also determine the price of the house with using this model when we sell a house.
