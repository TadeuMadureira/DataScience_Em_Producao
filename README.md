# Rossman - A Machine Learning Solution for Sales Forecasting

![Rossmann](https://upload.wikimedia.org/wikipedia/commons/9/95/Rossmann_Schriftzug_mit_Centaur.jpg)



---
## Introduction

This is a study project done in the course "Data Science Em Produção", of the Data Scientist Meigarom Lopes. The purpose of the project was to cover all the steps of a data science project, from the business knowledge to deploy, using techniques of data engineering, exploratory data analysis and machine learning.

The main idea was not only use the data and apply advanced techiniques to it, but also to understand the business context, so then find the best implementation solution in the business problem, always looking for results that really impact positively in the context.

This document will serve as a study review guide. The description of the steps used in the project are included in the next session. 

The story is fictional and was created only to contextualize the analysis.



---
## 1.0. The Business Problem

The Rossmann business team identified a demand for reforms at regional branches. To anticipate this gut, the company's CFO contacted each branch manager asking for a forecast of daily sales for the next six weeks.

The managers of each branch contacted the Data Science team to make this forecast. When investigating the business problem in depth, some essential points for the production of any solution were identified:

* **Motivation**: A demand from the CFO to know the sales forecast for the next six weeks;

* **Root Cause**: The CFO need the sales forecast for the next six week to antecipate fund to invest in the store reforms;

* **Stakeholder**: The CFO;




---
## 2.0 Solution strategy

The solution format will be a sales forecast for each store for the next six weeks, and Machine Learning techniques focused on Regression should be used to make this demand forecast possible. A daily granularity per store will also be assumed for the forecast, that is, our input data will be the daily sales of the stores.

The final format will be a Telegram Bot, which the CFO will be able to access in real time the demand forecast to the next six weeks of any store anywhere, depending only on an internet connection and an account in the Telegram application.

* **Granularity**: For day for store;
    
* **Type of problem**: A Demand forecast;
     
* **Solution**: Regression;
     
* **Delivery method:** Telegram Bot.




---
## 3.0 Insights


### Stores with closer competitors should sell less - FALSE

Common sense would lead us to imagine that the distance between competitors could have a certain impact on store sales, where stores that are competing for the same audience would divide the customers from that location. The real impact of this variable can be seen in the following graphs:

!['H2'](https://user-images.githubusercontent.com/73614098/110251310-4c5cd780-7f56-11eb-9330-e0e1f831b4a9.png)

The first graph allows us to have a macro view of the problem. It is possible to understand how the number of sales of each store is concentrated in relation to the other stores, and it is possible to perceive that, despite some outliers present, the vast majority of stores, regardless of the distance between them, concentrate the same number of sales.

The second graph is an analysis with limited intervals, showing only the distances that occur frequently. Despite a slight increase in sales in the range between 20,000 and 25,000 (which is probably the result of fewer occurrences of these distances in the data), sales maintain the same average pattern across all distance ranges.

The probable justification for this fact is that competition between short distance stores leads to a greater allocation of resources to attract customers, that is: a competition that improves the market. However, this is a hypothesis that must be confirmed in future analysis.


### Stores with more consecutive promotions should sell more. - FALSE

Consecutive promotions seem to be really impactful to increase sales, the greater the amount of promotions a store has in time, the greater its sales should be, correct? But the analysis of the graph leads us to another interpretation:

!['image'](https://user-images.githubusercontent.com/73614098/110251714-33552600-7f58-11eb-8330-1a30007408c7.png)

The interpretation of the graph is clear: According to the data provided to us, stores with extended promotions, on average, sell less than stores with traditional promotions every week of the year. The sales pattern is the same for every week, and both promotions follow the trends, however the extended promotion is always with a lower average than the traditional one.

To understand the reason for this, the project must be extended to an analysis of the cause of this fact.


### Stores should sell more after the 10th of each month. - FALSE

When creating hypotheses, it was thought about the possibility of stores selling more after the 10th, as it is the moment that most people receive their share of the monthly income and can spend on products. However, this was not the trend:

!['image'](https://user-images.githubusercontent.com/73614098/110556686-698bd480-8115-11eb-8c8b-bf5424d67efe.png)

As can be seen in the graphs, there is a clear downward trend in the average sales after the 10th day. However, at the end of the month it is possible to see a recovery in these sales. However, as a final analysis, it is possible to abstract this trend of higher sales volume in the first days of the month.




---
## 4.0 Machine Learning Model Applied

The sales forecast problem in the received granularity is regression, there were some special packages in this type of problem: * Random Forest Regressor *, * Linear Regressor *, * XGBoost Regressor *, in addition to a base model using the average sales

In addition, the metrics used to measure performance were * MAE - Mean Average Error *, * MAPE - Mean Avareage Percentage Error *, * RMSE - Root Mean Squared Error *:

Without Cross-Validation:

<img src="https://user-images.githubusercontent.com/73614098/111063742-d3dea500-8486-11eb-98e7-9d4093e571cd.png" alt="Your image title" width="400"/>

With Cross-Validation:

<img src="https://user-images.githubusercontent.com/73614098/110557469-0438e300-8117-11eb-853d-3826865666c8.png" alt="Your image title" width="500"/>

For testing purposes, XGboostRegressor will be used. Despite the high error in corss-validation, it is expected that it will gain performance in the tunning stage.



---
## 5.0 Machine Learning Performance

Using the XGBoostClassifier and tuning the hyperparameters, the following errors were achieved:

<img src="https://user-images.githubusercontent.com/73614098/111063453-e7890c00-8484-11eb-91cb-7d6c5b433d90.png" alt="Your image title" width="400"/>

Considering MAE (Mean Average Error), as the average error in currency of our model, we can understand that our model errs on average in the amount of $ 769.41 plus or minus. Comparing to the base model, which is the average model, we reduced this average error by approximately $ 585.4.

<img src="https://user-images.githubusercontent.com/73614098/111063638-34211700-8486-11eb-9126-e4ffa9da93d8.png" alt="Your image title" width="700"/>

It is possible to see that our forecasting model closely follows the sales trend by period.



---
## 6.0 Business Results

The best way to translate the results achieved for the CFO is through the demonstration of possible scenarios, in this way the CFO will be able to weigh the possibilities and make the decision in relation to the anticipation of the investment for the stores:

<img src="https://user-images.githubusercontent.com/73614098/111063953-d392d980-8487-11eb-964b-394984c8d0b0.png" alt="Your image title" width="250"/>

It is also possible to view individual stores. As you can see, each store has its own errors, some stores with major errors and others with minor errors. Those stores where the MAE is lower, it is possible to be more certain of the necessary due and thus make a safe decision in relation to the investment. For stores with high MAE, greater care should be taken.

As a next steps, it is interesting to have access to new sales data from these stores, to try some more improvements in the models, in addition to testing other regressors.

<img src="https://user-images.githubusercontent.com/73614098/111063932-ad6d3980-8487-11eb-9595-a29119165119.png" alt="Your image title" width="500"/>

All information regarding each store is available through an API on Heroku. As a final delivery proposal, a Bot was created on the telegram so that the CFO can, just by typing the code of the store of interest, have access to the average sales forecast for the next six weeks of that unit. In this way, decision making can be quick and easy to access.

!['H2'](https://raw.githubusercontent.com/tadeucbm/DataScience_Em_Producao/main/img/WhatsApp%20Video%202021-03-07%20at%2014.35.27.gif)




---
## 7.0 Conclusions

With the end of this project, we were able to reach our goal, which was a sales forecast for each store for the next few weeks, in order to support decision making regarding investment in stores.
The final format was satisfactory, now the CFO will have remote and quick access to forecasts in a quick and easy way.



---
## 8.0 Lessons Learned
This project was extremely important for the business understanding of a company with several stores in several locations.
Some metrics proved to be more important than others, the understanding of the functioning of each one led to a support for better communication of results.



---
## 9.0 Next Steps
As next steps, for greater scale and efficiency of this data:
- Creation of a Pipeline for real-time monitoring of store data;
- Creation of new hypotheses;
- Test other algorithms and test new features;
- Request more data.
