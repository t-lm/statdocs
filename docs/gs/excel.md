# **Get Started with Microsoft Excel**

Statit can be used to access and edit metrics in Excel.

Make sure you have read [**getting started with Statit on the web**](/gs/web.md) to understand the basics of how Statit works.

This section explains **how to start using Statit with Excel**. For the complete documentation covering Excel, please head over to the [**Excel reference**](/reference/excel.md).

Before continuing, **please sign-in to your account [here](https://gostatit.com/signin)** or **create one [here](https://gostatit.com/signup)**.


## **Installation**

To use Statit in Microsoft Excel, you will **use the Statit add-in**.

You might need a recent version of Microsoft Excel and specific access rights to install the Statit add-in. Please consult your IT support if your installation fails.

Follow these steps to install the add-in:

- In a Microsoft Excel workbook, go to the "Insertion" tab inside the workbook on the top of the workbook.
- Select 'Add-In'
- Select 'Download Add-In'
- Select 'Store'
- In Microsoft Add-in store, search for 'statit'
- Once found, press 'add' to install the Statit add-in inside Microsoft Excel

The Statit add-in will show as an icon on the right hand side of the the main menu. Great job!


## **Signin-in**

- Once the add-in opens, click on the "Sign in" tab
- Enter your username
- Enter your key (You will find your 'key' by clicking on your username on the top right hand side of a Statit window on the web and selecting 'My account'. The key is a the bottom of the page)

![Sign-In](/img/gs_excel_signin.png)


## **Get a metric**

Metrics on Statit are defined by a single 'id' or identifier.

To access the metric:

- Insert the 'id' of a metric in any cell (for instance: xr/weekly/eur/chf)
- Select the cell and press "Go"

The metric is returned starting in the cell below. Next to the id, you will find the status of the query, the date of the query, the size of the query (number of metrics returned).

If there is an error, look at these possible solutions:

- Fill-in your username and key
- Make sure the 'id' is correct by finding it on the web application
- Make sure you are online and you have the rights to access the metric

![Get a metric](/img/gs_excel_get.png)

### Horizontal display

You might need observations to be displayed horizontally.

To achieve this:

- Replace the "id" of the metric by 'geth:' followed by the id
- Select the cell and press Go


## **Get multiple metrics**

To achieve this:

- Insert the ids of the metrics you are looking for separated with a "," (for instance: xr/weekly/eur/chf,xr/weekly/eur/gbp,xr/weekly/eur/idr)
- With the cell selected, press "Go"


## **List all metrics with a specific parent id**


- Insert the parent id followed by "\*", for instance: xr/weekly/eur\*
- With the cell selected, press "Go"



## **Next steps**

You have learnt the basics of accessing one or multiple metrics with the Statit Excel add-in. If you would like to go further, please follow the full [Excel reference](/reference/excel.md).

You might as well develop your own Excel add-ins using Macros or Javascript. If you would like to achieve this, see the Statit API [here](/gs/api_rest.md).
