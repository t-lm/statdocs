# Publishing series on the web

This page explains how to publish time series using the web application.


## Collections and series

Time series are published inside collections.

Collections are groups of time series on a specific subject. Inside a collection, your time series will relate to a similar subject, cover a similar time range and be structured in the same way.

You can see how collections look like here:

- [French departmental air pollution indicators](https://www.gostatit.com/airhebdo/dpt)
- [Long-term energy consumption in France](https://www.gostatit.com/hdu/enr)

Inside collections, you will place time series.

Time series have unique identifiers similar to files on a computer. They follow the following format: [username] / [collection key] / [serie path]:

- username is your username with no capital letters
- collection key is a specific identifier for the collection (only alpha-numerical characters and point, underscore and dash characters)
- serie path is a specific identifier for the serie in the collection (same characters as collection key and slash )

Slashes can be added to the serie path. This is a way to structure how you navigate inside your collection. The slashes play the role of subfolders.

For instance, the serie [bdf-conj/commn/categorie/chaussure/indice-valeur/brut](https://www.gostatit.com/bdf-conj/commn/categorie/chaussure/indice-valeur/brut) has the following structure:

- username: bdj-conj
- collection key: commn
- serie path: categorie/chaussure/indice-valeur/brut

Collections are either public or private. Public collections will be accessible by anyone on the web. Private collections (and the series inside) will only be visible to the authorised collaborators.


## Creating a collection

- Go to the home page and click on the "publications" tab.
- On the right hand side, click on "Add collection"
- Fill the required fields for the collection: key, name, about ...
- Press save


## Adding a serie

Now that your collection is created, you can add your first serie:

- Click on the collection
- On the top right hand side, click on "Add serie"
- Fill the required field for the time serie
- Press save

You have two options for adding observations:

- Load a CSV file with the serie observations
- Write (or paste) values manually

We currenly only accept observations with the following format:

- Dates following the ISO 8601 format: YYYY-MM-DD (for example: 2021-01-02)
- Values with decimal separator as a point
- Each observation is on one line (date, observation)
- Date and observations must be split by either "," or ";" or a tab


## Adding multiple series

We are currently developing a way to bulk upload the series. Stay tuned for the next release.


## Adding series through the API

We are currently developing the documentation for the API
