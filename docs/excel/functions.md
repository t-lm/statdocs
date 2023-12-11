# Using functions

You have two ways to get series in your workbook: custom functions and the taskpane. In this chapter, we will look at functions. 

## Getting started

To get started, type in any cell the formula =STAT.VALUE("xrate/monthly/eur/gbp"). All Statit functions will start with STAT followed by a keyword. STAT.VALUE allows you to get the latest value of a serie. 

If the add-in installation worked, you will get the result after a few seconds. If this is the case, jump straight to the next section. 

If not, look at the troubleshooting section at the end of the page. 

## Custom functions

### STAT.VALUE

This function will get the last value for a serie. 

Parameter: serieID - for example, "xrate/monthly/eur/gbp"
Parameter: number_periods (optional) - the number of periods before the last (by default, 0)
Returns: number - the latest value of the serie in a single cell, for example 1.08

Example 1: =STAT.VALUE("xrate/monthly/eur/gbp")
Example 2: =STAT.VALUE("xrate/monthly/eur/gbp", 3)

### STAT.VALUE_CHANGE

This function will get the change between the last value of the serie and another one

Parameter: serieID - for example, "xrate/monthly/eur/gbp"
Parameter: number_periods (optional) - the number of periods between the last value and the one considered (by default, 1)
Returns: number - the latest value of the serie in a single cell, for example 1.08

Example 1: =STAT.VALUE_CHANGE("xrate/monthly/eur/gbp")
Example 2: =STAT.VALUE_CHANGE("xrate/monthly/eur/gbp", 5)


### STAT.VALUE_CHANGE_PERCENT

This function will get the change in percentage between the last value of the serie and another one

Parameter: serieID - for example, "xrate/monthly/eur/gbp"
Parameter: number_periods (optional) - the number of periods between the last value and the one considered (by default, 1)
Returns: number - the latest value of the serie in a single cell, for example 1.08

Example 1: =STAT.VALUE_CHANGE_PERCENT("xrate/monthly/eur/gbp")
Example 2: =STAT.VALUE_CHANGE_PERCENT("xrate/monthly/eur/gbp", 5)

### STAT.SERIE

This function will get all observations for a serie with their dates and values. This is useful when we need the full historic perspective on the serie

Parameter: serieID - for example, "world-bank/pink/prices/agri/orange/usd"
Parameter: start (optional) - the start date for the observations (following the ISO format "YYYY-MM-DD")
Parameter: end (optional) - the end date for the observations (following the ISO format "YYYY-MM-DD")
Returns: an array with a a list of values and dates

Example 1: =STAT.SERIE("world-bank/pink/prices/agri/orange/usd")
Example 2: =STAT.SERIE("world-bank/pink/prices/agri/orange/usd", "2021")
Example 3: =STAT.SERIE("world-bank/pink/prices/agri/orange/usd", "2021", "2023-12")

### STAT.SERIE_LAST

This function will get the last X observations for a serie with their dates and values. 

Parameter: serieID - for example, "world-bank/pink/prices/agri/orange/usd"
Parameter: number_periods (optional) - the number of periods to get
Returns: an array with a a list of values and dates

Example 1: =STAT.SERIE_LAST("world-bank/pink/prices/agri/orange/usd")
Example 2: =STAT.SERIE_LAST("world-bank/pink/prices/agri/orange/usd", 6)

### STAT.SERIE_AVG

Gets all observations for a serie averaged over a period of time

Parameter: serieID - for example, "world-bank/pink/prices/agri/orange/usd"
Parameter: number_periods (optional) - the number of periods used to average the values
Parameter: start (optional) - the start date for the observations (following the ISO format "YYYY-MM-DD")
Parameter: end (optional) - the end date for the observations (following the ISO format "YYYY-MM-DD")
Returns: an array with a a list of values and dates

Example 1: =STAT.SERIE_AVG("world-bank/pink/prices/agri/orange/usd")
Example 2: =STAT.SERIE_AVG("world-bank/pink/prices/agri/orange/usd", 6)
Example 3: =STAT.SERIE_AVG("world-bank/pink/prices/agri/orange/usd", "2022")

## Troubleshooting

There are different possible issues

### The function is not recognised

In this case, when you type =STAT in any cell, Excel does not recognise the function. When you have finished typing, Excel return something like #NAME?. This means that the custom function is not yet recognised by Excel. 

The first option is check if the function has been loaded. Try clearing the add-in cache on the top right hand side of the add-in on the right and reloading the add-in. If it still does not work, try restarting Excel and try again. 

The second option is to clear Excel cache. This is not harmful operation. Please check online Microsoft documentation for "clearing excel cache". At the time of writing, documentation was located [here](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/clear-cache). 

If this still does not work, please get in touch with us at [help@gostatit.com](mailto:help@gostatit.com)

### An error occured

Other common types of errors are:
- you have no internet connection
- you need to fill-in your username and password
- the serieID you are using does not exist or you do not have the permission to access it