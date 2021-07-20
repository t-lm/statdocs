# Statit on the Web

This page explains **how to start using Statit** with a web browser. Before continuing, **please sign-in to your account [here](https://gostatit.com/signin)** or **create one [here](https://gostatit.com/signup)**.


## Organisation

Statit is a platform where teams manage their metrics. Metrics are placed inside **workspaces** and **collections**.

**Workspaces are created for teams or organisations**. In the following example, we will access the "**xr**" **workspace**. This workspace gathers **exchange rates** metrics (xr for exchange rates). It is a "public workspace" accessible by every user on Statit.

Collections are used to **group similar metrics inside a workspace**. Collections are created for every subject or source of data. Below, we will start working with the "**xr/weekly**" collection that includes all **weekly exchange rate metrics**.


## Metrics

### A metric

Statit stores metrics. We define a metric as one or a set of observations over time.

Let's have a look at [the weekly Euro-Swiss Franc exchange rates](https://www.gostatit.com/xr/weekly/eur/chf). As you click on the link, you will reach the page of the metric. It is described by its name, description, unit and finally its observations presented as a chart.


### Understanding the metric

Looking at the chart is a first step.

We might be interested in the value at a specific point in time. Use the cursor below the graph to zoom on the period that is relevant. Move your mouse on the chart to look at a specific value.

If you are interested in exploring the numbers, click on the "grid" on the top left hand corner of the chart. This will allow you to browse the metric as a table of numbers.


#### Looking at trends

Some of the metrics are hard to understand as they go up and down frequently. See [Hungarian Florin against EUR](https://www.gostatit.com/xr/weekly/eur/huf)

We need a way to understand the trends. Averaging the observations of the last 8 weeks would allow us to understand the mid-term trend.

On the metric page above, find the small wheel on the top right hand side of the chart. A menu will appear with different ways to look at the metric such as changing the period of reporting.

In the example above, in Transformation, select last 8 periods. The underlying trend
of


### Downloading the metric

You might now need to work with this data to compare it with other long-term trends, transform it or present it in a chart.

Click on the down arrow on the right hand side and select the format you are interested in. European and
the UK & US formats differ in the decimal separator in numbers (',' for Europe and '.' for UK & US).


### Following the metric

If you are interested in the metric and would like to save it for future reference, click on the star on the top right of the screen. You will need to be signed-in to access that feature.

The metrics you follow will be accessible from your home page in the favorites tab. On this tab, you will be able to set a notification when to get an alert when the metric is updated.


### Exploring previous versions

On the metric page, below the 'path' of the metric, you will find a "Version" badge indicating 'last' or a specific version date. Click on 'Version' to list all the versions of the metric.

Click on a specific version to access the metric as it was for this version.


### Collections

metrics belong to collections which are groups of related metrics. You can navigate in the collection by clicking on the grey links just under the metric name.

Here is the link to the collection of [long-term monthly air temperatures](https://www.gostatit.com/climat-fr/cei-m) that includes the metric we have looked at before.

The collection page will provide the background on the metrics included: rationale, sources, methodology, structure, contact details ...


### Next steps

You have now learnt the basics of Statit: how to find a metric, how to use it and follow it, how to find a collection and navigate inside it.

If you would like to use metrics directly in Excel, please go to the [Excel section](gs_excel.md)

If you would like to start your own collections, continue reading.



## Building a collection

### Access

Building collections on Statit is for the moment limited to "beta" users. You are welcome to get started, please get in touch at [hi@gostatit.com](mailto:hi@gostatit.com).

The following guide is for users with access to that feature.


### Collections and metrics

metrics are placed inside collections.

Collections represent metrics on a similar subject, time range, structure or audience. You can visit the following public collections to get a sense of what they are:

- [French departmental air pollution indicators](https://www.gostatit.com/airhebdo/dpt)
- [Monthly indices of retail activity in France](https://www.gostatit.com/bdf-conj/commn)


metrics have unique identifiers similar to file names on a computer.

metric identifiers follow the format: [username] / [key of the collection] / [key of the metric]:

- username: the username of the collection administrator
- key of the collection: the specific identifier for the collection (only alpha-numerical characters and point, underscore and dash characters)
- key of the metric: specific identifier for the metric in the collection (same characters as collection key and slash )

Slashes can be added to the key of the metric. Slashes are a way to structure the navigation inside your collection. The slashes play the role of subfolders when browsing the collection.

For instance, the metric [bdf-conj/commn/categorie/chaussure/indice-valeur/brut](https://www.gostatit.com/bdf-conj/commn/categorie/chaussure/indice-valeur/brut) has the following structure:

- username: bdj-conj (stands for "banque de france - conjoncture" - an account dedicated to tracking)
- key of the collection: commn (stands for commerce national)
- key of the metric: categorie/chaussure/indice-valeur/brut

Collections are either public or private. Public collections will be visible by anyone on the web and metrics accessible by anyone on the web.

Private collections (and the metrics inside) will only be visible and accessible by the authorised collaborators.


### Creating a collection

- Go to the home page and click on the "Collections" tab.
- On the right hand side, click on "Add collection"
- Fill the required fields for the collection: key and name
- Press save


### Adding a metric

Now that your collection is created, you can add your first metric:

- Click on the collection
- On the top right hand side, click on "Add metric"
- Fill the required field for the metric
- Press save

You have two options for adding observations:

- Load a CSV file with the metric observations
- Write (or paste) values manually

We currently only accept observations with the following format:

- Dates following the ISO 8601 format: YYYY-MM-DD (for example: 2021-01-02)
- Values with decimal separator as a point
- Each observation is on one line (date, observation)
- Date and observations must be split by either "," or ";" or a tab

#### Observation-level metadata

You can add text metadata at observation level. To do so, add the metadata value after the value.

If you choose to add metadata to an observation, you will need to add a metadata field to all observations. This field can be empty ("") but will need to exist


### Adding authorisations

By default, your collection and the metrics it includes are private. The owner is the only one who can see them.

To collaborate with others, you need to add access rights to the collection.

There are four different types of rights you can provide to other users:
- Observer - This allows the user to view the collection and its metrics
- Member - This allows the user to view the collection, its metrics and participate with comments
- Editor - This allows the user to view and edit the collection
- Administrator - This allows the user to view, edit the collection and manage access rights

You add users with their email or their Statit username. For the moment, you can only invite users with a live account on Statit . Users can create an account for free on the [sign-up page](https://gostatit.com/signup)

#### Public collections

If you want to make your collection publicly visible. Add a user with the username 'public'.


### Next steps

You have now learnt the basics of building and sharing a collection on Statit.  

If you would like to put metrics directly from Excel, please go to the [Excel section](gs_excel.md)

If you would like to learn how to work with Statit using the API, go [here](gs_api.md)
