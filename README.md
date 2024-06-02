# finance_project
Project includes parsing, processing and analysis of financial data as well as building a forecasting ML model

# Navigation

- `final_datasets` - parsed and preprocessed datasets. Prefix "final" in file`s name means this file does not contain missing values. Parsing was done up to 2024-08-05
- `EDA` - EDA for each sector and hypotheses testing
  - `EDA_macro_data.ipynb` - notebook with macro data analysis
  - `Stock Analysis + Hypothesis Testing.ipynb` - notebook with analysis of stock prices, not marco data and hypothesis testing
- `parsers` - all functions needed to parse stock and macro data
- `ML models`
  - `Linear_models.ipynb` - training Linear model and ARIMA, trying LightAutoML
  - `MTGNN_experiment_financial.ipynb` - notebook with training MTGNN
  - `Stacking.ipynb` - final simple combining of all models

# Content
1) [Step №1. Theme and goal of our project](#the-goal-of-our-project)
2) [Step №2. Data parsing](#parsing)
3) [Step №3. EDA-1: Data processing](#data-processing)
4) [Step №4. EDA-2: Visualisation and Hypotheses](#visualisation)
5) [Step №5. Machine Learning](#machine-learning)

# Step №0. Warning(-s) to the reader.
* If you want to run our code, please, start with `!pip install -r requirements.txt`
   
# Step №1. The Goal of our Project
The scope of our project is the financial market. We will use data for last 5 years as features or target (the desription of all features you can find [here](https://github.com/AnalyseOptimize/finance_project/blob/main/Data%20processing.ipynb). We want to reach accurate prediction for future prices of more than 400 shares of different companies. They were chosen not accidentally: we decided to focus on 4 sectors.
* Industrials
* Renewable Energy
* Financial Services
* Healthcare

Due to their incohesion, we expect them to be uncorrelated, so models can be trained in each sector separatly. Our final product is a _telegram bot_ that can predict prices. 
P.S. Now there is no _telegram bot_, but we will finish it some day!!!

# Step №2. Parsing
> Folder for this step: [parsers](https://github.com/AnalyseOptimize/finance_project/tree/main/parsers)
Data for the final dataset was taken from: [FMP API](https://site.financialmodelingprep.com/developer/docs) (US stock parsing), [Alpha Vantage API](https://www.alphavantage.co/) (US macro statistic), [FED](https://www.newyorkfed.org/markets/reference-rates/effr) (Effective Federal Funds Rate), [CBR](https://www.cbr.ru/statistics/) (Russian monetary statistics), [Federal State Statistics Service](https://eng.rosstat.gov.ru/) (Russian GDP), [ApiMoex](https://pypi.org/project/apimoex/) (RU stock parsing)

Our results of this step are:
* 4 datasets (for each sector), that you can find [here](https://github.com/AnalyseOptimize/finance_project/tree/main/final_datasets)! They are without prefix "final"!
* a lot of different macro and other data, that become our features (you know, [where](https://github.com/AnalyseOptimize/finance_project/blob/main/Data%20processing.ipynb) to find their description)
* quotes of more than 420 shares

# Step №3. Data processing
> Files for this step: [Data processing.ipynb](https://github.com/AnalyseOptimize/finance_project/blob/main/Data%20processing.ipynb) and [Final_merge.ipynb](https://github.com/AnalyseOptimize/finance_project/blob/main/Final_merge.ipynb)
It's a technical step to handle parsed data and make datasets for ML part. On par with other methods we have used ARIMA model, as a way to process some NaNs.
**Variables added at this stage:**
* **gap_hl** for IMOEX and S&P500, which shows the gap between high and low prices. This
* **gap_co** for IMOEX and S&P500, which shows the gap between close and open prices.

# Step №4. Visualisation, Hypotheses Testing
> Folder for this step: [EDA](https://github.com/AnalyseOptimize/finance_project/tree/main/EDA)
The main scope of this step is to evalute either particular features valuable for predicting stock prices or not. [Granger causality test](https://en.wikipedia.org/wiki/Granger_causality) and correlation were used.  
As new categorical features we added day of the week.
Hypotheses were checked in the level of confidence of 1%.
* The list of hypothesis:
     * Distribution of Log-returns
     * The January effect ([stylized fact](http://www.cs.ucl.ac.uk/fileadmin/UCL-CS/images/Research_Student_Information/RN_11_01.pdf))
     * The Monday effect ([stylized fact](http://www.cs.ucl.ac.uk/fileadmin/UCL-CS/images/Research_Student_Information/RN_11_01.pdf))
* Methods, that we use to check these hypothesis:
     * the Shapiro-Wilk test
     * the Wilcoxon test
* Our results:
  All null hypotheses were rejected. So, we didn't find the highest returns in January or on Monday in the USA. Also our log-returns don't have normal distribution (except one random russian stock)!

# Step №5. Machine Learning
> [Folder](https://github.com/AnalyseOptimize/finance_project/tree/main/ML%20models) and [preparation file](https://github.com/AnalyseOptimize/finance_project/blob/main/Make_train_dataset.ipynb)
Our general pipeline includes 2 linear models (ARIMA and linear regression trained on compressed data) and MTGNN architecture. On outputs of three models bleding is used (stacking with linear regression as a metamodel).

Later we will incorporate more neural networks and train linear models more accurately. Also, all framework will be included in scikit-learn-like pipeline to host it on cloud platforms and perform online learning.


# Our team:
1) Nikita Chuikin 
2) Andrew Nizov
