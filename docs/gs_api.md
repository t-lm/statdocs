# Getting started with the REST API


This tutorial will show you the main operations to access and push time series on Statit.

It is split in two sections:

- Set-up and basic concepts
- Accessing time series
  - Getting a single time serie
  - Getting a list of time series in a collection

- Pushing time series
  - Creating a collection of time series
  - Putting series in the collection
  - Adding authorisation for collaborators

The API relies on POST requests to the API end point.

API version: v1.0.1

## Set-up and basic concepts

#### API format

The API accepts simple HTTP GET and POST requests on the end-point defined below.

For the sake of simplicity, all examples will be presented using 'curl'. You can of course execute the requests in the language of your choice.


#### End-point

All requests are addressed to the URL https://api.gostatit.com/core. Core stand for the core API.

```bash
### request

curl https://api.gostatit.com/core

### response

{
  "message": "Welcome on Statit core API"
}
```

#### Authentication

To perform requests, you will need to use credentials: your username and API Key.

Your username is the one you defined on Statit and your API key can be found in the account section in the home page for your profile.

For the moment, the API uses basic Http authentication. On the command line, it looks like

```bash
### request

curl  -X POST \
      -u username:apiKey \
      https://api.gostatit.com/core

### response

{
    "code": "ERROR_PARAM_REQUIRED",
    ...
}
```

#### Actions

Once you are authentified, it is time to call specific actions: getSerie, getCollection, putSerie ...

We will do this by adding a json object to the query specifying the action called and the inputs required.


```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "getSerie", "input": {"id": "climat-fr/cei-m/region/bretagne/temp"}}' \
    https://api.gostatit.com/core

### response

{
  "Item": {
  "unit": "Degree Celcius",
  ...
  }
}

```

In the request above, we call the 'getSerie' action to get a single serie and pass a parameter called input with the 'id' of the serie we are requiring.

If you would like to learn the basics about serie identification, please head over to [Getting started on the web](gs_web.md).


#### Errors

If your request can not be processed, the API will return an error code with an error message.


```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "getSerie" }' \
    https://api.gostatit.com/core

### response

{
  "code": "ERROR_PARAM_REQUIRED",
  "message": "Error. Your request is missing a required parameter. Please check the documentation"
}

```


#### Next steps

That's it. You have learnt the basics of how the API works. Head-over to the next sections to understand how to get time series from a registry or create a collection and push time series inside.


## Accessing time series

### Getting a single time serie

We have already explored this request in the example above.

#### Example:

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "getSerie", "input": {"id": "climat-fr/cei-m/region/bretagne/temp"}}' \
    https://api.gostatit.com/core

### response

{
  "Item": {
    "unit": "Degree Celcius",
    "frequency": "M",
    "sources": [ "Copernicus. Climate and Environmental Series" ],
    "name": "Monthly real temperature",
    "updated": "2021-03-10T17:14:45.504Z",
    "notes": [],
    "observations": "[[\"1979-01-01\", \"1.6\"], [\"1979-02-01\", \"5.3\"], [\"1979-03-01\", \"6.7\"], [\"1979-04-01\", \"8.5\"], [\"1979-05-01\", \"11.0\"], [\"1979-06-01\", \"14.6\"] ..."
    "description": "Average monthly temperature (degree Celcius)",
    "id": "climat-fr/cei-m/region/bretagne/temp",
    "tags": []
  }
}
```


#### Parameters

- action: 'getSerie'
- input: { id: 'id' of the serie requested }

#### Response:

There are three different responses:

- If you are not authorised to access this collection, you will receive an error.
- If you are authorised to access the collection and the serie exists, you will receive a JSON response with an Item object.
- If are authorised to access the collection but the serie does not exist, you will receive an empty object

The Item object is quite explicit. It contains both serie metadata and observations in a "stringified" array.


### Listing time series in a collection

#### Introduction

It is possible to get multiple series in a single go.

For the moment, the API accepts requests that specify the parent and will provide all the "children" series.

As an example, if we are looking to get all waste indicators for "déchets ménagers associés" in the "Paris" department, we will query [dechets-fr/dma-dpt/paris/dechets-menagers-associes](https://gostatit.com/dechets-fr/dma-dpt/paris/dechets-menagers-associes).

It is necessary to specify exactly the id of the parent. The response returned will have a maximum size of 1MB.


#### Example:

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "listSeries", "input": {"id": "dechets-fr/dma-dpt/paris/dechets-menagers-associes"}}' \
    https://api.gostatit.com/core

### response

{
  "Items": [
    {
      "unit": "Tons",
      "frequency": "Y",
      "sources": [ "Base Sinoe de l'Ademe" ],
      "name": "Paris | Déchets ménagers et associés | Valorisation énergétique",
      "updated": "2021-02-24T07:05:32.120Z",
      "observations": "[[\"2009-01-01\", \"842125.33407\"], [\"2011-01-01\", \"833876.24514\"], [\"2013-01-01\", \"803965.81276\"], ...]",
      "description": "Paris. Déchets ménagers et associés. Valorisation énergétique",
      "id": "dechets-fr/dma-dpt/paris/dechets-menagers-associes/valo_energetique"
    },
    {...}
  ]
}

```


#### Parameters

- action: 'listSeries'
- input: { id: 'id' of the parent }

#### Response:

There are three different responses:

- If you are not authorised to access this collection, you will receive an error.
- If you are authorised to access the collection and children series exist, you will receive a JSON response with an Items object containing all the series.
- If are authorised to access the collection but the serie does not exist, you will receive an empty object

The items in the Items array are the same as the Item in getSerie


## Pushing time series

We recommended you try building a collection and pushing time series first using the web interface. Follow the [documentation](gs_web.md) to understand the main concepts.

In this tutorial, we will only recap the main steps to:

- Create a collection
- Add series to the collection
- Add authorisations to the collection

### Creating a collection

You create a new collection by providing its 'id' and its 'name'.


#### Example:

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "putCollection", "input": \
      {"id": "[USERNAME]/[COLLECTION_KEY]", \
      "name": [COLLECTION_NAME]}}' \
    https://api.gostatit.com/core

### response

{
  "input": {
    "id": "[USERNAME]/[COLLECTION_KEY]"
  }
}
```


#### Parameters

- action: putCollection
- input:
  - id - string - required: ID of the collection
  - name - string - required: Mame of the collection
  - about - string - optional: A descriptive field. Text format
  - frequency - string - optional: A descriptive field. Authorised values: D, W, M, Q, S, Y
  - description  - string - optional: A descriptive field. Text or markdown format.
  - start - string - optional: A descriptive field for the start date of the series (YYYY-MM-DD)
  - end -  string - optional: A descriptive field for the end date of the series (YYYY-MM-DD)
  - language - string - optional: A descriptive field for the language used in the collection. Authorised values: en, fr, de
  - tags - array - optional: Tags related to the collection


#### Response

There are two different responses:

- If your username is incorrect or if the 'id' or 'name' fail validation, you will receive an error.
- If the request is successful, you will receive an input object with the 'id' of the collection


### Put a serie

Now that you have created the collection, you can push series inside.

The required parameters for a serie are: serie ID, name and frequency. The serie ID is built based on the username, the collection key and a specific serie id.

Slashes are authorised inside serie keys.


#### Example:

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "putSerie", "input": { "id": "USERNAME/COLLECTION_KEY/SERIE_KEY", "name": "SERIE_NAME", "frequency": "D" }}' \
    https://api.gostatit.com/core


### response

{
  "input": {
    "id": "USERNAME/COLLECTION_KEY/SERIE_KEY"
  }
}
```


#### Parameters

- action: putSerie
- input:
  - id - string - required: ID of the serie
  - name - string - required: Mame of the serie
  - frequency - string - required: Frequency of the serie. Authorised values: D, W, M, Q, S, Y
  - description - string - optional: Description of the serie. Text format
  - unit - string - optional: Unit of the serie
  - sources - array - optional: List of sources
  - tags - array - optional: List of tags for the serie
  - notes - array - optional: List of notes
  - observations - string - optional: a stringified array of individual observations "[[date1, val1], [date2, val2]]"


#### Response

There are two different responses:

- If the username, the collection key, the serie key or the serie parameters are invalid, you will receive an error.
- If the request is successful, you will receive an input object with the 'id' of the serie


### Add an authorisation

You have created a collection and pushed a serie inside.

Now is the time to create an authorisation to make your serie available to other people.

For simplicity, we will make the serie public.


#### Example:

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "putSerie", "input": { "id": "USERNAME/COLLECTION_KEY/SERIE_KEY", "name": "SERIE_NAME", "frequency": "D" }}' \
    https://api.gostatit.com/core


### response

{
  "input": {
    "id": "USERNAME/COLLECTION_KEY/SERIE_KEY"
  }
}
```


#### Parameters

- action: putSerie
- input:
  - id - string - required: ID of the serie
  - name - string - required: Mame of the serie
  - frequency - string - required: Frequency of the serie. Authorised values: D, W, M, Q, S, Y
  - description - string - optional: Description of the serie. Text format
  - unit - string - optional: Unit of the serie
  - sources - array - optional: List of sources
  - tags - array - optional: List of tags for the serie
  - notes - array - optional: List of notes
  - observations - string - optional: a stringified array of individual observations "[[date1, val1], [date2, val2]]"


#### Response

There are two different responses:

- If the username, the collection key, the serie key or the serie parameters are invalid, you will receive an error.
- If the request is successful, you will receive an input object with the 'id' of the serie
