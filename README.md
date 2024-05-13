# finance_project
Project includes parsing, processing and analysis of financial data as well as building a forecasting ML model

# Navigation

- `final_datasets` - parsed and preprocessed datasets. Prefix "final" in file`s name means this file does not contain missing values. Parsing was done up to 2024-08-05
- `EDA` - EDA for each sector and hypotheses testing
- `parsers` - all functions needed to parse stock and macro data

# Content
1) [Step №1. Theme and goal of our project](#the-goal-of-our-project)
2) [Step №2. Data parsing](#parsing)
3) [Step №3. EDA-1: Data processing](#data-processing)
4) [Step №4. EDA-2: Visualisation](#visualisation)
5) [Step №5. Feature engineering](#feature-engineering)
6) [Step №6. Hypotheses](#hypotheses)
7) [Step №7. Machine Learning](#machine-learning)

# Step №0. Warning(-s) to the reader.
* If you want to run our code, please, start with `!pip install -r requirements.txt`
   
# Step №1. The Goal of our Project
The scope of our project is the financial market. We want to reach accurate prediction for future prices of more than 400 shares of different companies. They were chosen not accidentally: we decided to focus on 4 sectors.
* Industrials
* Renewable Energy
* Financial Services
* Healthcare

Due to their incohesion, we expect them to be uncorrelated, so models can be trained in each sector separatly. Our final product is a _telegram bot_ that can predict prices.

write in general about models, desired result (how it's going to look like)

# Step №2. Parsing
Data for the final dataset was taken from: [FMP API](https://site.financialmodelingprep.com/developer/docs) (US stock parsing), [Alpha Vantage API](https://www.alphavantage.co/) (US macro statistic), [FED](https://www.newyorkfed.org/markets/reference-rates/effr) (Effective Federal Funds Rate), [CBR](https://www.cbr.ru/statistics/) (Russian monetary statistics), [Federal State Statistics Service](https://eng.rosstat.gov.ru/) (Russian GDP), [ApiMoex](https://pypi.org/project/apimoex/) (RU stock parsing)

Dataset Overview... (write about all features and the logic of adding them for this project)

# Step №3. Data processing


# Step №4. Visualisation


# Step №5. Feature engineering


# Step №6. Hypotheses


# Step №7. Machine Learning
Here we've built a forecasting ML model. Description of models + result

# Our team:
1) Nikita Chuikin 
2) Andrew Nizov
