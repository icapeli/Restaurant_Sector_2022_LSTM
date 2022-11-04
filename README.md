![image](https://user-images.githubusercontent.com/101752113/196540084-8af6bf70-e6da-49a6-b1d3-208e423aced9.png)
# PREDICTING RESTAURANT EQUITY PRICES USING AN LSTM
The COVID-19 pandemic has changed the landscape of the restaurant industry. This repository contains a model intended to predict restaurant equity prices for the remainder of the year 2022. Using  projected COVID-19 deaths and daily volume as an exogenous variables, I use an LSTM to predict future prices. Although the model is limited by the inherent diffculty of predicting COVID deaths, the results were solid. **The top performers were  Papa Johns, Dominos and McDonalds while the bottom 3 were Wingstop, Jack in the Box, and Starbucks.** 
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

## XGBoost Regressor
![image](https://user-images.githubusercontent.com/101752113/197634962-894adc43-49bb-4f4e-9b0c-a27c20d2df90.png)
## PROPHET

![image](https://user-images.githubusercontent.com/101752113/199979332-84b5c3dc-1a5e-4556-ae52-3ed4748bef1f.png)

## LSTM 

![image](https://user-images.githubusercontent.com/101752113/199972645-9ed1fc42-6ae5-45f4-b4df-19c285771115.png)

Surprisingly, the Prophet model performed better than the LSTM but the  MAPE values are still quite high. However, these results do not compare unfavorably to results found elsewhere:
![image](https://user-images.githubusercontent.com/101752113/196505182-2cfb9325-1b72-4e30-aed9-708ae257abef.png)

Source:https://qjhong.github.io/

Here are my projections:

![image](https://user-images.githubusercontent.com/101752113/196772766-7b716420-23cf-4403-8781-112662a9ef01.png)
#  VOLUME MODELING 
## PROPHET VOLUME MODELING 
![image](https://user-images.githubusercontent.com/101752113/199973166-04fa4617-4932-4498-b206-d219a1190cd9.png)

## LSTM VOLUME MODELING 
![image](https://user-images.githubusercontent.com/101752113/199973634-9ef54af4-3f09-4a9c-8bc2-c99dc79748dc.png)

# PRICE MODELING

## Auto.Arima

![image](https://user-images.githubusercontent.com/101752113/199974904-cbc96946-66ac-45c3-9163-bd574dfdc89e.png)

## PROPHET PRICE MODEL

![image](https://user-images.githubusercontent.com/101752113/199974788-324ceee9-3a3a-4ab7-852e-671d62b36e82.png)

## LSTM PRICE MODEL
The LSTM model numbers below represent an average of 3 models.
![image](https://user-images.githubusercontent.com/101752113/199974609-bdc21833-e10e-49da-939d-1a84811ccd8f.png)
![image](https://user-images.githubusercontent.com/101752113/199974434-5319486d-4969-405b-891e-7aebdff87b58.png)
Overall, the results were good. I chose to use the LSTM model because its results were the best except for a few outliers that I will have to approach with caution.

## PRICE PREDICITONS
The LSTM model numbers below represent an average of 3 models.

![image](https://user-images.githubusercontent.com/101752113/199975528-58e1c6de-bb85-4864-a92d-a8e0a8b6be02.png)

![image](https://user-images.githubusercontent.com/101752113/199975866-68962dee-833a-4fbb-b609-0ee2257c09b0.png)

### TOP 3
I chose to exclude results from the stocks with MAPEs over 10% because their results were potentially unreliable.  That means **Bloomin Brands, Cracker Barrel, Shake Shack, and Wendy's are all eliminated**. After eliminating them, the top perfomers were:

![image](https://user-images.githubusercontent.com/101752113/199976073-641fc4b1-f8c2-4db0-a146-69bc2f0d20a8.png)

### BOTTOM 3
The worse 3 performers were:

![image](https://user-images.githubusercontent.com/101752113/199976246-85966054-bc9d-4be4-addd-dcf76a564a0d.png)

# CONCLUSION
**The top performers were  Papa Johns, Dominos and McDonalds while the bottom 3 were Wingstop, Jack in the Box, and Starbucks.**  Overall, the results were good but the high MAPEs for a few companies and the high MAPEs for the COVID predictions certainly leave room for improvement. Moreover, more exogenous variables like commodities prices, and inflation rates would also enhance the dataset. Include each of those would involve making assumptions about effects just like I did for COVID death numbers. Also, other models like a VARMAX model or a hybrid model may also prove fruitful. 

# REPOSITORY STRUCTURE
```bash
├── gitignore
├── 5_year_restaurant_prices.xlsx
├── 7day delay.xlsx
├── 7day_delay_withmy_preds.xlsx
├── Q4 restaurant equity .ipynb
├── README.md
├── presentation.pdf
├── volume_copy.xlsx
```
