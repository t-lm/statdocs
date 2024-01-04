# Using functions

In Google Sheets, you access series using specific functions. 



## Getting started

To get started, type in any cell the formula =STAT_OBS("xr/monthly/eur/gbp"). All Statit functions will start with STAT followed by a keyword. STAT_OBS allows you to get the latest value of a serie. 

If the add-in installation worked, you will get the result after a few seconds. If this is the case, jump straight to the next section. 

If not, look at the troubleshooting section at the end of the page. 

## Custom functions

### STAT_OBS

This function will get the last value for a serie. 

Parameter: serieID - for example, "xr/monthly/eur/gbp"
Parameter: number_periods (optional) - the number of periods before the last (by default, 0)
Returns: number - the latest value of the serie in a single cell, for example 1.08

Example 1: =STAT_OBS("xr/monthly/eur/gbp")
Example 2: =STAT_OBS("xr/monthly/eur/gbp", 3)

### STAT_OBS_CHANGE

This function will get the change between the last value of the serie and another one

Parameter: serieID - for example, "xr/monthly/eur/gbp"
Parameter: number_periods (optional) - the number of periods between the last value and the one considered (by default, 1)
Returns: number - the latest value of the serie in a single cell, for example 1.08

Example 1: =STAT_OBS_CHANGE("xr/monthly/eur/gbp")
Example 2: =STAT_OBS_CHANGE("xr/monthly/eur/gbp", 5)


### STAT_OBS_CHANGE_PERCENT

This function will get the change in percentage between the last value of the serie and another one

Parameter: serieID - for example, "xr/monthly/eur/gbp"
Parameter: number_periods (optional) - the number of periods between the last value and the one considered (by default, 1)
Returns: number - the latest value of the serie in a single cell, for example 1.08

Example 1: =STAT_OBS_CHANGE_PERCENT("xr/monthly/eur/gbp")
Example 2: =STAT_OBS_CHANGE_PERCENT("xr/monthly/eur/gbp", 5)

### STAT_SERIE

This function will get all observations for a serie with their dates and values. This is useful when we need the full historic perspective on the serie

Parameter: serieID - for example, "world-bank/pink/prices/agri/orange/usd"
Parameter: start (optional) - the start date for the observations (following the ISO format "YYYY-MM-DD")
Parameter: end (optional) - the end date for the observations (following the ISO format "YYYY-MM-DD")
Returns: an array with a a list of values and dates

Example 1: =STAT_SERIE("world-bank/pink/prices/agri/orange/usd")
Example 2: =STAT_SERIE("world-bank/pink/prices/agri/orange/usd", "2021")
Example 3: =STAT_SERIE("world-bank/pink/prices/agri/orange/usd", "2021", "2023-12")

### STAT_SERIE_AVERAGE

Gets all observations for a serie averaged over a period of time

Parameter: serieID - for example, "world-bank/pink/prices/agri/orange/usd"
Parameter: number_periods (optional) - the number of periods used to average the values
Parameter: start (optional) - the start date for the observations (following the ISO format "YYYY-MM-DD")
Parameter: end (optional) - the end date for the observations (following the ISO format "YYYY-MM-DD")
Returns: an array with a a list of values and dates

Example 1: =STAT_SERIE_AVERAGE("world-bank/pink/prices/agri/orange/usd")
Example 2: =STAT_SERIE_AVERAGE("world-bank/pink/prices/agri/orange/usd", 6)
Example 3: =STAT_SERIE_AVERAGE("world-bank/pink/prices/agri/orange/usd", "2022")

## Troubleshooting

There are different possible issues:
- You need to fill-in your username and password - 
- The serieID you are using does not exist or you do not have the permission to access it