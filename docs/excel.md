# Statit on Microsoft Excel

This page explains how to access, create and edit time series in Microsoft Excel using the Statit Excel add-in.

The Statit Excel "add-in" will allow you to perform basic operations. If you want to go further, you can develop your own add-ins and use the [Statit API](api.md).


## Installation

In an Excel workbook, go to the "Insertion" tab inside the workbook. Look for "Add-Ins" or "Download Add-ins".

On Microsoft Add-in store, search for 'statit'. Press add to install the Statit add-in.

The add-in will show as an icon on the right in the main menu. Good job.


## Signin-in

- Once the add-in opens, click on the "Sign in" tab
- Enter your username
- Enter your API key (you will find this in your web account in the home tab)


## Get series

There are two ways to run queries in the add-in:
- Get - You specify the query and get the response directly in the sheet where you are working
- Batch get - You specify multiple queries in advance, run the queries all together and get the response where it suits you

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


## Batch Get queries

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


## Put series

You can put series directly in the collections you have created in Statit.

You can not create a collection from inside Excel. Head over to the [web instructions](web.md) to learn how to create a collection.

### A single serie

Starting anywhere in the sheet, present the serie you want to put in the following format:

- On line 1, in cell 1, write 'put' (without '')
- On line 2, in cell 1, write 'id' and in cell 2 the value of the 'id'
- On line 3, in cell 1, write 'name' and in cell 2 the value of the 'name'
- On line 4, in cell 1, write 'frequency' and in cell 2 the value of the 'frequency'
- On line 5, in cell 1, write 'unit' and in in cell 2 the value of the 'unit'
- On line 8, in cell 1, write the date (in YYYY-MM-DD) format (set the format of the cell as Text) and in cell 2, the value of the observation

Continue with observations on the following lines and press 'Put'.

### Multiple series

You can put multiple series as long as they share the same dates. Just, put the series in columns next to each other and select all series before pressing 'Put'.

The maximum amount of series is limited to 25 for the moment.


## Next steps

You have learnt the basics of using the Statit Excel add-in. If you would like to go further, you can integrate Statit to your own add-ins or build a specific one. See the Statit API [here](api.md).
