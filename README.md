# BondForecasting
Data Driven Decision Models for Investment in Bonds
1. Introduction
1.1 Purpose
The purpose of this document is to outline the high-level design of the Investment in Gold or General Bonds and provide an overview of the tool implementation.

Its main purpose is to –
●	Recommend a bond that has high returns to the client.
1.2	Scope
Investment in Gold or General Bonds is a forecasting application that receives inputs from the client, It provides the input as a form of the time period to the model. 

The model will take inputs from the customer. There will be 3 inputs and the user has to choose 1 option out of 3. The options are 1 year, 4 year and 8 year. These inputs are basically asking the model to give a forecast of the number of days.

The output will give the forecasted value for both Gold and General Bond along with the returns after "n" number of days. It will show returns and graph for both GOLD and General so that users can see and decide which one to buy. It takes less than 1 minute to execute this whole operation depending on how good your system is.
2.	System Overview
2.1 Context
The 2008-09 global financial crises and 2020-21 pandemic have shown us the volatility of the market. Many people are finding a way to invest money to secure their future. People are trying to find a secure investment with minimum financial risks with higher returns. This is also a fact that with investment there also comes with risks. There is a saying in the world of investment “Do not put all your eggs in one basket”. We need a diverse portfolio in the area of investment, so that if one investment does not give you enough yields due to fluctuations in the market rates then others will give you higher yield. 

Bonds are one such investment people prefer the most. The Bonds we have selected are two government bonds – SGB (Sovereign Gold Bond) and IRFC (Indian Railway Finance Corporation). The objective was to forecast the prices of SGB and IRFC bonds and calculate the returns. Compare the returns and recommend the client which one to pick based on the input that is the number of years to forecast.
2.2 Product Feature
The major feature of the project will be the following: -
o	UI input - The user has to select one option from three options.
o	 It is taking live data every time the model is running and stored it in a database.
o	Database - SQLite database is easy to use and operate. The user does not need any prior knowledge to use SQLite.
o	Hyper-Parameters - Every time the model runs, it calculates the p,d,q values of both the bonds. It takes time but we have put accuracy over speed.
o	No Outside Interference - Since our model is collecting live data on its own, storing it in a database, and calculating hyperparameters by itself, it does not require any human interference at all.
2.3	Technologies Used
The APP will be developed in Python using the Flask framework, Model will be implemented in Python. The frontend web application will be implemented using HTML and CSS.
The system will have Machine Learning libraries too.
Front-end – HTML and CSS
Middleware (APP) – Python, Flask framework
Backend – SQLite
3.	Application Architecture
3.1 Architecture Design as per student perspective
Front-end Application – Web app with UI which receives input from the user in text format.
APP – Receive HTTP GET requests containing user input and forward them to the ML-based model.
NSE - Collecting data from the NSE server.
Data Preprocessing - Performing EDA and Feature Engineering.
Database – Store the bonds data in the database with module-info
ML Model – Model will receive the user input and forecasts the prices of both the bonds upto the desired time of the user.
Model Accuracy - We have two Model accuracy measures - RMSE and MAPE
HyperParameter -  Using Auto_arima to get the values of p,d,q

 

3.2 System Operations
Below figure is an illustration of the interaction between system subsystems in during the use of the application.

 
4.	Database Architecture (Entity Relationship Diagram)
4.1 SQLite Database
The database essentially serves as an all-encompassing cluster that provides the data needed for all recommendation queries. SQLite works by compiling SQL text into byte code, then running that byte code using a virtual machine. SQLite is often used as the on-disk file format for various desktop applications.
4.2 Generation and Storing
Live Data is automatically collected and stored in the SQLite database. SQLAlchemy provides a nice “Pythonic” way of interacting with databases, you can leverage the Pythonic framework of SQLAlchemy to streamline your workflow and more efficient query your data. SQLAlchemy can be used to automatically load tables from a database using something called reflection. Reflection is the process of reading the database and building the metadata based on that information.
Entity Relation diagram of the database shown below: - 

 
5.	Approach
We have tried multiple ML forecasting methods to solve the issue which are listed below: -
5.1 Naive Model
We used the Naive model as a base model to compare. 
The RMSE and MAPE of IRFC General bond is 
RMSE: 101.6912900410688
MAPE: 0.07516511798165514

And The RMSE and MAPE of SGB Gold Bond is 
RMSE: 1530.829541126325
MAPE: 0.43522779410918855

5.2 Holt Winter’s ES
We used Holt Winter because we had seasonality in our data.
The RMSE and MAPE of IRFC General bond is
RMSE: 108.56073298320254
MAPE: 0.07988544586788512

And The RMSE and MAPE of SGB Gold Bond is 
RMSE: 1019.3419695838711
MAPE: 0.43522779410918855

5.3	SARIMA
We have used the SARIMA model because it has seasonality.
The RMSE and MAPE of IRFC General bond is
RMSE: 7.738862719485895
MAPE: 0.002838789019735471

And The RMSE and MAPE of SGB Gold Bond is 
RMSE: 25.846279902508467
MAPE: 0.003635532370340004
5.4	ARIMA
We have used ARIMA as our final model by removing the seasonality from the data. 
The RMSE and MAPE of IRFC General bond is
RMSE: 7.730512468167058
MAPE: 0.0027900365441560345

And The RMSE and MAPE of SGB Gold Bond is 
RMSE: 25.831099690687623
MAPE: 0.0037058182587375267

So, as we can see, ARIMA is giving you very good values of RMSE and MAPE. So we chose ARIMA for our forecasting model.
6.	Assumption and Constraints
6.1 Time Periods.
We have created a specific output that means, the returns which will be calculated will be after 1 year, 4 year and 8 year
6.2 Buying and Selling are specified and sold before maturity. 
We have assumed that the user will buy the bond in between these 3 options based on the current price of both of the bonds and sell it when the returns are high. We have assumed that the user will not hold the bond till it reaches its maturity and sells it when the returns are high.
7. References
https://medium.com/analytics-vidhya/arima-model-from-scratch-in-python-489e961603ce
https://analyticsindiamag.com/comprehensive-guide-to-time-series-analysis-using-arima/
https://www.machinelearningplus.com/time-series/arima-model-time-series-forecasting-python/
https://www.analyticsvidhya.com/blog/2020/10/how-to-create-an-arima-model-for-time-series-forecasting-in-python/
https://machinelearningmastery.com/naive-methods-for-forecasting-household-electricity-consumption/






