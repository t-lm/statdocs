# Accessing series in Microsoft Excel

This page explains how to use time series directly in Microsoft Excel.

The benefit is to accelerate discovery of series and use of multiple time series directly in Excel.

To get started, follow installation instructions.


## Installation

### Windows
- The Microsoft Excel add-in for Windows is under testing and will be released soon on Microsoft App Store

### Mac
- Download the Excel add-in file though the link on your home page (manifest.xml)
- Copy the file in: /Users/<username>/Library/Containers/com.microsoft.Excel/Data/Documents/wef
- Open Microsoft Excel - Click on Insert > Add-ins > My Add-ins and choose Statit Excel
- Prerequisites: Mac running OS X ("Yosemite" or later), Excel on Mac (version 15.19 or later)


## Signin-in

- Once the add-in opens, click on the "credentials" tab
- Enter your username
- Enter your API key (you will find this in your web account in the home tab)



## Simple queries

There are two types of queries in the add-in:
- simple queries where you get the data directly in the sheet where you are working
- batch queries where you specific the query in advance and run all the queries together

### Get a time serie

This is the simplest query.

- Insert the id of a serie in any cell (for instance, cvfr/hosp-dpt/paris/hosp_in)
- With the cell selected, press "GET"

The serie is returned starting in the cell below. Next to the id, you will find the status of the query, the date of the query, the size of the query (number of series returned).

If there is an error, look at these possible solutions:

- Fill-in your username and password
- Check the 'id' is correct by finding it on the web application
- Make sure you are online


### Get multiple time series

- Insert the ids of the series you are looking for separated with a ","
- With the cell selected, press "GET"


### List all time series in a collection or a specific path in the collection

- Insert the id of the collection or the path to the serie in any cell ending with a "\*" (cvfr/hosp-dpt/paris\*)
- With the cell selected, press "GET"

Notes:

- You can not perform multiple list queries separated with a ","


## Batch queries

To perform batch queries, insert a "batch" sheet inside your workbook

Starting on the 2nd line, add a line for every query (limited to 25):

- In the 1st cell, insert the query string (similar to simple queries)
- In the 2nd cell, insert the name of the target worksheet (where the response will be sent)
- In the 3rd cell, insert the name of the target cell (where response will be displayed)
- Press "BATCH"

For every query (on every line), you will get the following codes:

- Status: OK or error (first cell on the right after target cell)
- Date: full ISO date (second cell)
- Size: number of series returned (third cell)
