# Accessing series

You are now ready to access series directly in Excel.


## Downloading a serie

To download a single serie, write in any cell the identifier of a public collection.

Take for instance the serie 'eustat/apro_mk_colm/de/raw_milk_delivered' that represents the volumes of milk delivered by farms in Germany.

Select the cell with the serie and click on "Go". That is it. After a few seconds, the serie is available in the sheet

![Installer complément](/img/user-fr_excel_access_0.png){: style="width:600px;margin:30px;padding:20px;border:1px solid #ddd;border-radius:5px"}


## Downloading a serie horizontally

Another way to download the serie above is to write in a cell 'get:eustat/apro_mk_colm/de/raw_milk_delivered' (do not put '').

'get' is used to download a serie vertically. 'geth' is used to get a serie horizontally.

In a different place in the worksheet, write 'geth:eustat/apro_mk_colm/de/raw_milk_delivered'. Select the cell. Click go. The serie appears now horizontally


## Downloading multiple series

It is possible to download multiple series with a single call. You only have to separate them with commas.

The formula 'get:xrate/monthly/eur/cad,xrate/monthly/eur/aud,xrate/monthly/eur/usd' lets you download the three exchange rate series (CAD, AUD, USD) against Euro.


## Downloading all series from a collection

It is possible to download multiple series from the same collection (or from the same directory, remember, a collection is organised like a directory of files).

For instance, to get all monthly metrics against Euro, you can use the following formula 'get:xrate/monthly/eur/\*'. '\*' means all series with an identifier starting with 'xrate/monthly/eur/'.

This requests returns 31 results.


## Next steps

We have presented basic commands for Statit in Excel. If you would like to publish metrics, please head over to the [publisher guide](http://helppub_en.gostatit.com).
