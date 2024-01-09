# Using functions

In Google Sheets, you access series using specific functions. 

## Getting started

To get started, type in any cell the formula =STATIT_OBS("xr/monthly/eur/gbp"). All Statit functions will start with STAT followed by a keyword. STATIT_OBS allows you to get the latest value of a serie. 

If the add-in installation worked, you will get the result after a few seconds. If this is the case, jump straight to the next section. 

If not, look at the troubleshooting section at the end of the page. 

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

There are different possible issues:
- You need to fill-in your username and password - 
- The serieID you are using does not exist or you do not have the permission to access it