# Data

[Vanguard Total Stock Market Index Fund ETF Shares (2001-2021)](https://finance.yahoo.com/quote/VTI/history?period1=1002326400&period2=1633478400&interval=1d&filter=history&frequency=1d&includeAdjustedClose=true)

 From USNEWS:

"The investment seeks to track the performance of the CRSP US Total Market Index that measures the investment return of the overall stock market. The fund employs an indexing investment approach designed to track the performance of the index, which represents approximately 100% of the investable U.S. stock market and includes large-, mid-, small-, and micro-cap stocks regularly traded on the New York Stock Exchange and Nasdaq. It invests by sampling the index, meaning that it holds a broadly diversified collection of securities that, in the aggregate, approximates the full index in terms of key characteristics."

### Top 10 Holdings:

| COMPANY | % NET ASSETS |
| ----------- | ----------- |
| Apple Inc AAPL | 5.20 |
| Microsoft Corporation MSFT | 4.91 |
| Amazon.com Inc. AMZN | 3.22 |
| Facebook Inc - Ordinary Shares - Class A FB | 1.96 |
| Alphabet Inc - Ordinary Shares - Class A GOOGL | 1.88 |
| Alphabet Inc - Ordinary Shares - Class C GOOG | 1.73 |
| Tesla Inc TSLA | 1.23 |
| NVIDIA Corp NVDA | 1.15 |
| Berkshire Hathaway Inc Class B BRK.B | 1.07 |
| JPMorgan Chase & Co. JPM | 1.05 |

### FUND SNAPSHOT (Updated 10/21/21)
Previous Close: $234.17
YTD Return: 21.83%
1-Year Return: 36.00%
Bid: $234.83
Ask: $234.86
Expense Ratio: 0.03%
Volume: 2,839,751
Net Assets: $280.03B
Shares Outstanding: 1,192,321,373
Dividends: $0.72 (Quarterly)


# Data Wrangling and EDA

[Data Wrangling](https://github.com/harmoly/Springboard/blob/main/Capstone%203/Capstone%203%20-%20Data%20Wrangling.ipynb)

A snapshot of our data:

![image](https://user-images.githubusercontent.com/72481886/138651022-fa91b879-254f-4eca-8111-1e2c49d62195.png)

[EDA](https://github.com/harmoly/Springboard/blob/main/Capstone%203/Capstone%203%20-%20EDA.ipynb)

Here, we get a sense for VTI's opening prices over the last 2 decades:

![image](https://user-images.githubusercontent.com/72481886/138651167-9a44e85b-7dfb-4541-b3a9-dcb21dd8fda2.png)

...And its daily closings alongside its opening prices:

![image](https://user-images.githubusercontent.com/72481886/138651217-117a7d30-8813-43f5-b869-83f76fe41a88.png)

...Along with its daily highs and lows:

![image](https://user-images.githubusercontent.com/72481886/138651282-14b15b6d-9b5c-40b1-870c-468df9706e35.png)

Now, we want to decompose our data to assess things like seasonality and trend. This is visualized below for our price openings, since our distributions for each variable, besides volume, are roughly equivalent. So, we see VTI'S daily opening prices have displayed a general consistent increase over the last 20 years, and it exhibits a definite seasonal pattern.

![image](https://user-images.githubusercontent.com/72481886/138651335-8cb29540-3e0a-4448-80fc-7ec71cf3b8ea.png)

The KPSS test indicates our data is not stationary, so we take the logarithm of our data to eliminate any changing variance--and then we difference our data to obtain a constant mean. Now, our data is stationary:

![image](https://user-images.githubusercontent.com/72481886/138651412-bcce2915-292c-4aa5-8801-6d6280e992ac.png)

Now, we repeat the same process for volume. This is going to be our target variable for our model. Daily stock volume purchased depicted below:

![image](https://user-images.githubusercontent.com/72481886/138651467-6c1f2917-e384-483b-bde0-5277639e428c.png)

Again, the data exhibit a general increase over time, and again, seasonality:

![image](https://user-images.githubusercontent.com/72481886/138651536-e6d33184-89f6-422e-a1ec-b7ec08651a9f.png)

Following the same procedure as above, we obtain our stationary data:

![image](https://user-images.githubusercontent.com/72481886/138651600-32ad718a-da85-4c10-89fb-e7b21e76fc90.png)


# Preprocessing and Modeling

[Preprocessing and Training Data Development](https://github.com/harmoly/Springboard/blob/main/Capstone%203/Capstone%203%20-%20Preprocessing%20and%20Training%20Data%20Development.ipynb)

[Modeling](https://github.com/harmoly/Springboard/blob/main/Capstone%203/Capstone%203%20-%20Modeling%20(1).ipynb)

We will be using an ARIMA model for our data. We shall use our ACF and PACF to approximate our hyperparameters p and q. An ADF test gives us a value of 0, so this'll be our d. Based on the plots below, and after some testing, we decide select p, q = 3. Our approximation is confirmed with auto_arima. 

![image](https://user-images.githubusercontent.com/72481886/138651659-fbe05d9f-799a-440a-b2fb-2ee978ecdf5b.png)

Next, we assess our residuals...

![image](https://user-images.githubusercontent.com/72481886/138651729-115ad8cd-870b-4ae4-b4de-b5753b228601.png)

Pretty low variance, and a residual mean very close to 0.

![image](https://user-images.githubusercontent.com/72481886/138651774-6d481e65-f269-42b3-98fd-d6f99f6d913b.png)

Now, a plot of our predictions against the data.

![image](https://user-images.githubusercontent.com/72481886/138651827-172372ba-fb33-4361-b896-2909ceea7d7c.png)

And for a closer look--the same plot over the last year.

![image](https://user-images.githubusercontent.com/72481886/138651877-cf6f3401-6545-4d64-af87-0e114cd01abd.png)


# Results

SARIMAX Results
Dep. Variable:	Volume	No. Observations:	5034

Model:	ARIMA(3, 0, 3)	Log Likelihood	-3147.521

Date:	Wed, 20 Oct 2021	AIC	6311.042

Time:	18:22:29	BIC	6363.234


coef 	std err	z	P>|z|	[0.025	0.975]

const	14.2880	0.665	21.474	0.000	12.984	15.592

ar.L1	0.7276	0.068	10.670	0.000	0.594	0.861

ar.L2	0.9554	0.092	10.433	0.000	0.776	1.135

ar.L3	-0.6838	0.051	-13.453	0.000	-0.783	-0.584

ma.L1	-0.4210	0.070	-6.026	0.000	-0.558	-0.284

ma.L2	-0.9276	0.071	-13.042	0.000	-1.067	-0.788

ma.L3	0.4263	0.039	10.836	0.000	0.349	0.503

sigma2	0.2045	0.003	77.217	0.000	0.199	0.210

Ljung-Box (L1) (Q):	0.03	Jarque-Bera (JB):	3053.04

Prob(Q):	0.86	Prob(JB):	0.00

Heteroskedasticity (H):	0.32	Skew:	0.71

Prob(H) (two-sided):	0.00	Kurtosis:	6.54

