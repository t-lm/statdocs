# **Get Started with Microsoft Excel**

Statit can be used to access and edit metrics in Excel.

This section explains **how to start using Statit with Excel**. For the complete documentation covering Excel, please head over to the [**Excel reference**](reference/excel.md).

Before continuing, **please sign-in to your account [here](https://gostatit.com/signin)** or **create one [here](https://gostatit.com/signup)**.


## **Installation**

To use Statit in Microsoft Excel, you will **use the Statit add-in**.

You might need a recent version of Microsoft Excel and specific access rights to install the Statit add-in. Please consult your IT support if your installation fails.

In a Microsoft Excel workbook, go to the "Insertion" tab inside the workbook on the top of the workbook. Select 'Add-In', then 'Download Add-In', then 'Store'.

In Microsoft Add-in store, search for 'statit'. Once found, press 'add' to install the Statit add-in inside Microsoft Excel.

The Statit add-in will show as an icon on the right hand side of the the main menu. Great job!


## **Signin-in**

- Once the add-in opens, click on the "Sign in" tab
- Enter your username
- Enter your key (You will your 'key' by clicking on your username on the top right hand side of a Statit window on the web and selecting 'My account'. The key is a the bottom of the page)


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

- Insert the id of the parent of the series you want to get "\*" (cvfr/hosp-dpt/paris\*)
- With the cell selected, press "GET"

Notes:

- You can not perform multiple list queries separated with a ","


## Batch Get queries

To perform batch queries, insert a "batch" sheet inside your workbook

Starting on the 2nd line, add a line for every query (limited to 25):

- In the 1st cell, insert the query string (similar to a simple query)
- In the 2nd cell, insert the name of the target worksheet (where the response will be sent)
- In the 3rd cell, insert the name of the target cell (where response will be displayed)
- Press "BATCH"

For every query (on every line), you will get the following codes:

- Status: OK or error (first cell on the right after target cell)
- Date: full ISO date (second cell)
- Size: number of series returned (third cell)


## Put series

You can put series directly in the collections you have created in Statit.

You can not create a collection from inside Excel. Head over to the [web instructions](gs_web.md) to learn how to create a collection.

### A single serie

Starting anywhere in the sheet, present the serie you want to put in the following format:

- On line 1, in cell 1, write 'put' (without '')
- On line 2, in cell 1, write 'id' and in cell 2 the value of the 'id'
- On line 3, in cell 1, write 'name' and in cell 2 the value of the 'name'
- On line 4, in cell 1, write 'frequency' and in cell 2 the value of the 'frequency'
- On line 5, optionally, in cell 1, write 'unit' and in in cell 2 the value of the 'unit'
- On line 6, optionally, in cell 1, write 'description' and in in cell 2 the value of the 'description'
- On line 7, optionally, in cell 1, write 'sources' and in in cell 2 the value of the 'sources'
- On line 8, optionally, in cell 1, write 'notes' and in in cell 2 the value of the 'notes'
- On line 9, optionally, in cell 1, write 'version' and in in cell 2 the value of the 'version'. Version is a comment that is specifically linked to the version published
- On line 11, in cell 1, write the date (in YYYY-MM-DD) format (set the format of the cell as Text) and in cell 2, the value of the observation

Continue with observations on the following lines and press 'Put'.


### Metadata

You can add specific text metadata for each observation.

For instance, for a specific value, you might want to add a commentary. If you are looking to add metadata, you can use the column next to observations to do so.

On top of the column with metadata (next to the id of the serie), place a 'm' (for metadata).

### Multiple series

You can put multiple series as long as they share the same dates. Just, put the series in columns next to each other and select all series before pressing 'Put'.

The maximum amount of series is limited to 25 for the moment.


## Next steps

You have learnt the basics of using the Statit Excel add-in. If you would like to go further, you can integrate Statit to your own add-ins or build a specific one. See the Statit API [here](gs_api.md).
