# **Get started on the Web**

This page explains **how to start using Statit** with a web browser.

Before continuing, **please sign-in to your account [here](https://gostatit.com/signin)** or **create one [here](https://gostatit.com/signup)**.


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


### Downloading the metric

You might now need to work with this metric to compare it with other long-term trends, transform it or present it in a chart.

Click on the down arrow on the right hand side and select the format you are interested in. European and
UK & US formats differ in the decimal separator (',' for Europe and '.' for UK & US).


### Saving the metric as favorite

If you would like to save the metric to access it directly in your home page, click on the star on the top right of the screen.




### Collections

Metrics belong to collections which are groups of related metrics. You can navigate in the collection by clicking on the grey links just under the metric name.

Here is the link to the collection of [weekly exchange rate metrics](https://www.gostatit.com/xr/daily) that includes the metric we have looked at before.

Click on the "About" tab for a description of the collection.


### Next steps

You have now learnt the basics of accessing metrics on Statit: how to find a metric, how to use it and follow it, how to find a collection and navigate inside it.

If you would like to use metrics directly in Excel, please go to the [Excel section](gs_excel.md)

If you would like to building your own workspace and collections, continue reading.


## Workspace

### Creating a workspace

- Go to your home page and click on the "Collections" tab.
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
