# PREDICTING RESTAURANT EQUITY PRICES USING AN LSTM
The COVID-19 pandemic has changed the landscape of the restaurant industry. This repository contains a model intended to predict restaurant equity prices for the remainder of the year 2022. Using  projected COVID-19 deaths as an exogenous variable, I use an LSTM to predict future prices. Although the model is limited by the inherent diffculty of predicting COVID deaths, the results were solid. The top 3 best perfomers were**worse** . The worst 3 performers were **worse**
# SUMMARY
# BUSINESS UNDERSTANDING
Currently, the market is in a period of uncertainty. Interest rate hikes, supply chain questions, international conflicts, and a still unrelenting but increasingly silent pandemic hover over the marketplace. For any investors looking to save on fees and do their own trading, these problems making profitable trading a daunting task. The restaurant industry, in particular, is vulnerable to so many of those issues. 

My task is to help navigate this perilous industry by providing you with the restaurant industry equities that will perform best in the remainder of this year and the equities that will perform worse. I am using closing price data from Yahoo Finance. Yahoo Finance is an incredibly rich source of finance data. These predictions should refelct the company's preparedness for the current conditions like a COVID surge.

![image](https://user-images.githubusercontent.com/101752113/196517979-a5b5e470-7498-4dbf-bbca-e486a1f1d0b4.png)
# DATA UNDERSTANDING

To properly model and predict restaurant equity prices in today's world, it's essential to include COVID-19 numbers. There were many "COVID-19 numbers" that I could have used but I decided to use deaths from COVID-19. In another iteration of this work, I may use infection rates but my intuition tells me that people generally worry less about infection nowdays. Basically, increasing infection numbers probably wouldn't alarm consumers but increasing death numbers would deter them from visitng dining establishments in person. 

My COVID-19 death numbers are on a 7 day delay. The reasons are simple: 1:) the CDC takes a week to release results, 2.) the market can take a while to react to COVID numbers. In fact, there is evidence that the market can take very long to react:https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8426993/

I used Yahoo Finance site to obtain my price data. I chose to settle on closing price data although intraday price points could be included as well. Each stock in this dataset has, as a prerequisite for examining 5 years of trading, traded for at least 5 years.

**The main metric I use in this notebook is Mean Absolute Percentage Error(MAPE)** because of its universality. I compare between different models and between different stocks. MAPE is great for comparing between very disparate types of values. I will predict prices using multiple models and therefore I need a metric that will provide useful information between models and stocks inside of models. Other metrics like RMSE and MAE would not be helpful in comparing the model's performance on, for example, Chipotle(currently priced in the 4 digits) and Wendy's (trading around 20 dollars). 

# COVID MODELING
## PROPHET

## LSTM 
Surprisingly, the Prophet model performed better than the LSTM but the  MAPE value are still quite high. However, these results do not compare unfavorably to results found elsewhere:
![image](https://user-images.githubusercontent.com/101752113/196505182-2cfb9325-1b72-4e30-aed9-708ae257abef.png)

# MODELING 

## PRICE MODELING
Here is a comparison of MAPEs for each equity.

![image](https://user-images.githubusercontent.com/101752113/196524535-05d12454-76b3-4cbf-b1ce-4547fd41c61e.png)
Overall, the results were good. I chose to use the LSTM model because its results were the best except for a few outliers that I will have to approach with caution.

## PRICE PREDICITONS
![image](https://user-images.githubusercontent.com/101752113/196524287-b92a3714-2def-4e8b-8a62-db6d95b88771.png)

### TOP 3

### BOTTOM 3

# CONCLUSION
The top 3 stocks were**dd**; the lowest 3 were**dd**. Overall, the results were good but the high MAPEs for a few companies and the high MAPEs for the COVID predictions certainly leave room for improvement. Moreover, more exogenous variables like commodities prices, inflation rates, and volume numbers would also enhance the dataset. Include each of those would involve making assumptions about effects just like I did for COVID death numbers. Also, other models like a VARMAX, XGBoost Regressor model, or a hybrid model may also prove fruitful. 
