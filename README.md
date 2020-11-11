# Housing
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

## Modeling
This time, we use all the features except the categorical feature that has less than 10 kinds.
I did imputation with the mean for the numerical features and most frequent category for the categorical features.

I also attached two kind of regression model to estimate the price of the house.
One is `Random Forest` and the other is `Gradient Boosting`. The parameters for each model I used were default in `scikit-learn`.
The mean absolute error for these are `19383` for `Random Forest` and `16199` for `Gradient Boosting`.
Then I took the final model for `Gradient Boosting`.

With using this model, I won the top 10% of the ranking at kaggle competetion.

<img width="231" alt="2020-10-26 12 13 51" src="https://user-images.githubusercontent.com/5339011/98860102-2a809780-2431-11eb-8384-34a27ce48ebf.png">

## Conclusion
