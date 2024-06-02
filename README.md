# finance_project
Project includes parsing, processing and analysis of financial data as well as building a forecasting ML model

# Navigation

- `final_datasets` - parsed and preprocessed datasets. Prefix "final" in file`s name means this file does not contain missing values. Parsing was done up to 2024-08-05
- `EDA` - EDA for each sector and hypotheses testing
- `parsers` - all functions needed to parse stock and macro data
- `ML models`
-    - `Linear_models.ipynb` - training Linear model and ARIMA, trying LightAutoML
     - `MTGNN_experiment_financial.ipynb` - notebook with training MTGNN
     - `Stacking.ipynb` - final simple combining of all models

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

It's a technical step to handle parsed data and make datasets for ML part.

# Step №4. Visualisation, Hypotheses Testing

The main scope of this step is to evalute either particular features valuable for predicting stock prices or not. [Granger causality test](https://en.wikipedia.org/wiki/Granger_causality) and correlation were used. You can find it `EDA` folder.  

As new categorical features we added day of the week. 

# Step №7. Machine Learning

Our general pipeline includes 2 linear models (ARIMA and linear regression trained on compressed data) and MTGNN architecture. On outputs of three models bleding is used (stacking with linear regression as a metamodel).

Later we will incorporate more neural networks and train linear models more accurately. Also, all framework will be included in scikit-learn-like pipeline to host it on cloud platforms and perform online learning.


# Our team:
1) Nikita Chuikin 
2) Andrew Nizov
