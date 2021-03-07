# Rossman - A Machine Learning Solution for Sales Forecasting

![Rossmann](https://upload.wikimedia.org/wikipedia/commons/9/95/Rossmann_Schriftzug_mit_Centaur.jpg)

## Introduction

This is a study project done in the course "Data Science Em Produção", of the Data Scientist Meigarom Lopes. The purpose of the project was to cover all the steps of a data science project, from the business knowledge to deploy, using techniques of data engineering, exploratory data analysis and machine learning.

The main idea was not only use the data and apply advanced techiniques to it, but also to understand the business context, so then find the best implementation solution in the business problem, always looking for results that really impact positively in the context.

This document will serve as a study review guide. The description of the steps used in the project are included in the next session. 

The story is fictional and was created only to contextualize the analysis.

## 1.0. The Business Problem

The Rossmann business team identified a demand for reforms at regional branches. To anticipate this gut, the company's CFO contacted each branch manager asking for a forecast of daily sales for the next six weeks.

The managers of each branch contacted the Data Science team to make this forecast. When investigating the business problem in depth, some essential points for the production of any solution were identified:

* **Motivation**: A demand from the CFO to know the sales forecast for the next six weeks;

* **Root Cause**: The CFO need the sales forecast for the next six week to antecipate fund to invest in the store reforms;

* **Stakeholder**: The CFO;

## 2.0 Solution strategy

The solution format will be a sales forecast for each store for the next six weeks, and Machine Learning techniques focused on Regression should be used to make this demand forecast possible. A daily granularity per store will also be assumed for the forecast, that is, our input data will be the daily sales of the stores.

The final format will be a Telgram Bot, which the CFO will be able to access in real time the demand forecast to the next six weeks of any store anywhere, depending only on an internet connection and an account in the Telegram application.

* **Granularity**: For day for store;
    
* **Type of problem**: A Demand forecast;
     
* **Solution**: Regression;
     
* **Delivery method:** Telegram Bot.

## 3.0 Insights

### Stores with closer competitors should sell less - FALSE

Common sense would lead us to imagine that the distance between competitors could have a certain impact on store sales, where stores that are competing for the same audience would divide the customers from that location. The real impact of this variable can be seen in the following graphs:

!['H2'](https://user-images.githubusercontent.com/73614098/110234644-f6f6db00-7f01-11eb-9aef-288a844f57e0.png)

The first graph allows us to have a macro view of the problem. It is possible to understand how the number of sales of each store is concentrated in relation to the other stores, and it is possible to perceive that, despite some outliers present, the vast majority of stores, regardless of the distance between them, concentrate the same number of sales.

The second graph is an analysis with limited intervals, showing only the distances that occur frequently. Despite a slight increase in sales in the range between 20,000 and 25,000 (which is probably the result of fewer occurrences of these distances in the data), sales maintain the same average pattern across all distance ranges.

The probable justification for this fact is that competition between short distance stores leads to a greater allocation of resources to attract customers, that is: a competition that improves the market. However, this is a hypothesis that must be confirmed in future analysis.



## 5.0 Machine Learning Model Applied


## 6.0 Machine Learning Performance


## 7.0 Business Results


## 8.0 Conclusions


## 9.0 Lessons Learned


## 10.0 Next Steps
   
   
   
   
   
   
   

<h4 align="center"> 
	🚧  Under construction  🚧
</h4>
