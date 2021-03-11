# Getting started with the REST API


This tutorial will show you the main operations to access and push time series on Statit.

It is split in two sections:

- Accessing time series
  - Getting a single time serie
  - Getting a list of time series in a collection

- Pushing time series
  - Creating a collection of time series
  - Putting series in the collection
  - Adding authorisation for collaborators

The API relies on POST requests to the API end point.

This API version is 2021-02-12

## Set-up

#### Authentication

To perform requests, you will need credentials: your username and API Key.

Your username is the one you defined on Statit and your API key can be found in your account section in the home page for your profile.

#### End-point

All requests are addressed to the following URL https://api.gostatit.com/core

curl -X POST -H "Content-Type: application/json" \
    -d '{"name": "linuxize", "email": "linuxize@example.com"}' \
    https://example/contact


```javascript
var s = "JavaScript syntax highlighting";
alert(s)
```


### Requests format

The API accepts POST requests on the above end point.

## Getting time series

###
