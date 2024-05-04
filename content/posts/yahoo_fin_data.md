---
template: post
title: Exporting Historical yahoo financial data to Csv files
slug: scrape-historical-yahoo-financial-data-to-csv
socialImage: static/media/Yahoo.jpeg
draft: false
date: 2024-05-27T19:27:32.169Z
description: Web Scraping Historical financial data from Yahoo using Package
category: Python
tags:
  - python
---
**Web Scrape the Financial data from Yahoo** 
Do you know there is a simple library in python where we can download the whole historical data for ticker symbols you have into the csv files or excel files the is **yfinance** package

let me tell you how we will use this library in python for scracping data

![Web Scrapping Yahoo financial data](/media/yahoo.jpeg)

## scraping single ticker historical data to a csv file

* For doing this you need to install python package as "Pip install yfinance".
* install pandas as "Pip install pandas".
* install date time as "pip install datetime"

```python
import yfinance as yahooFinance
import pandas as pd
import datetime

#Expoting historical yahoo financial data for single csv file
startDate = datetime.datetime(2019, 5, 31)
endDate = datetime.datetime(2021, 1, 30)

data = yahooFinance.Ticker("BMY")
 
# Valid options are period = 1d, 5d, 1mo, 3mo, 6mo, 1y,
# 2y, 5y, 10y and ytd.
findata = data.history(start=startDate,end=endDate)
findata.to_csv(r'/Users/swetha/Documents/fin_data/BMY.csv')
```

Now you can see you scraped data in your target location as csv file. 

<figure>
	<blockquote>
		<p>Its so simple to download a single file right what if you have thousands of ticker symbols to get the data we cant run the program thousand times right. Let me show you how to download data automatically for the multiple given ticker symbols</p>
		<footer>
		</footer>
	</blockquote>
</figure>

## exporting Financial Historical data for Multiple ticker symbols by saving them with its own ticker name as csv file

Now let's see how we will Scrape data for  mutlple ticker symbols and saving them individually with its own name

* This requires same packages as above

```python
#Expoting historical yahoo financial data for single csv file
startDate = datetime.datetime(2019, 5, 31)
endDate = datetime.datetime(2021, 1, 30)

data = yahooFinance.Ticker("BMY")
 
# Valid options are period = 1d, 5d, 1mo, 3mo, 6mo, 1y,
# 2y, 5y, 10y and ytd.
findata = data.history(start=startDate,end=endDate)
findata.to_csv(r'/Users/swetha/Documents/fin_data/BMY.csv')
```

If you dont want to save them individually and wanted all of scraped data for multiple ticker symbols in a single file you can use the below code

```python
#Exporting whole historical financial data to a single master data
df = pd.read_excel(r"/Users/swetha/Downloads/sample_ticker.xlsx")
comp = df["Symbol"]
startDate = datetime.datetime(2019, 5, 31)
endDate = datetime.datetime(2021, 1, 30)
result = pd.DataFrame()
#print(comp)
for i in comp:

    data = yahooFinance.Ticker("{}".format(i))
     
    # Valid options are period = 1d, 5d, 1mo, 3mo, 6mo, 1y,
    # 2y, 5y, 10y and ytd.
    findata = data.history(start=startDate,end=endDate)
    #print (findata)
    findata['Ticker'] = i
    result = result._append(findata)   
    print(result) 
result.to_csv(r'/Users/swetha/Documents/fin_data/master.csv')
```

That's it you have simply downloaded the data for multiple ticker symbol  very easily in no time. try it and save your time!!!!! binge coding :->