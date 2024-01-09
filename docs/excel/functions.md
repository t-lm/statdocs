# Using functions

You have two ways to get series in your workbook: custom functions and the taskpane. In this chapter, we will look at functions. 

## Getting started

To get started, type in any cell the formula =STATIT_OBS("xr/monthly/eur/gbp"). All Statit functions will start with STATIT followed by a keyword. STATIT_OBS allows you to get the latest value of a serie. 

If the add-in installation worked, you will get the result after a few seconds. 

Now copy paste the formula  =STATIT_SERIE("xr/monthly/eur/gbp"). This should return an array with two columns. The first one represents the date of the observation, the second one represents the value of the observation. 

The date is represented as a number as this is the way it is coded in Excel. To make sense, select the date column and format it as a Date.

If all works fine, jump straight to the next section. Note that all examples use international formating with function arguments separated with a ",". In certain countries, you might have to replace the commas with a ";". 

If you are facing problems, look at the troubleshooting section at the end of the page. 

## Custom functions


### STATIT_OBS

This function will display the value of the last observation for a serie

- Parameter: id - for example, "xr/monthly/eur/gbp"
- Parameter: periods (optional) - the number of periods starting from the most recent one (by default, the last period or 1)
- Returns: number - the latest value of the serie in a single cell, for example 1.08

Examples: 

- =STATIT_OBS("xr/monthly/eur/gbp")
- =STATIT_OBS("xr/monthly/eur/gbp", 3)

### STATIT_OBS_CHANGE

This function will get the change between the last value of the serie and another one

- Parameter: id - for example, "xr/monthly/eur/gbp"
- Parameter: periods (optional) - the number of periods between the last value and the one considered (by default, 1)
- Returns: number - the latest value of the serie in a single cell, for example 1.08

Examples:

- =STATIT_OBS_CHANGE("xr/monthly/eur/gbp")
- =STATIT_OBS_CHANGE("xr/monthly/eur/gbp", 5)


### STATIT_OBS_CHANGE_PERCENT

This function will get the change in percentage between the last value of the serie and another one

- Parameter: id - for example, "xr/monthly/eur/gbp"
- Parameter: periods (optional) - the number of periods between the last value and the one considered (by default, 2)
- Returns: number - the latest value of the serie in a single cell, for example 1.08

Examples:

- =STATIT_OBS_CHANGE_PERCENT("xr/monthly/eur/gbp")
- =STATIT_OBS_CHANGE_PERCENT("xr/monthly/eur/gbp", 5)

### STATIT_OBS_DATE

This function will display the date of the last observation

- Parameter: id - for example, "xr/monthly/eur/gbp"
- Parameter: periods (optional) - the number of periods starting from the most recent one (by default, the last period or 1)
- Returns: number - the latest value of the serie in a single cell, for example 1.08

Example: 

- =STATIT_OBS_DATE("xr/monthly/eur/gbp")

### STATIT_SERIE

This function will get all observations for a serie with their dates and values. This is useful when we need the full historic perspective on the serie

- Parameter: id - for example, "world-bank/pink/prices/agri/orange/usd"
- Parameter: observations (optional) - the number of observations to return
- Parameter: direction (optional) - the direction of the observation, 1 for the chronological order, -1 for the opposite
- Returns: an array with a a list of values and dates

Examples:

- =STATIT_SERIE("world-bank/pink/prices/agri/orange/usd")
- =STATIT_SERIE("world-bank/pink/prices/agri/orange/usd",4)
- =STATIT_SERIE("world-bank/pink/prices/agri/orange/usd",6,-1)

### STATIT_SERIE_H

This is the same function as the one above but this will return observations horizontally.

### STATIT_SERIE_CHANGE

Gets all observations for a serie averaged over a period of time

- Parameter: id - for example, "world-bank/pink/prices/agri/orange/usd"
- Parameter: periods (optional) - the number of periods used to average the values
- Parameter: observations (optional) - the number of observations to return
- Parameter: direction (optional) - the direction of the observation, 1 for the chronological order, -1 for the opposite
- Returns: an array with a a list of values and dates

Examples:

- =STATIT_SERIE_CHANGE("world-bank/pink/prices/agri/orange/usd")
- =STATIT_SERIE_CHANGE("world-bank/pink/prices/agri/orange/usd",6)
- =STATIT_SERIE_CHANGE("world-bank/pink/prices/agri/orange/usd",6,4)
- =STATIT_SERIE_CHANGE("world-bank/pink/prices/agri/orange/usd",6,4,-1)

## Troubleshooting

There are different possible issues

### The function is not recognised

In this case, when you type =STATIT in any cell, Excel does not recognise the function. When you have finished typing, Excel return something like #NAME?. This means that the custom function is not yet recognised by Excel. 

The first option is check if the function has been loaded. Try clearing the add-in cache on the top right hand side of the add-in on the right and reloading the add-in. If it still does not work, try restarting Excel and try again. 

The second option is to clear Excel cache. This is not harmful operation. Please check online Microsoft documentation for "clearing excel cache". At the time of writing, documentation was located [here](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/clear-cache). 

If this still does not work, please get in touch with us at [help@gostatit.com](mailto:help@gostatit.com)

### An error occured

Other common types of errors are:
- you have no internet connection
- you need to fill-in your username and password
- the id you are using does not exist or you do not have the permission to access it