# Sales-Prediction-analysis

HOUSE SALE PRICE PREDITION USING LINEAR REGRESSION MODEL
CHAPTER 1. INTRODUCTION AND BACKGROUND
The study aims at identifying the factors contributing to the sale price and predicting sale prices of residential properties in Ames, Iowa, USA. Utilizing a dataset from Iowa’s Assessor’s Office, the study is comprised of 2880 observations and 78 variables, providing property sales details Ames, between 2006 and 2010.
In this particular study, predicting of sales price has been accomplished using linear regression model. The sale price is the target variable and 16 predictor variables in the data set are used based on literature reviews. Data cleaning has been done for selected variables and ggplot was used to get visualize data better. Hypothesis testing for 5 major predictor variables was established using correlation test. 5 multivariate regression models were built, out of which the best performing model was selected based on accuracy statistics. PREDICTION
Hypothesis:
H1: There will be a positive relationship between lot area and sale price
H2: There will be a positive relationship between no of bedrooms and sale price
H3: There will be a positive relationship between no of bathrooms and sale price
H4: There will be a negative relationship between age of the building and sale price
H5: There will be a positive relationship between basement area and sale price
As per the recent studies by Kalaivani et.al.(2023), the lot area emerged as a significant variable in house sale prediction. However, a Quantile regression model study by Feng et.al.(2021), proposed a contrasting view of nonlinear relationship between house size, owing to discount effect on large-sized house. In this study, the hypothesis is taken as positive linear relationship between lot area and price, which is the general notion. In the housing price model estimates, the pricing index shows depreciation with increasing age of property (Mukhlishin et.al.,2017;Cannaday et.al.,2005). House sale price prediction using various parametric and semi parametric regression techniques like linear regression m random forest, gradient boosting etc. showed a positive association with bedrooms, bathrooms and fireplaces (Hu et.al., 2019; Bin, 2004). As per the hedonic pricing model, the house price is a function of physical characteristics and other factors like basement area, garage spaces, pool, air conditioning and house quality (Sirmans et.al.,2005; Malpezzi,2002). Based on these literature findings, the 5 hypothesis variables and other control variables as shown in Table.1 was selected.

CHAPTER 2. METHODOLOGY
R studio is used for carrying out the prediction analysis using linear regression model. Earlier, a similar successful study of house sale prices using linear regression model was established by Andersson (2022) and Mire et.al. (2022). Initially the entire data set is loaded into dataframe data in R. The 16 variables are finalized as per the literature review in Chapter 1. are subsetted into subdata dataframe. 2 derived variables - total_bath and age_2010 are used.

![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/7008d934-a44b-48e7-980f-2dd8181c39e4)
All the necessary actions are carried out in this subset data frame. The various stages of process carried are mentioned below.
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/33277ae3-2bda-4460-9a3b-47b9d2028ca5)
2.1. DATA QUALITY REPORT
In the exploratory data analysis using summary, table and boxplot functions missing data and outliers were found. In this preliminary analysis, the main data quality issues found were
1.missing values
2. outliers
3. incorrect data
4. incorrect variable type
The house quality, house condition,neighbourhood, month_sold and aircon set to categorical variable using as.factor() function. While using table function, 3 observations were having value as 11, which is incorrect as per data dictionary. It necessary to set the correct class for each variable to get an accurate model. The table function on house quality variable has 3 values in level 11, which is incorrect as per the data set. Hence it has been replaced with the highest level in the variable 10. Now the missing values in entire data frame is obtained using ColSums(is.na()) function. As per this, there were 2 blanks each in bsmt_full_bath, bsmt_half_bath and total_bath and 1 blank each in bsmt_area and garage_cars. All these blanks are replaced with 0, as missing values may distort the final model. Using boxplot () and summary () function outlier were identified in lot area, bsmt_area, age_2010. 7 outlier values in lot area, 9 outlier values in age_2010, 2 outlier values in bsmt_area and 2 outliers in sale_price were identified. The outliers were handled using IQR upper and lower fences (Chhabra, 2021). The boxplots and table summary of bedroom and bathroom showed values 0,5, 6,8 as outliers. However, only 0 and 8 are replaced with nearest values. Values 5 and 6 are maintained as it in the dataset as this seems to be data characteristic, rather than an anomaly. Removal of outliers is necessary to maintain the normal distribution and reduce error variance of the dataset (Osborne & Overbay,2004). However, removal of these many observations, may complicate interpretation of results, instead it can be transformed (Osborne & Waters,2002). Hence the replacement technique using IQR and capping method as mentioned above was carried out.
2.2 PROCESSING OF CLEAN DATA
Data visualization of all the hypothesis variables were done using ggplot. Lot area and basement area were plotted against sale price using geom_point and geom_smooth, whereas building age was plotted against sale price using geom_line and geom_smooth. In this study, bedrooms and bathrooms are treated as numerical variables for which it can be plotted using geom_point. However, these can be treated as categorical variable as well for easy understanding of visualization. Both visualizations are depicted for comparison.The hypothesis mentioned in Section. Is tested using Pearson correlation coefficient, as all the hypothesis variables are numerical variables. Statistical test is to be selected depending on the type of the variable (Bevans, 2023). Once the hypothesis is established, the data set is divided into training data set and test data set in 80%-20% ratio using createDataPartition () and set.seed () .5 multivariate linear regression models were built on train data using lm () and summary (). For each model, formula was modified by removing insignificant variables and adding new variables and the best fitted model was selected for accuracy test. The developed models was then used to predict the sale prices on test data using predict() and postResample(). The accuracy of the model was tested using vif(), cook.distance() , dwtest() and residual plots.

CHAPTER 3. RESULTS AND DISCUSSIONS
3.1 DESCRIPTIVE STATISTICS
The initial descriptive statistics gave a summary about the data characteristics and data quality issues in the dataset.
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/8c5ce8c4-83ea-402b-814b-56759ade3140)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/91315e8c-45bf-41f3-b1aa-f2820b8c9bf2)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/64966d93-90d3-4abd-bfb7-17c0409eb7cd)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/63609d0b-864b-4292-a468-d4c48763e9d4)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/19d3f9d3-5630-4116-9f8e-b8c16f02eb2e)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/25a1e82f-69fa-40eb-afdb-d3fb2af9ae3e)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/9db19977-3d0e-49c9-8bc0-879bbe2a1e38)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/4393e91d-eaa7-4b79-81ac-571a1e11e36a)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/24d639c6-e00f-41c1-b8e1-3182a6cac6b7)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/0b94ef81-3528-4e36-95ee-b550b948d360)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/7fb7aed4-c321-4407-aa0d-68b5085f56e8)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/92b7621b-b934-47ff-bf3d-f3cf8b10e133)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/e48fd586-bd1b-4c88-96f5-0bfb3c5239a2)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/37f7a895-ced5-4eab-b6f2-2b3b3c901903)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/713357cd-34db-4bcf-a64e-040afb1640d0)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/d7f66f95-1b6a-4b00-b12f-89208c6e02ce)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/88d42c26-b36d-4cc7-b02a-f41b92a690c0)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/e4bbad61-b1ae-42c2-a0b3-f5f74d4e52ab)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/0af20b1c-aca9-493c-b28a-cbae6a992fab)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/e305a125-caf3-4fd3-8e80-4d59ca855403)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/bfc07711-6610-4ee0-bff7-2a758dbd755b)


3.2 FINAL DATA VISUALIZATIONS
As per the analysis of the ggplot plot visualizations the lot area, basement area, no of bedrooms and no f of bathrooms show a positive correlation with sale price whereas the age of the building shows a negative correlation with sale price.

![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/42776323-ee2b-401c-9ec1-c6f4e74c2e88)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/79ced920-b6bf-4aa3-9a4b-dba0f8aabc01)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/a231b847-0669-4286-9486-a63f2c3fbdd4)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/52c6b3a2-fc47-467d-ba64-70754cc81e13)  ![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/959b5164-cccf-4947-95fb-21e76995da1e)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/88c3aaa0-b483-4650-915e-9d96057af574)  ![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/4ec77ca2-c16e-430b-9857-d41cbf142038)


3.3 MEASURES OF ASSOCIATION
The measure of association of all 5 hypothesis variables with the target variable was checked using Pearson’s Correlation Coefficient, with 95% confidence interval. A coefficient of ±0.1 refers to a weak linear relationship, ±0.3 refers to a moderate linear relationship and ±0.5 refers to a strong linear relationship (Schober et.al., 2018)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/d19388a4-08db-45eb-8471-f8462376a093)

As per the correlation test, there is an extremely significant correlation between lot area and sale price as the p-value is less than 0.05 and correlation coefficient of 0.35 indicates that there is a moderate positive linear relationship between the 2 variables.
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/782bc6e4-6b0b-43a9-a0af-49e6868e8f36)

As per measure of association test, there is an extremely significant correlation between no of bedrooms and sale price as the p-value is less than 0.05 and correlation coefficient of 0.14 indicates that there is a weak positive linear relationship between the 2 variables. This is contrast to several studies including the one by Uwayezu & Vries (2020) where as bedroom were a significant and positive factor in pricing. This might be contradicting probably because of increasing demand for studio apartments.
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/b7d47ea2-d9e0-4f60-a231-60bc9e0a1452)

As per the Pearson correlation coefficient, there is an extremely significant correlation between no of bathrooms and sale price as the p-value is less than 0.05 and correlation coefficient of 0.62 indicates that there is a strong positive linear relationship between the 2 variables, as coefficient is greater than 0.5.
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/ffa42906-3934-4089-b218-476bf5f44fa4)

As per the correlation test, there is an extremely significant correlation between age of building and sale price as the p-value is less than 0.05 and correlation coefficient of -0.56 indicates that there is a strong negative linear relationship between the 2 variables.
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/b6416eb4-e88f-4b50-833b-7db4923f9dc2)

As per the Pearson correlation coefficient, there is an extremely significant correlation between age of building and sale price as the p-value is less than 0.05 and correlation coefficient of 0.66 indicates that there is a strong positive linear relationship between the 2 variables, as coefficient is greater than 0.5.
The above mentioned correlation test results strongly suggests that alternative hypothesis asserted in Chapter 1. hold true and there is positive relationship for variables lot area, no of bedrooms, no of bathrooms and basement area and a negative relationship for age of building with the sale price. From the above results, the strongest correlation of sale price is with basement area, followed by no of bathrooms, age of building, lot area and no of bedrooms in that order respectively.

3.4 REGRESSION MODEL
The consolidated output of the 5 regression models on the train data set is depicted as follows using stargazer().
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/de5577d8-f828-4e7f-884c-b82a7266ab42)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/05faa359-f191-4e42-aa72-12713b6d9ad2)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/a7c2d521-ab79-4cc8-91df-3b1e34f8c244)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/41f597e9-9248-4299-a5dc-cf0475384eb8)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/f3fad824-ac34-499b-a341-b7e3e6e8abef)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/482290b2-356a-480f-ae3b-7e186379afbf)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/d0428aa4-3646-45ab-b2ec-7eb2d9cfb2db)


In model1, all the 5 hypothesis variables were taken as predictors and sale price as target. In this initial model, all the variables are extremely significant, with p-value less than 0.05 except no of bedrooms. Subsequent model was built with the 4 significant variables and with 2 additional variables house quality and month sold were introduced. this process of retention of significant varaibles and additing of new variables were carried out to form 5 regression models.The best and final regression model isa model5 with the predictors lot area , no of bathrooms,age of building, basement area , house quality , air conditioning, garage cars ,no of fireplaces and pool area . In model5, it is clear that all the predictors are having signification relationship with p-value less than 0.05.The R2 in model 5 is to 0.836 , indicating that the model accounts for 83.6% variability in sale price Even though model4 , is having slightly high R2 , it is not selected as best model, as its F-statistic is 317.344, as compared to the F-statistic 729.279 of model5. F-statistic and p-value are closely related. Higher the F-statistic shows higher overall fit of the model.

3.5 PREDICTIONS
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/326d6b33-5d6c-4e9b-81c3-ec4d6404052b)

The best fit regression model gave an RMSE value of 37754.83, which the measure of difference between the predicted and observed values i.e the error between the actual and observed, which is kept at minimum. The Rsquared of 0.808009 shows that the model accounts for 80.8% variability in the sale price, which is quite high and considered good for the prediction model. Even though RMSE is slightly lower and Rsquared is slightly higher in model4, it was not selected as best fit value because of the low F-statistic observed during training of data.

3.6 ACCURACY MEASURES
Multicollinearity was checked using Variance Inflation Factor (VIF) and values are closer to 1, which shows a low multicollinearity among the variables. House quality,age_2010 and garage_cars are having slightly high value, which indicate some multicollinearity , however it is not highly worrying.
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/dad8d8fb-64e7-4b96-b63c-2f8a2f925983)

Assumption of independence was checked using Durbin-Watson test (dwtest) and a value closer to 2 shows that the model meets this assumption. The p-value is greater 0.05, which shows that the test is not significant.
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/aa5f2190-2c91-497a-a4a1-9cc5330ff4d9)

The residual Vs fitted plot shows the residuals as fanned out, which indicate that model has some heteroscedasticity. Plotting of standardized residuals, shows that the residuals deviate at the extremer points, indicating the violation of assumption of normality.
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/859ca53a-49f5-433b-ad97-94c965fc62f1)  ![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/4c0cca3f-e978-477c-8770-034644b1c78a)

Outliers or influential cases tested using cooks distance and a cooks distance less than 1, indicate there are no influential cases and the same has been depicted in plot.
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/c71e409d-6c25-4ff1-82de-723e93507270)
![image](https://github.com/AnishaBalachandran/Sales-Prediction-analysis/assets/159025182/aa1141b1-bfa7-47b2-9531-856ec5b93fed)

Based on these accuracy tests, it can be concluded that the model could be improved further.

CHAPTER 4. CONCLUSIONS
All the hypothesis assumptions hold true, but interestingly no of bedrooms had a weak correlation. The best fit model could explain the variability in sale price to a great extent with minimized errors, however as per the accuracy tests that model could be further improved. In modern times Artificial Neural Networks (ANN) and Fuzzy Logic (FL) approaches are viewed as superior tools for modelling property value predictions, compared to linear regression (Kusan et.al., 2010).
Limitations
-Only a subset of the data was used in modelling
-Data cleaning was not done for the entire data set
-Assumptions violations of linear regression model were noted but not dealt with.
-Large no of independent variables required for prediction accuracy
