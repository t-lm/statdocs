# Introduction

Statit is an online registry for time series.

At its core, Statit is a database of time series. Each time serie on Statit has a unique code that you will use to access the data.

## Time series

Statit only hosts time series. Time series are often thought of as time-based observations, i.e. a combination of a specific metric and a time.
Temperature measures, economic indices, social indicators are all time series.

Let's jump in with [monthly air temperature in Britanny in France](https://www.gostatit.com/climat-fr/cei-m/region/bretagne/temp)

As you click on the link, you will see a simple time serie on Statit. It is described by its name, an indicator, a description, various
properties such as its frequency, the unit, the sources, its start, its end and finally the serie presented as a chart.


## Making sense

Some of the series are hard to understand as such. This is the case for volatile measures that are highly seasonal and where the trend is
difficult to appreciate.

To that end, you can click on the small wheel on the right hand side. A menu will appear with different ways to change the data: changing the
frequency (from monthly data to yearly data for instant) or to average the data over last periods.

In our example, in Aggregation, select annual (and average). And, in Transformation, select last 4 periods. The underlying trend (increase
  in temperature) of roughly 1.5 degrees in the last 30 years will be easier to spot then.


## Downloading serie

You might now need to work with this data to compare it with other long-term trends, transform it or present it in a chart.

Click on the down arrow on the right hand side and select the format you are interested in. The difference between the European and
the UK & US formats lie in the decimal separator (, for Europe and . for UK & US)




## Saving serie





By focusing on time serie, Statit makes it simple


## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
