---
title: "Pros and Cons of Stock APIs"
datePublished: Thu Dec 15 2022 08:46:58 GMT+0000 (Coordinated Universal Time)
cuid: clbou8cu3000f08l32gb12j9h
slug: pros-and-cons-of-stock-apis
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1671833049761/97081e64-f4ef-407b-b354-e9e478e23266.png
tags: stocks-api, python-stock-library, financila-api

---

Real-time and historic stock or other financial datasets are very essential for developing financial applications. Developers and Data Engineers typically want to extract data from Application Programming Interfaces (API) from within their code. There are many stock APIs out there, therefore could be a bit difficult to decide on which API to use.

We will be looking at some of the popular ones out there and comparing them based on cost, how well-supported the API is, ease of use, limitations on the size of the dataset, and support for real-time data.

In terms of cost, some are free, others give free days of trial, while some are not free and don’t give free trial.

We can measure how well-supported an API is by its last update, for example in the case of a python library of an API, the last date of update in PyPi. We can also measure this by the frequency of updates of their GitHub repository.

# **Yahoo Finance**

Yahoo Finance publishes free stock data from the major stock market around the world.

**Pros:**

· It is free

· We can get a huge amount of data from it

· It has two well-supported Python libraries, pandas-datareader library as well as the yfinance library. The libraries simplify the extraction and use of the data by reducing the amount of code. The latest release for yfinance was on Nov 16, 2022

**Cons:**

· The API is not an official Yahoo Finance API

· Only basic dataset can be retrieved

· Because it is unofficial, the rate of API calls could be limited

# **Alpha Vantage**

Alpha Vantage provides enterprise-grade real-time and historical financial market data through a set of powerful and developer-friendly data APIs and spreadsheets. Delivered through REST stock APIs, Excel, and Google Sheets.

Pros:

· It has a python library, but it is not popular

· It is suitable for commercial applications

· Supports real-time and historical financial market data

Cons:

· It is not free.

· It has an unofficial python library that is not well supported of which the latest release is July 4, 2021

# **Bloomberg API**

Pros:

· it has an official python library

· suitable for commercial applications

· Supports real-time and historical financial market data

Cons:

· Not free. Start at $2000 per month

· Its python library is not well supported. The latest version was released Jan 1, 2019

# **Stock News**

Focused on stock news and summary reports

Pros:

· Good at stock news

Cons:

*   No custom python library. You make us of request to get data in json format.
    
*   Gives a 14-day free trial plan starting at $19.99 per month.
    
*   Requires details like card number and name on the card to make payment.
    

# **IEX Cloud**

Pros:

· Has a free trial

· Supports real-time and historical financial market data

Cons:

*   No custom python library. You make us of request to get data in json format.
    
*   Not free. Starting at $49
    

# **Morning star**

Pros:

· Has a python library

Cons:

*   Not free.
    
*   Python library is not well supported. The latest release was Jun 16, 2020
